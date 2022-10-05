# How to pick a good SLO

A Service Level Objective (SLO) is a measurable, specific goal for a given service's reliability level of service over time, based on one or more SLIs (Service Level Indicator). The SLI is a measure of "what-you-want" (e.g. x should be true) and the SLO is the measure of "how-much-you-want-it" (e.g. y% of the time). Ideally, the SLOs/SLIs are reflecting of some aspect of the service which a customer would consider necessary to the satisfactory usage of that service. For example, as a customer, it is really important for me to be able to get an answer back for my search within 5 seconds (what I want) at least 99% of the time (how much I want it). These are called "customer-centric" SLOs and the reflect a customer's view of the "reliability" they expect for that service. To learn more about SLIs, check out our article on how to [pick good SLIs](./picking_good_slis.md).

An SLO is used to quantify customer experience. Furthermore, SLOs enable [service owners](./ADRs/RH/SIG-SRE/ADR-00002%20Personas%20related%20to%20Managed%20Services.md#service-owner) to avoid false positives in alerting and help focus on symptom-based alerting. SLOs can vary from organization to organization. Consequently, there is no single formula that could define the appropriate reliability target.

The SLO is based on good SLIs, and these should reflect the aspects of the service of most importance to the customer. All the considerations following are nuances of this underlying theme.

It's important to understand the outcomes of setting an SLO. These outcomes differ depending on multiple factors, including both the maturity of the service and the whole organization overall. To understand the different SLO settings, let's explore some use-cases that appear at either end of SLO adoption.

## Case 1 - New Service

For this case, imagine a mature SRE organization. In this organization, there are stakeholders spanning SLO [personas](./ADRs/RH/SIG-SRE/ADR-00002%20Personas%20related%20to%20Managed%20Services.md). Each stakeholder understands the outcomes of both meeting or missing an SLO.

So with that in mind, what should be the service level objective?

A new service presents the opportunity to use an SLO to steer development efforts before reaching production. Ideally, a new service in production is both featureful and reliable. Product managers responsible for the service could use an SLO to define the production readiness. SLOs can assist in removing subjectivity about components of a decision and that helps make clear and quantifiable decisions about the service's readiness.

To learn more about the responsibilities across different personas in an organization, read our [article](./ADRs/RH/SIG-SRE/ADR-00006%20SLO%20RACI%20Chart.md) on the RACI model.

## Case 2 - Existing Service

For this scenario, imagine there's already an SLI for an existing Authentication service in production and defined an SLO. Suddenly, one day, the on-call SRE gets paged that the SLO exceeded the target level. After a quick investigation, the on-call SRE notices that the service's 3rd party auth provider is down. Consequently, the auth service is in degraded mode. Since the SLO target is exceeded because of a third-party service, shall the team stop releasing new features?

When creating an SLO, external dependencies should be considered, and mitigation strategies should be employed to handle service disruptions from those external dependencies. Once the organization is convinced of the benefits that SLOs bring across multiple teams, retrofitting this into a mature service has some cultural considerations.

First, all stakeholders have to agree on the outcomes of missing an SLO [burning the error budget](./ADRs/RH/SIG-SRE/ADR-00007-Error-Budget-Policy.md). This decision may take time for engineering teams to digest the idea of slowing feature work and focusing on reliability issues. The goal here should be the balance of direct impact on current processes vs introducing new processes.

There are two main paths this could be navigated, and each should consider if there is pre-existing data that provides a baseline of current service levels.

* Set a high SLO to start with and work towards it. What is high? 99.9%? This decision depends on if you can approximate the current service levels being delivered.
* Set a [permissive SLO](./ADRs/RH/SIG-SRE/ADR-00005%20SLO%20Lifecycle.md#permissive-slo-phase=) as a lightweight target goal. The service owners engage in the practice of SLOs, but without any "enforcing" aspect to the SLO lifecycle.

## Tips

* Have good SLIs based on what is important to customers.
* Reflect on customer experience: Customer satisfaction drives the sustainability of the business, so make sure to focus on critical paths that make customers happy.
* Define Expectations vs Reality SLOs: Distinct aspirational SLO target levels from those you can acually achieve.
* Start somewhere: Don't wait until you find the best target levels to create an SLO.
* Iterate often: You need continuously re-evaluate reliability targets and update the SLOs based on more realistic target goals.
* Never forget external dependencies: Monitoring external dependencies and considering them while crafting SLOs is important as they have a direct impact on the reliability targets.

To learn more about the SLO lifecycle check our [article](./ADRs/RH/SIG-SRE/ADR-00005%20SLO%20Lifecycle.md) to give you a glimpse of our approach.
