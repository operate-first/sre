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

### Metrics and Monitoring

* [Picking good Service Level Indicators (SLIs)](./picking_good_slis.md)

    Service Level Indicators are one of the most important sets of metrics
    in SRE, and defining them correctly is key to running an effective
    SRE service.

* [Prometheus Alerting Consistency](./prometheus_alerting_consistency.md)

    Alerts are only useful if they're clear and understandable. This guide
    presents some suggested best practices for designing alerts that are
    consistent and useful.

### Decision-Making

* Some sample SIG-SRE [Architecture Decision Records](./ADRs/RH/SIG-SRE)

### Other Documents

* A work in progess - the [SRE Maturity Model](./sre_maturity.md)

    Moving to an SRE model generally happens in a series of steps rather than
    as a single big change. The SRE Maturity Model is intended to describe
    a set of milestones along the route from "no SRE at all" to "a fully
    functioning SRE organisation".

## Contributing

Feedback is always welcome, and contributions are too! Feel free to file an
issue, or simply send us a PR.

If you're submitting Markdown, please check for any linting problems.  The
[vscode-markdownlint](https://github.com/DavidAnson/vscode-markdownlint) plugin
can be used to do this in VSCode.
