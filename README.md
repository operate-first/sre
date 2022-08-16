# Operate First - Site Reliability Engineering

## Introduction

This the Operate First repository for Site Reliability Engineering (SRE)
documentation. Here we intend to collect documentation on the nitty-gritty
aspects of building and operating an effective SRE organisation.

## Who runs this repository?

Hello! We're the Red Hat SIG-SRE group, a cross-team group of people inside Red
Hat with an interest in promoting and developing strong SRE culture. As a
result you can expect some of the material here to be a little slanted toward
the way we do things here inside Red Hat, but as we're doing our best to stick
to what are generally accepted to be good SRE practices you should be able to
make use of it with, at most, minor modification.

##  Table of Contents

### Getting Started

* [The Reliability Nightmares Colouring Book](https://github.com/operate-first/sre/raw/main/sre-coloring-book/red-hat-sre-coloring-book.pdf)

    A readable, accessible guide to the various ways in which SRE principles
    and managed services can solve many of the problems associated with running
    complex IT services (and restaurants).

* [The SLO Bootstrap Guide](./slo_bootstrap_guide.md)

    A self-contained bootstrapping guide for teams looking to use the
    SRE approach to supporting services.

* [Incident Management Process Guide](./process/incident_management.md)

    A useful starting point for developing your own incident management
    proceses and procedures.

### Metrics and Monitoring

* [Picking good Service Level Indicators (SLIs)](./picking_good_slis.md)

    Service Level Indicators are one of the most important sets of metrics
    in SRE, and defining them correctly is key to running an effective
    SRE service.

* [Picking good Service Level Objectives (SLOs)](./picking_good_slos.md)

    Where SLIs are used to answer the question "Is everything working as it
    should?", Service Level Objectives (SLOs) define the expectations for
    how much and how often a service should perform correctly according
    to its SLIs. They are probably the single most important set of
    statistics used for evaluating the performance of a managed service,
    as they show maintainers and customers alike just how well things are
    working.

* [Prometheus Alerting Consistency](./prometheus_alerting_consistency.md)

    Alerts are only useful if they're clear and understandable. This guide
    presents some suggested best practices for designing alerts that are
    consistent and useful.

### Decision-Making

* Some sample SIG-SRE [Architecture Decision Records](./ADRs/RH/SIG-SRE)

    When major decisions are made on design or operational aspects of
    system, it can be very worthwhile to keep a clear record of those
    decisions for future reference. An Architecture Decision Record
    (ADR) acts as a document of the discussion and reasoning behind the
    decision it relates to, and in years to come can be extremely valuable
    for answering the eternal question - "Why do we do things this way?".

    This directory contains some sample ADRs from the SIG-SRE group.

### Other Documents

* A work in progess - the [SRE Maturity Model](./sre_maturity.md)

    Moving to an SRE model generally happens in a series of steps rather than
    as a single big change. The SRE Maturity Model is intended to describe
    a set of milestones along the route from "no SRE at all" to "a fully
    functioning SRE organisation".

## Contributing

Feedback is always welcome, and contributions are too!
Feel free to file an
[issue](https://github.com/operate-first/sre/issues/new) or
send us a pull request (PR). If you'd like to know more about what we do or
find out about ways you can get involved, then you can read about
[becoming part of the Operate First community.](https://www.operate-first.cloud/our-community)

If you're submitting Markdown, please check for any linting problems.  The
[vscode-markdownlint](https://github.com/DavidAnson/vscode-markdownlint) plugin
can be used to do this in VSCode.
