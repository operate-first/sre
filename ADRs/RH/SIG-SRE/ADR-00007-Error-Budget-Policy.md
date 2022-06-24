# ADR-00007 Error Budget Policy

Authors: Craig Robinson


## Status

Draft

## Problem Statement

A fundamential tenet of Site Reliability Engineering is to maximise customer satisfaction, not only through the function that a service provides, but also through its stability (aka reliability). This stability is measured through an SLO (Service Level Objective).

This "SLO miss" can be referred to as the "error budget". The error budget can be described as the amount of "error" that a system can withstand without having a negative effect on the service, most notably, the customers "experience" of the service. Mathematically, it is often described as the inverse of the SLO: that is, as an example, there is an SLO target of 99.9% (3 nines) then the error budget is 0.1%. It can also be referred to as a measure of time (e.g. the error budget is 4 minutes per month).

For an SLO to be effective, it needs to have consequences. That is:

"What happens when we consume all our error budget?"

In many organisations, this question is often answered through the existence of a document, backed by a process, that can be called an "Error Budget Policy".


## Goals

The aim of this ADR is to provide a template, with some rationale, for an example Error Budget Policy.


## Non-goals

* This ADR does not aim at providing a definitive policy. The intention would be that consumers of this document would be able to take this example, based on the lessons learned from SRE teams already experienced in the running of services, and mold it to their own experience. It is purposefully generalised.

## Current Architecture

* An analysis of a number of existing Error Budget Policies was conducted, identifying the commonalities and the differences. The best practices articulated in this document was a synthesis of these sources.


## Proposed Architecture

The proposed content is as follows:

***

# Error Budget Policy (draft)

Service Name: \<Service/s Name\>

# Service

\<Briefly describe the service/s under the scope of this document.\>

# Definitions

* _SLI_: The Service Level Indicator is the carefully-considered measure for an aspect of the service that is considered necessary to its function (e.g. the login screen should be available).
* _SLO_: The Service Level Objective is the desired target for the aspect measured by an SLI (e.g. the login screen should be available for 99% of the time).
* _Error Budget_:  The Error budget is one of the fundamental metrics for service reliability. It is the measure of how much a service can be unreliable (e.g. fail) without impacting customers. Error budgets are always based on SLOs.
* _SLO miss_: The state where the error budget has been consumed, and the level of service is not acceptable to the service owner. 
* _Burn rate_: The speed you are consuming your error budget. For example, consuming 100% of the error budget in the expected period (for 30 days period - 30 days), consuming 200% of the error budget in the expected period (for 30 days period - 15 days). This should be used for SLO-based alerting. 
* _Reliability Work_: The work that is needed to recover the service from an "SLO miss" state.
* _Feature Work_: The work that is done to provide the features and functionality that is needed by that service.

# Aim

There are many inputs which affect the prioritization of work. The reliability of a service is a significant, but not the only, input to this process. The Error Budget is the primary metric that is used to inform the decision makers of issues that affect the reliability of a service, and by inference, the satisfaction of the customer with that service.

The questions that this is aiming to help answer is:

* "What do we need to do now that the error budget is all gone?"
* "How do we detect the early signs of system degradation, and what automated mechanisms do we have in place to intercept them?"

# Scope

The scope of this policy is limited to: \<service\>.

The SLOs for this \<service\> are defined \<here\> (link to SLO definitions document).

# Out-of-Scope

The scope of this policy does not apply to: \<service/aspect-of-service\>.

# Current Status

The SLOs for this service are tracked via \<this\> dashboard (link to dashboard or visualization of SLOs).

# Decision Making Principles

## Short-term

* If the service has any remaining error budget for each SLO, releases (feature work) can proceed.
* If the service has consumed more than the allowed error budget for at least one SLO, all releases will stop except for security fixes and the work needed to recover from the "SLO miss" state (reliability work).
    * However, if the error budget was consumed by miscategorised errors (false positives e.g. due to imperfect SLI implementation) and no customers were impacted, releases may continue. A bug for the miscategorisation must be prioritized and fixed as soon as possible.
    * As the error budget is only one of the inputs, an exception process is available to enable the continuation of feature work at the discretion of the service owner (business).

## Long-Term

