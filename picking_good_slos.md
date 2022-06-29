# How to pick a good SLO

A Service Level Objective (SLO) is a measurable, specific goal for a given service's reliability level of service over time, based on one or more SLIs.
To learn more about SLIs, check out our article on how to [pick good SLIs](./picking_good_slis.md).

An SLO is used to quantify customer experience.
Furthermore, SLOs enable us to avoid false positives in alerting and help us focus on symptom-based alerting.
SLOs can vary from organization to organization. Consequently, there is no single formula that we could use to define the appropriate reliability target. 
In this article we will share some tips for picking a good SLO.

So, what should we consider when picking the SLO for a service?

It's important to understand the outcomes of setting an SLO. These outcomes differ depending on multiple factors, including both the maturity of the service and the whole organization overall.
To understand the different SLO settings, let's explore some use-cases that appear at either end of SLO adoption.

## Case 1 - New Service

For this case, imagine a mature SRE organization. In this organization, we have identified stakeholders spanning SLO [personas](./ADRs/RH/SIG-SRE/ADR-00002%20Personas%20related%20to%20Managed%20Services.md).
Each stakeholder understands the outcomes of both meeting or missing an SLO. 

So with that in mind, what should be our service level objective? 

The fact that this case has a new service brings forward the opportunity to use an SLO to steer development efforts before reaching production. 
Ideally, a new service in production is both featureful and reliable. Product managers responsible for the service could use an SLO to define the production readiness by its limited and general availability or other aspects of the service. The availability of a service typically has deadlines, and an SLO can assist in making a clear decision about the risk for a service.

Do we focus our remaining time on making the service more reliable or adding a feature that customer X wanted?

The answer to the above is your decision to make - SLO is the tool used to remove subjectivity about components of the decision. 

## Case 2 - Existing Service 

For this scenario, imagine we created our SLIs for an existing Authentication service in production and defined an SLO. Suddenly, one day, we get paged that our SLO exceeded our target level.
After a quick investigation, we notice that our 3rd party auth provider is down. Consequently, our auth service is in degraded mode. 

Since we have exceeded our SLO because of a third-party service, should we stop releasing new features?

When creating an SLO, external dependencies should be considered, and mitigation strategies should be employed to handle service disruptions from those external dependencies. 
Once your organization is convinced of the benefits that SLOs bring across multiple teams, retrofitting this into a mature service has some cultural considerations. 

First, all stakeholders have to agree on the outcomes of missing an SLO [burning the error budget](./ADRs/RH/SIG-SRE/ADR-00007-Error-Budget-Policy.md). 
This decision may take time for engineering teams to digest the idea of slowing feature work and focusing on reliability issues. 
The goal here should be the balance of direct impact on current processes vs introducing new processes. 

There are two main paths this could be navigated, and each should consider if there is pre-existing data that provides a baseline of current service levels. 
* Set a high SLO to start with and work towards it. What is high? 99.9%? This decision depends on if you can approximate the current service levels being delivered. 
* Set a low SLO to be more tight interally and catch potential issues earlier. However, tight SLOs lead to higher alerting frequency. 

# Tips
* Reflect on customer experience: Customer satisfaction drives the sustainability of the business, so make sure to focus on critical paths that make customers happy.
* Define Expectations vs Reality SLOs: Distinct aspirational SLO target levels from those you can acually achieve.
* Start somewhere: Don't wait until you find the best target levels to create an SLO. 
* Iterate often: You need continuously re-evaluate your reliability targets and update the SLOs based on more realistic target goals.
* Never forget external dependencies: Monitoring external dependencies and considering them while crafting SLOs is important as they have a direct impact on your reliability targets.

To learn more about the SLO lifecycle check our [article](./ADRs/RH/SIG-SRE/ADR-00005%20SLO%20Lifecycle.md) to give you a glimpse of our approach.  