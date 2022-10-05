# Picking Good SLIs

## SRE's Philosophy on Monitoring

A core goal of Site Reliability Engineering (SRE) is to ensure the availability of a service. "Availability" here means much more than simply "is my application running." Effectively monitoring a modern cloud application requires insight into the application's response time, error rate, traffic level, and more.

Furthermore, the scope of monitoring should not be limited solely for use in deciding when to page an operations team. Metrics should be closely tied to business objectives, informing decisions on what work to prioritize and when to focus on adding new features versus improving reliability.

To make this vision a reality, service teams rely on two key concepts:

* Service Level Indicators (SLIs) - A quantifiable metric that measures a specific aspect of a service's level of service.
* Service Level Objectives (SLOs) - A measurable, specific goal for a given service's level of service over time, based on one or more SLIs.

In starting on this [journey](sre_maturity.md), we recommend first identifying SLOs for your service. In doing so, consider the perspective of the end user and what aspects of level of service are most important to them. The details that follow offer guidance for selecting the best SLIs to measure adherence to your SLOs.

## Selecting SLIs

In choosing SLIs, we recommend attempting to implement a measure for each of the four "Golden Signals".

### The Four Golden Signals of Monitoring

Google defines the four golden signals well in their [SRE Book](https://sre.google/sre-book/foreword/): "The four golden signals of monitoring are latency, traffic, errors, and saturation. If you can only measure four metrics of your user-facing system, focus on these four."

We recommend implementing at least one SLI for each of these signals.

#### Latency

Latency measures how long it takes your service to handle a request. Examples of how to measure this might be:

* How long does it take for a page of your browser-based application to load
* How long it takes for an API system to respond to an API call
* How long does a database query take
* How long does it take to provision some user-requested environment or resource

Using latency as an SLI can sometimes be a difficult choice, or even the wrong choice. For example, if your service allows users to configure some aspect of it such that the time it takes for a request or transaction is variable, the latency could change dramatically from user to user. If you have an authorisation callback in your API that needs to wait on some 3rd party or customer system before it can perform the requested operation, your service is completely dependent on that external system for the overall latency. Alternatively, if you provide a message broker service,  a user can configure a client to read messages at varying intervals, or even skip reading messages. There is no guarantee of consistency for which you can measure the latency of a full end to end transaction (which the user actually cares about).
Take care to allow for all potential points of latency when abstracting a feature into an SLI, particularly when the service is not a simple http API. You may even consider using an approximation of user interaction as an indicator. For example, a canary application that regularly produces and then consumes a message from a broker. This end-to-end interaction can be captured as metrics and used to approximate what the user experience is like in a controlled environment, leaving users to extrapolate from that if their own experience of the service is within operational parameters.

#### Traffic

Traffic measures how many concurrent workloads are being handled by a service at a point in time. Examples of how to measure this might be:

* How many concurrent users have active sessions in your web app
* How many messages per second are published to a message queue
* How many requests per second is your API handling
* How much network bandwidth is your application serving

If you are running a multi-tenanted service, these indicators can have a dual purpose. They can track the overall traffic of your service, which is useful for overall scaling concerns. They can also be used to track individual tenants of your service and how much traffic is spread or contended between tenants. This would require a simple tenant label on the indicator metric to allow filtering etc. A traffic indicator could show how a small subset of users affect the level of service for all users. (Having guard rails to prevent this happening is a different topic altogether). For example, in a kubernetes environment there may be different instances of a service all running in the same network zone as each other. A lot of network traffic going to 1 user's instance may exhaust the network for other users trying to send traffic to their own instance in the same network zone.

#### Errors

Errors measures the rate of failed requests to your service. Examples of how to measure this might be:

* The number of requests to your API that have a 5xx response code
* The number of errors seen on the client-side by users of your web app
* The rate of dropped packets on a network

When using errors as an SLI, be careful to avoid choosing a metric where user initiated errors can contribute. If possible, find a way to distinguish between the different sources of error and only include non-user initiated errors in the indicator. This maps well to a http service where 5xx response codes generally mean it’s our problem rather than something the user did. 4xx responses might be customer errors, but could also be signs of other issues (confusing API properties, client UX, etc.).  The distinction may be more difficult to tease out of non-HTTP services. Depending on the service protocol, you may need to expose different metrics or labels depending on the source of the error. For example, in a message broker system there may be a general count of errors when consuming a message. A message could fail to be consumed for any number of reasons, caused by a server problem or client misconfiguration.

#### Saturation

Saturation measures the utilization of your service relative to that point at which it would be considered "full". Effectively implementing SLIs for saturation requires knowledge, or at least a hypothesis, of the capacity for your service and the limiting factor. Examples of how to measure this might be:

* CPU utilization percentage for services that are highly CPU-constrained
* Memory utilization percentage for services that are highly Memory constrained
* Storage capacity usage percentage
* Network bandwidth capacity usage percentage
* API request count as a percentage of maximum capacity

Indicators around saturation can be used as a safeguard in a well managed environment where limits are not expected to be reached. However, having unused/wasted resources is not ideal, so you may want to increase capacity on demand. Whether that means a manual increase or an automated scaling of instances, the important piece is having the right indicator of saturation for your service i.e. what is likely to be exhausted first as users use my service.

### Common Pitfalls to Avoid

While not exhaustive, here are a few commonly-made mistakes that we recommend against:

#### Alerting on everything

Many teams attempt to create alerting rules for every metric they collect. This frequently results in “pager fatigue”, or receiving a high number of unactionable alerts or alerts for things that don’t really matter.

Instead, focus on picking the right SLOs, then pick SLIs that help you measure them and alert when you’re in or approaching breach of SLO.

#### Distant Inferences

The distant inference is a measurement made far from the thing that is under consideration. By way of example, using an airport weather forecast for your own home that is 100km away is not as good as measuring at your home.

The risk of the distant inference is that it is not a measurement with high fidelity. They may be chosen because there aren’t means to measure closer to the source (such as with the weather forecast example), or because an error in understanding what the highest fidelity metrics are for a service.

#### Measuring queue size instead of time in queue

In systems that include queues, teams often elect to implement an SLI based on queue size. This metric, however, can be impacted by a number of different factors such as a short term burst of traffic, a brief slowdown in event processing due to a small number of very large requests, or errors while handling events. Instead, we recommend implementing SLIs for time that events have spent in a queue and setting SLOs on that.

This concept can be applied more broadly to selecting good SLIs: take care to identify metrics that directly relate to the user-facing level of service for your application.
