# Prometheus Alerting Consistency

## Summary

This guide is originally based on the [Alerting Consistency][1] proposal for OpenShift alerts.

Clear and actionable alerts are a key component of a smooth operational experience. If an alert doesn't have a proven documented procedure to follow when it fires, it can lead to an increase in mean time to repair (MTTR).
Ensuring you have clear and concise guidelines for engineers and SRE creating new alerts will result in a better experience for end users.

## Recommended Reading

A list of references on good alerting practices:

* [Google SRE Book - Monitoring Distributed Systems][2]
* [Prometheus Alerting Documentation][3]
* [Alerting for Distributed Systems][4]

## Style Guide

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

* Alert names MUST be CamelCase, e.g.: `BackendServiceStuck`
* Alert names SHOULD be prefixed with a component, e.g.: `ZookeeperPersistentVolumeFillingUp`, or a Service Level Objective (SLO) name if the alert is a [Multi-Window, Multi-Burn Rate alert](https://sre.google/workbook/alerting-on-slos/#6-multiwindow-multi-burn-rate-alerts)
  * There may be exceptions for some broadly scoped alerts, e.g.: `TargetDown`
* Alerts MUST include a `severity` label indicating the alert's urgency.
  * Valid severities are: `critical` or `warning` — see below for
    guidelines on writing alerts of each severity.
* Alerts MUST include `summary` and `description` annotations.
  * Think of `summary` as the first line of a commit message, or an email
    subject line.  It should be brief but informative.  The `description` is the
    longer, more detailed explanation of the alert.
* Where applicable, alerts SHOULD include a `namespace` label indicating the source of the alert.
  * Many alerts will include this by virtue of the fact that their PromQL
    expressions result in a namespace label.  Others may require a static
    namespace label.
* Alerts SHOULD include a cluster identifier label, especially in cases where alerts are defined or routed centrally for multiple services & clusters.
  * This can hint to an SRE where the affected service is located. It can also be useful for aggregation & filtering when analysing groups of firing alerts.
* All alerts SHOULD include an annotation (e.g. `runbook_url`) which directs the responder(s) to the location of the runbook (sometimes called a Standard Operating Procedure or SOP) that is specific to fixing that problem.

## Critical Alerts

Critical alerts are for alerting current and impending disaster situations.  These alerts page an on-call Engineer.  The situation should warrant waking someone in the middle of the night and/or interrupting their regular workflow.

Reserve critical level alerts only for reporting conditions that may lead to service unavailability.
Failures of individual components should not trigger critical level alerts in general, unless they would result in that condition.
Configure critical level alerts so they fire before the situation becomes irrecoverable.

Example critical alert:

```yaml
- alert: BackendServiceStuck
  expr: max_over_time(backend_state[5m]) != 1
  for: 10m
  labels:
    severity: critical
  annotations:
    summary: 'The backend service is stuck in a non-ready state'
    description: 'The backend service {{ $labels.name }} in the {{ $labels.namespace }} namespace, managed by operator {{ $labels.pod }} has been in a non-ready state for 10 minutes'
    runbook_url: 'https://example.com/backend_service_stuck.asciidoc'
```

This alert fires if a backend service has *not* been ready for the last 10 minutes.
This is a clear example of a critical issue that represents a threat to the operability of the service, and likely warrants paging someone.
The alert has a clear summary and description annotations, and it links to a runbook with information on investigating and resolving the issue.
If there is an SLO related to the alert, mention it in the description so the responder knows why the alert is important.

The group of critical alerts should be small, very well-defined, highly documented, polished and with a high bar set for entry.

## Warning Alerts

The vast majority of alerts should use this severity.
Issues at the warning level should be addressed in a timely manner, but don't pose an immediate threat to the operation of the service as a whole.
If your alert does not meet the criteria in "Critical Alerts" above, it belongs to the warning level.

Use warning level alerts for reporting conditions that may lead to inability to deliver individual features of the service, but not the service as a whole.
Most alerts are likely to be warnings.
Configure warning level alerts so that they do not fire until components have sufficient time to try to recover from the interruption automatically.
You should have a policy for triaging warning alerts and responding in a timely manner e.g. issues created automatically on a backlog that is being actively worked from.

Example warning alert:

```yaml
- alert: PrometheusDuplicateTimestamps
  annotations:
    description: Prometheus {{$labels.namespace}}/{{$labels.pod}} is dropping
      {{ printf "%.4g" $value  }} samples/s with different values but duplicated
      timestamp.
    summary: Prometheus is dropping samples with duplicate timestamps.
    runbook_url: 'https://example.com/prometheus_duplication_timestamps.asciidoc'
  expr: |
    rate(prometheus_target_scrapes_sample_duplicate_timestamp_total{job=~"prometheus-k8s|prometheus-user-workload"}[5m]) > 0
  for: 1h
  labels:
    severity: warning
```

This alert fires if prometheus is dropping samples that have different values but the same timestamp.
Although not ideal, it's also not a current or impending disaster situation and hence shouldn't need to wake someone in the middle of the night.
The 1h timeline allows sufficient time for the service to resolve the problem itself before firing.
If the alert does fire, it can be triaged during normal working hours.
Like with critical alerts, if there is an SLO related to the warning alert, mention it in the description so the responder knows why the alert is important.

[1]: https://github.com/openshift/enhancements/blob/master/enhancements/monitoring/alerting-consistency.md
[2]: https://sre.google/sre-book/monitoring-distributed-systems/
[3]: https://prometheus.io/docs/practices/alerting/
[4]: https://www.usenix.org/sites/default/files/conference/protected-files/srecon16europe_slides_rabenstein.pdf
