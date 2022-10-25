# SIG-SRE — the Operate First Site Reliability Engineering Special Interest Group

## Introduction

When starting the Operate First project, we looked around and said, "There is no Open group of SRE practitioners.
Nowhere to discuss and document all the Why, What, and How of our discipline.
We should fix that."

So we are fixing that, and you are invited to participate in creating this [community of practice](https://en.wikipedia.org/wiki/Community_of_practice) around Site Reliability Engineering (SRE).

This is SIG SRE, the Special Interest Group (SIG) for Site Reliability Engineering (SRE) in the Operate First project.

We focus on a core part of the Operate First goal to improve managed services by fully Opening all aspects of the cloud environment.
This new _Open Cloud_ environment is going to need Open SRE practices to go with it, and this is where SIG SRE comes in.

Read the [SIG charter](charter.md) for more details about our purpose and approach.

If you are interested in keeping track of our progress, you can [subscribe to our announcements group](https://lists.operate-first.cloud/archives/list/sig-sre-announce@lists.operate-first.cloud/).

To participate in bootstrapping this community of practice, [join our discussion group](https://lists.operate-first.cloud/archives/list/sig-sre@lists.operate-first.cloud/).

## What kind of SRE practices belong here?

It's easy to say, "All of the good ones," :) and while that is true, we are realistic about where we are today.

As a starting point, we are focusing on practices that relate to a Kubernetes-based environment, and specifically an OpenShift environment.

We believe reliability engineering is agnostic of specific technologies.
We welcome SRE practitioners of all kinds who work with all types of technologies.

BUT there are a few points to understand:

1. Artifacts created in this community are [Open Works](https://fossrit.github.io/open-work-definition/) -- licensed with an Open Source license, etc.
2. We default to Open, including for the kind of software and cloud environments we focus on.

Strictly speaking, we will welcome contributions that guide SRE practices for non-Open Source-based cloud environments.
But where it comes to what is a central focus of this community, it will always be around Open Source-based environments.

##  Table of Contents

### Getting Started

* [The Reliability Nightmares Colouring Book](https://github.com/operate-first/sre/raw/main/sre-coloring-book/red-hat-sre-coloring-book.pdf)

    A readable, accessible guide to the various ways in which SRE principles and managed services can solve many of the problems associated with running complex IT services (and restaurants).

* [The SLO Bootstrap Guide](./slo_bootstrap_guide.md)

    A self-contained bootstrapping guide for teams looking to use the SRE approach to supporting services.

* [Incident Management Process Guide](./process/incident_management.md)

    A useful starting point for developing your own incident management processes and procedures.

### Metrics and Monitoring

* [Picking good Service Level Indicators (SLIs)](./picking_good_slis.md)

    Service Level Indicators are one of the most important sets of metrics in SRE, and defining them correctly is key to running an effective SRE service.

* [Picking good Service Level Objectives (SLOs)](./picking_good_slos.md)

    Where SLIs are used to answer the question "Is everything working as it should?", Service Level Objectives (SLOs) define the expectations for how much and how often a service should perform correctly according to its SLIs.
    They are probably the single most important set of statistics used for evaluating the performance of a managed service, as they show maintainers and customers alike just how well things are working.

* [Prometheus Alerting Consistency](./prometheus_alerting_consistency.md)

    Alerts are only useful if they're clear, understandable and actionable. This guide presents some suggested best practices for designing alerts that are consistent and useful.

### Decision-Making

* Some sample SIG-SRE [Architecture Decision Records](https://github.com/operate-first/sre/tree/main/ADRs/RH/SIG-SRE)

    When major decisions are made on design or operational aspects of system, it can be very worthwhile to keep a clear record of those
    decisions for future reference.
    An Architecture Decision Record (ADR) acts as a document of the discussion and reasoning behind the decision it relates to, and in years to come can be extremely valuable for answering the eternal question - "Why do we do things this way?".
    This directory contains some sample ADRs from the SIG-SRE group.

### Other Documents

* A work in progress - the [SRE Maturity Model](./sre_maturity.md)

    Moving to an SRE model generally happens in a series of steps rather than as a single big change.
    The SRE Maturity Model is intended to describe a set of milestones along the route from "no SRE at all" to "a fully functioning SRE organisation".

## Contributing organizations

### Red Hat
This repository is used by the SRE teams at Red Hat for collecting documentation on the nitty-gritty aspects of building and operating an effective SRE organisation:

Hello! We're a cross-team group of people inside Red Hat with an interest in promoting and developing strong SRE culture.
As a result you can expect some of the material we bring here to be a little slanted toward the way we do things inside Red Hat.
But we're doing our best to stick to what are generally accepted to be good SRE practices, so you should be able to make use of it with — at most — minor modifications.

### Operate First contributing orgs

These organizations have a contributing stake in the Operate First project, which uses this repository as a general practice upstream.
- [MOC Alliance](https://massopen.cloud)
- [Red Hat Collaboratory](https://www.bu.edu/rhcollab/) at Boston University

## Contributing

_For complete information on contributing to this SIG, refer to the canonical [CONTRIBUTING.md](./CONTRIBUTING.md) file._

Feedback is always welcome, and contributions are too!
Feel free to file an [issue](https://github.com/operate-first/sre/issues/new) or send us a pull request (PR). If you'd like to know more about what we do or find out about ways you can get involved, then you can read about [becoming part of the Operate First community.](https://www.operate-first.cloud/our-community)

If you're submitting Markdown, please check for any linting problems.
The [vscode-markdownlint](https://github.com/DavidAnson/vscode-markdownlint) plugin can be used to do this in VSCode.
