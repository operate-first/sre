# SLO Bootstrap Guide

Red Hat's SIG-SRE group has created a set of documents which share how some teams engage with the practice of SLOs inside Red Hat. This guide is meant to be a self-contained bootstrapping guide for teams looking to use the site reliability engineering approach to supporting services. It is our hope that these supporting documents can assist others. Before we get started, there are some [definitions](#step-1-familiarise-definitions) to ensure common understanding of terms and phrases that are used throughout the package.

## Steps

### Step 1: Familiarise Definitions

**Service Level Indicator (SLI)** - A Service Level Indicator (SLI) is a specific metric that is used to measure the health/behavior of the system. These **indicators** may be exposed through the service (“white box”) itself or measured in a way that is external to the service (“black box”).

**Service Level Objective (SLO)** - A Service Level Objective is a specific, measurable target to express the level of service provided to a service's customers, be they internal or external. These **objectives** can be focused on a particular aspect of the service, such as a specific API endpoint.  The target for a given SLO is defined against a specific Service Level Indicator.

**Service Level Agreement (SLA)** - A Service Level Agreement is similar to a **SLO**, but is usually a legal document which imposes financial obligations from the service provider to their customers when the agreed service performance target is unmet.

**Persona** - Throughout these documents, the word "persona" is used to describe a kind of person who holds a specific role within a team or organisation. See also [Personas Related to Managed Services][personas-adr].

**Service** - A service is a discrete software that is providing some value to customers (internal or external).

### Step 2: Personas

The first document to familiarise with, aside from this one, is the [Personas Related to Managed Services][personas-adr]. Many of the other documents make reference to the described personas.

### Step 3: SLO Lifecycle

After reviewing the personas, the [SLO Lifecycle][slo-lifecycle-adr] document describes the three phases of living with SLOs: Research, for SLO ideation and gap analysis; Implementation, where changes to a service’s codebase and service team’s processes change to support the SLO; Iteration, for any changes to the SLO or processes after implementation. It is important to know that SLOs are living things and can (and should) be adapted to the team’s lived experiences.

#### Step 3.1: Picking Good SLOs and SLIs

Two documents directly relate to the SLO Lifecycle’s Research phase: [Picking Good SLIs][sli-guide] and [Picking Good SLOs][slo-guide]. A third document supports the Iteration phase as it describes [Error Budget Policy][error-budget-policy].

### Step 4: RACI Chart

The SLO Lifecycle document suggests a number of responsibilities for various personas and the [SLO RACI Chart][raci-chart-adr] aims to be a quick reference for who is responsible for what using a [responsibility assignment matrix pattern][raci-wiki-page].

### Step 5: SLO Reporting

Finally, the [SLO Reporting document][slo-reporting] can be an aid for reporting on the SLO hits and misses to key external stakeholders.

[personas-adr]: https://github.com/operate-first/sre/blob/main/ADRs/RH/SIG-SRE/ADR-00002%20Personas%20related%20to%20Managed%20Services.md
[slo-lifecycle-adr]: https://github.com/operate-first/sre/blob/main/ADRs/RH/SIG-SRE/ADR-00005%20SLO%20Lifecycle.md
[sli-guide]: https://github.com/operate-first/sre/blob/main/picking_good_slis.md
[slo-guide]: https://github.com/operate-first/sre/blob/main/picking_good_slos.md
[error-budget-policy]: https://github.com/operate-first/sre/blob/main/ADRs/RH/SIG-SRE/ADR-00007-Error-Budget-Policy.md
[raci-chart-adr]: https://github.com/operate-first/sre/blob/main/ADRs/RH/SIG-SRE/ADR-00006%20SLO%20RACI%20Chart.md
[raci-wiki-page]: https://en.wikipedia.org/wiki/Responsibility_assignment_matrix
[slo-reporting]: https://docs.google.com/document/d/1W1jf9ov_AZzKU_cyqPMu_pSzsJhRlfiPjtXmN0ZPt-k/edit#
