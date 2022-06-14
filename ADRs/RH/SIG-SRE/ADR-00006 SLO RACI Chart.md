# ADR-00006 SLO RACI Chart

Authors: Lisa Seelye <@lisa>, Jeremy Eder


## Status

Draft


## Problem Statement

With [a large number of personas][personas-adr] involved in a managed services context it can be difficult to keep track of how each persona interacts with or is involved with the many SLO processes.

## Goals

Create a matrix that breaks down the steps involved with the SLO lifecycle and use the [RACI model][wiki-raci] to create a reference matrix for personas.

## Non-goals

Inclusion of every persona and every possible step is not desired. Some personas are not involved with this matrix and it is not feasible to enumerate every possible step.


## Current Architecture

Ad-Hoc.

## Proposed Architecture

We propose to introduce a RACI, or Responsibility Assignment Matrix to define and help visualize roles typically assigned to [various personas][personas-adr] involved with the SLO lifecycle. “RACI” refers to the four different roles, discussed below. These roles are then associated with one or more steps in a table to form the matrix, or chart.

### Proposed Roles

The four roles are Responsible (R), Accountable (A), Consulted (C) and Informed (I).

#### Responsible

The Responsible role applies to those who are expected to do the work.

#### Accountable

The Accountable role applies to those who are answerable for the work being done.

#### Consulted

The Consulted (or Consultant) role applies to those whose opinions are sought. They will likely be subject matter experts, or those whose input is especially important.

#### Informed

The Informed role applies to those who are only notified of the status. Their input is not required or even necessarily sought out; this can be a one-way communication.

### Responsibility Matrix

The following matrix can be used as a starting point and is intended to be copied to other documents with names filled in for those personas. The steps in the matrix correspond to activities taking place in the phases from the [SLO Lifecycle][slo-lifecycle-adr] and areas of responsibility to each persona.

**Note**: Not every [persona][personas-adr] may appear in this chart.

| Step                 | Service Owner | Product Owner(s) | Engineering/Quality Lead | Sw. Eng/QE | SRE IC | Eng Manager/Director | Exec (VP) |
|----------------------|---------------|------------------|--------------------------|------------|--------|----------------------|-----------|
| Existence of SLO     | A/R           | C                | R                        | A          | C      | C                    | I         |
| Propose SLO          | C             | R                | R                        | C          | C      | A                    | I         |
| Agree on SLO         | A             | R                | R                        | C          | I      | I                    | I         |
| Measure+Track SLO    | I             | I                | R                        | I          | A/R    | I                    | I         |
| Propose SLO Roadmap  | C             | C                | A/R                      | C          | C      | I                    | I         |
| Agree SLO Roadmap    | A/R           | R                | C                        | C          | C      | R                    | I         |
| Execute SLO Roadmap  | I             | I                | A                        | R          | R      | C                    | I         |
| Handle Error Budget  | C             | A                | R                        | C          | I      | R                    | I         |
| Recalibrate/Planning | A             | R                | R                        | C          | C      | C                    | I         |

## Challenges

Some organizations may have personas that do not directly map to the ones outlined in the [Personas ADR][personas-adr]. In this case, teams adopting this ADR will need to apply a “best fit” to map their personas to the ones discussed here.


## Alternatives Considered

None.

## Dependencies

None.

## Consequences if Not Completed

None.

[wiki-raci]: https://en.wikipedia.org/wiki/Responsibility_assignment_matrix
[personas-adr]: https://github.com/operate-first/sre/blob/main/ADRs/RH/SIG-SRE/ADR-00002%20Personas%20related%20to%20Managed%20Services.md
[slo-lifecycle-adr]: https://github.com/operate-first/sre/pull/13