The following table is adapted from the ["Implementing SLOs"](https://sre.google/workbook/implementing-slos/#decision-making-using-slos-and-error-budgets) chapter in [The Site Reliability Workbook](https://sre.google/workbook/table-of-contents/). The intention is to use it for reviewing and being accountable to SLOs on a regular cadence. The inputs to this table are:

* Performance against SLO (were the current SLOs met or not)?
* The amount of toil required to operate the service (Measured in terms of responding to alerts, manual work & customer reported issues from CEE)?
* The level of customer satisfaction with the service (Measured by customer tickets and any direct customer engagement from the Business)?

<table>
  <tr>
   <td colspan="3" ><strong>INPUTS</strong></td>
   <td colspan="2" ><strong>ACTIONS</strong></td>
  </tr>
  <tr>
   <td><strong>SLO</strong></td>
   <td><strong>Level of Toil/Effort</strong></td>
   <td><strong>Customer Satisfaction </strong></td>
   <td><strong>Considered Action</strong></td>
   <td><strong>"Feature" vs. "Reliability" Balance</strong></td>
  </tr>
  <tr>
   <td>Met</td>
   <td>Low</td>
   <td>High</td>
   <td>No action suggested.</td>
   <td>Focus on "feature work".</td>
  </tr>
  <tr>
   <td>Met</td>
   <td>High</td>
   <td>High</td>
   <td>Focus on reducing toil - especially eliminating false positives.</td>
   <td>Balance the velocity of "reliability work" vs. "feature work" based on all inputs, <em>considering the effect on the SRE team and the risk of error.</em></td>
  </tr>
  <tr>
   <td>Met</td>
   <td>Low</td>
   <td>Low</td>
   <td>If there is no SLO reflecting customer dissatisfaction, create it if appropriate.<p>If an SLO exists, then review based on customer feedback.<p>Fix the Service if needed.</td>
   <td>Stop "feature work" and focus on "reliability work" to resolve the customer satisfaction problem as the priority.</td>
  </tr>
  <tr>
   <td>Met</td>
   <td>High</td>
   <td>Low</td>
   <td>If there is no SLO reflecting customer dissatisfaction, create it if appropriate.<p>If an SLO exists, then review based on customer feedback.<p>Fix the Service if needed.</td>
   <td>Stop "feature work" and focus on "reliability work" to resolve the customer satisfaction problem as the priority.</td>
  </tr>
  <tr>
   <td>Not Met</td>
   <td>Low</td>
   <td>High</td>
   <td>Review the SLO. It is likely a false positive and needs to be adjusted (or even deleted).</td>
   <td>Focus on "feature work". However, fixing the SLO is a priority, as it may hide actual issues.</td>
  </tr>
  <tr>
   <td>Not Met</td>
   <td>High</td>
   <td>High</td>
   <td>Review the SLO. It could be a false positive and needs to be adjusted (or even deleted). If this is causing toil for another team then fix it.</td>
   <td>Balance the velocity of "reliability work" vs. "feature work" based on all inputs, <em>considering the effect on the affected teams and the risk of error.</em></td>
  </tr>
  <tr>
   <td>Not Met</td>
   <td>Low</td>
   <td>Low</td>
   <td>If there is no SLO reflecting customer dissatisfaction, create it if appropriate.<p>If an SLO exists, then review based on customer feedback.<p>Fix the Service if needed.</td>
   <td>Focus on "reliability work" to resolve the customer satisfaction problem.</td>
  </tr>
  <tr>
   <td>Not Met</td>
   <td>High</td>
   <td>Low</td>
   <td>Offload toil and fix product and/or improve automated fault mitigation.</td>
   <td>Stop "feature work" and focus on "reliability work" to resolve the customer satisfaction problem.</td>
  </tr>
</table>

# Review Cadence

It is absolutely necessary to setup a cadence for a regular review of the state of the error budget consumption at any point in time. The following is an example of what would be considered the minimum viable cadence required to keep on top of "burning" error budget. These meetings are an essential part of the "Iteration" phase as described in the [SLO Lifecycle ADR](https://github.com/operate-first/sre/pull/13). The reviews refer to these [personas](https://github.com/operate-first/sre/blob/main/ADRs/RH/SIG-SRE/ADR-00002%20Personas%20related%20to%20Managed%20Services.md).

## Weekly Team Uptime Review

The team/s (SRE/Engineering) responsible for the services need to collaboratively review the availability of the services on a regular basis. As per many typical engineering processes that have been well established, this can, and should, include regular sprint reviews (standups) and retrospectives. However, it has proven very beneficial to have a regular (e.g. weekly) review between, at least, SRE and engineering (but also possibly including the Product Owner). SRE, for example, are typically those who first identify that the error budget has been consumed, or is being consumed. At this meeting, they have the opportunity to inform the engineering team. If the error budget consumption coincides with an incident, this is often in the form of an RCA (Root Cause Analysis) document. The engineering team receive this information, and in close collaboration with the Product Owner, they can prioritise the rectification of the issue/s.

Note: this regular weekly meeting does not replace the need for urgent action required in the case of a significant incident. It is expected that, at these times, ad-hoc review meetings can be called to expedite the resolution.

## Monthly Uptime Review

The weekly review meeting focuses on rapidly identifying issues to mitigate burning error budget as quickly as possible. However, as SLOs are often measured monthly, it is also beneficial to review the SLO performance on a monthly basis. The focus for this review is identifying trends over this longer time period. This is particularly useful in identifying SLOs that may need to be revised (for example, they are set to low or to high, or, they may be false alerts).

# Escalation Process

If, during one of these review meetings, that an "SLO miss" is declared, then it may be an advantage to have a defined process that best enables the resolution of the issue causing the miss. That is, it can be "escalated" through the appropriate channels. The following is an example of an escalation process for this situation.

This event is typically captured during one of the SLO review meetings mentioned previously, but is not constrained to that. An escalation can be triggered at any time, and by any stakeholder. An obvious example of that is when an "incident" is declared, often coinciding with a serious indication of error budget depletion. In these cases, an "incident management process" is often triggered, with its own process and deliverables (e.g. a postmortem).

If any service team exceeds their error budget for a given time period (e.g. monthly), the following steps need to be taken to address the breakage in alignment with stakeholders. For the purposes of this process, these [personas](https://github.com/operate-first/sre/blob/main/ADRs/RH/SIG-SRE/ADR-00002%20Personas%20related%20to%20Managed%20Services.md) are assumed:

1. A "SLO miss" is declared (by anyone, but typically by SRE), and an "owner" is identified.
2. The owner (initially a SRE lead or Manager) meets with the team to declare the start of the rectification process. The root cause should be tracked (even if it is not yet fully determined). At a minimum, it should include:
    * Problem description
    * Impact on the team, end users and stakeholders
    * If there is a manual workaround, then the impact on the SRE team, and a risk assessment.
3. The owner informs the stakeholders. This would typically include:
    * An email to a team or project mailing list.
    * Announcement at a program call.
4. The Product Manager takes into consideration all the inputs and prioritizes the work, balancing "feature work" and "reliability work" as appropriate.
5. The owner role transitions to Engineering (Lead or Manager).
6. The team meets regularly to track the progress and make any adjustments as necessary.
7. The team regularly update about the event status on the program call and in other venues as agreed.
8. Once the issue has been addressed, the coordinator informs the stakeholders that this issue is resolved.

# Exception Process

In a scenario where there is a "SLO miss" that is affecting customers (i.e. valid), and, de-prioritizing committed work is not acceptable to stakeholders, a decision needs to be made between these two opposing options:

1. De-prioritizing the previously committed work ("feature work"), in favor of "reliability" work.
2. Accepting the current impact on the customer/s and lowering the SLO for the service in question (I.e. effectively reducing the SLA).

Decision #2 is a valid response and it is a knob that can be tuned (together with stakeholders) to get the right balance between feature velocity and service reliability. Choosing this path should trigger an "Exception Process", which is handled on a case-by-case basis. This process is essentially about documenting the decision that the stakeholders have chosen, together.

The following is an example of such a process (for the purposes of this process, these [personas](https://github.com/operate-first/sre/blob/main/ADRs/RH/SIG-SRE/ADR-00002%20Personas%20related%20to%20Managed%20Services.md) are assumed):

1. The Product Manager is best placed to assess all the inputs and propose the exception. The persona becomes the owner of this process, and they document the inputs affecting the decision and the cons of not doing #1 and proposing #2. JIRA is a good 
2. The Product Manager organizes a meeting with the key internal stakeholders and presents the document. The decision is ratified.
3. The Product Manager notifies the broader stakeholders. This would typically include:
    * An email to a team or project mailing list.
    * Announcement at a program call.
4. The team meets regularly to track the progress and make any adjustments as necessary.
5. The item is tracked on a program call or similar venue as agreed.
6. Once the issue has been addressed, the Product Manager announces the closure of the exception.

***

## Challenges

* Every organisation has their own structure and processes. This document is not designed to override these, but is offered as a resource to be adapted.

## Alternatives Considered

Google has published a sample [Error Budget Policy](https://sre.google/workbook/error-budget-policy/) which was also considered in the building of this document. There are many common concepts which are shared in both documents.

## Dependencies

There are no dependencies.

## Stakeholders

* Relevant SIG-SRE members who are dependent on the content in this document.
* Consumers of this document, especially those teams currently building services and considering the questions around SLOs and their consequences.

## Consequences if Not Completed

* This ADR is a good example of an Error Budget Policy. If this was not completed, then those teams considering these issues would not have this resource to base their efforts upon. It is a good starting place.
