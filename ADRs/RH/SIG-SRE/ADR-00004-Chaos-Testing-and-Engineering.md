# ADR-00004 - Chaos Testing & Engineering

Authors: Naga Ravi Chaitanya Elluri

## Status

Draft

## Problem Statement

There are assumptions that users might have when operating and running their applications in distributed systems environment:

* The network is reliable.
* There is consistent resource usage with no spikes.
* There is zero latency.
* Bandwidth is infinite.
* The network is secure.
* Topology never changes.
* The network is homogeneous.

The assumptions led to a number of outages in production environments in the past.  The services suffered from poor performance or were inaccessible to the customers, leading to the service missing Service Level Agreement uptime promises, revenue loss, and a degradation in the perceived reliability of said services.

To meet the needs and promised Service level agreements ( SLA’s ) for customers and users, it’s important to ensure that both platform as well as the services running on top of it are resilient to failures with minimal degradation in terms of performance for best user experience and avoid any potential downtime.

To achieve this, we need to provide guidance on:
How users can actively adopt Chaos Engineering principles and methodology as part of their test pipelines, depending on their products’ maturity phase in terms of Observability and the  time window that can be used for testing, while still meeting the Service Level Agreement ( SLA ) in production environments as documented as part of SRE maturity.
Evaluating SLO’s under chaotic conditions.

Implications of not addressing the problem:

* Service downtime impacting customers and users
* Not being able to meet SLA’s
* Degraded performance

## Goals

Provide guidance on testing and hardening the services for customers, users and product teams to adopt.

## Non-goals

Test Framework that is part of the Chaos Testing Guide will be actively maintained and can be leveraged but support in terms of assisting with testing one’s services is out of the scope.

## Current Architecture

There isn’t an existing approach. The goal of the document is to add a new feature which doesn’t exist.

## Proposed Architecture

* Deliver and maintain Chaos Testing Guide that can be leveraged by customers and each of the service teams as part of their test pipelines. The guide will encapsulate:
  * Best practices, recommendations that services running in production environments need to take into account for the best user experience.
  * How to leverage the tooling and methodology to evaluate and improve the platform , service resilience and performance impact during chaotic conditions
  * Validate SLO’s and improve the weaknesses under failures

  **NOTE**: Chaos Testing Guide content will be published and maintained as part of the Operate First blog platform.

* Tie chaos testing practices into [various phases of the SRE](https://github.com/operate-first/sre/blob/main/sre_maturity.md) for customers and users to adopt depending on the maturity of their environment and team with an ultimate goal to adopt chaos testing in production environments during the available time window or error budget while still meeting the SLA.

## Challenges

* Engineering cycles to actively maintain and support the Chaos Testing Guide and test framework.

## Alternatives Considered

Alternatives haven’t been considered.

## Dependencies

* For services running on OpenShift and Kubernetes:
  * [Krkn][krkn] aka Kraken, framework to inject failures and evaluate the resilience and performance
  * [Cerberus][cerberus], tool which integrates with Kraken to monitor the health of the OpenShift cluster

## Stakeholders

* Engineering
* SRE
* QE

## Consequences if Not Completed

* Service downtime impacting customers and users
* Not being able to meet SLA’s
* Degraded performance

[krkn]: https://github.com/chaos-kubox/krkn
[cerberus]: https://github.com/chaos-kubox/cerberus
