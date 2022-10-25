# SRE Maturity

- [People and Culture](#people-and-culture)
  - [People and Culture - Phase 1: The ‘Crawl’ Phase](#people-and-culture---phase-1-the-crawl-phase)
  - [People and Culture - Phase 2: The 'Walk' Phase](#people-and-culture---phase-2-the-walk-phase)
  - [People and Culture - Phase 3: The 'Run' Phase](#people-and-culture---phase-3-the-run-phase)
- [Observability](#observability)
  - [Observability - Phase 1: The ‘Crawl’ Phase](#observability---phase-1-the-crawl-phase)
  - [Observability - Phase 2: The 'Walk' Phase](#observability---phase-2-the-walk-phase)
  - [Observability - Phase 3: The 'Run' Phase](#observability---phase-3-the-run-phase)
- [On Call, Escalations and Incidents](#on-call-escalations-and-incidents)
  - [On Call, Escalations and Incidents - Phase 1: The ‘Crawl’ Phase](#on-call-escalations-and-incidents---phase-1-the-crawl-phase)
  - [On Call, Escalations and Incidents - Phase 2: The 'Walk' Phase](#on-call-escalations-and-incidents---phase-2-the-walk-phase)
  - [On Call, Escalations and Incidents - Phase 3: The 'Run' Phase](#on-call-escalations-and-incidents---phase-3-the-run-phase)
- [Failures](#failures)
  - [Failures - Phase 1: The ‘Crawl’ Phase](#failures---phase-1-the-crawl-phase)
  - [Failures - Phase 2: The 'Walk' Phase](#failures---phase-2-the-walk-phase)
  - [Failures - Phase 3: The 'Run' Phase](#failures---phase-3-the-run-phase)
- [Security](#security)
  - [Security - Phase 1: The ‘Crawl’ Phase](#security---phase-1-the-crawl-phase)
  - [Security - Phase 2: The 'Walk' Phase](#security---phase-2-the-walk-phase)
  - [Security - Phase 3: The 'Run' Phase](#security---phase-3-the-run-phase)
- [Room to improve](#room-to-improve)
  - [Room to improve - Phase 1: The ‘Crawl’ Phase](#room-to-improve---phase-1-the-crawl-phase)
  - [Room to improve - Phase 2: The 'Walk' Phase](#room-to-improve---phase-2-the-walk-phase)
  - [Room to improve - Phase 3: The 'Run' Phase](#room-to-improve---phase-3-the-run-phase)
- [Releasing](#releasing)
  - [Releasing - Phase 1: The ‘Crawl’ Phase](#releasing---phase-1-the-crawl-phase)
  - [Releasing - Phase 2: The 'Walk' Phase](#releasing---phase-2-the-walk-phase)
  - [Releasing - Phase 3: The 'Run' Phase](#releasing---phase-3-the-run-phase)

## People and Culture

### People and Culture - Phase 1: The ‘Crawl’ Phase

You have a strong SRE voice in your team, someone who advocates for reliability features.
They establish people focused mantras like "It's OK to fail", "Hope is not a strategy" and "Trust by default & extend on it".
Communication is important in your team and you hire diverse people based on soft skills & leadership rather than specific technologies.

You may also have folks from previous "disciplines". For example, sys admins, or experienced developers. Or, even some folks who have experience in "devops". They can bring great skills, experience and value.

You are likely to see resistance to change when making this transition with existing team members, so retraining (or even unlearning) can help. However, there may be inevitable difficult personnel decisions to be made.

At this phase, having buy-in from executive level leadership is essential.
Without this it will be very difficult to get their support later, and eventually their engagement.

The product manager for you service should have a good understanding of SRE.
They should help you advocate for service features that make the service more reliable.

### People and Culture - Phase 2: The 'Walk' Phase

*This is a stub. Please help by adding content. Ref: [SIGSRE-75](https://issues.redhat.com/browse/SIGSRE-75)*

- Starting to get Exec support (improvement on 'buy-in')

### People and Culture - Phase 3: The 'Run' Phase

*This is a stub. Please help by adding content. Ref: [SIGSRE-76](https://issues.redhat.com/browse/SIGSRE-76)*

- Exec engagement

## Observability

### Observability - Phase 1: The ‘Crawl’ Phase

The foundations for monitoring and observing your service are in place.
Being able to measure something meaningful about your service is important, and supplements any feedback you get from initial users.
A common way to do this is via metrics exposed by your service.

In this phase with a well established team that understands common SRE practices, SLOs would start to appear for their service(s) as a way of placing measuring sticks around the effectiveness of scaling efforts. Error budgets wouldn't be tracked, at least not formally.

There might only be one SLO around service availability and it may not even be formally tracked at the start of this phase (as one is first learning to walk). Towards the end of the phase, as the team transitions to "running", they may start to wonder how to enforce this availability SLO and other new ones they want to put into place.

There's a graduation process with SLOs from "informing" to "enforcing". You can use SLOs to inform decisions in this early stage. As they get refined and gain wider awareness & support, you can start thinking about enforcement of an error budget policy.

### Observability - Phase 2: The 'Walk' Phase

*This section needs elaboration. Please help by adding content. Ref: [SIGSRE-77](https://issues.redhat.com/browse/SIGSRE-77)*

You have established patterns and guidelines for observability signals such as metrics, logs, errors etc.
You are using these patterns to speed up debugging of issues and to be to able to correlate various signals more easily, thereby reducing your Mean Time To Recovery (MTTR).
Your alerts have matured and rarely give false positives as a result of having these patterns and refining queries.

- SLOs - SLOs have been iterated on, and you have more than 1 meaningful SLO.
- You understand and track error budgets
- Your alerts are actionable
- Your systems are self healing
  - Avoid SRE having sub-systems that automagically work around the inefficiencies of upstream - needs a good argument why it can’t be fixed upstream - pushing left
- Combination of internal (whitebox) and external (blackbox) monitoring - tied to SLOs
- Dashboards, logging (easily accessible)
- Improving the architecture for lower cost to serve. Prereq here - calculating & knowing the cost to serve

### Observability - Phase 3: The 'Run' Phase

*This section needs elaboration. Please help by adding content. Ref: [SIGSRE-78](https://issues.redhat.com/browse/SIGSRE-78)*

- Observability correlation between logs, metrics, alerts, events etc..
- build on this foundation looking at AI Ops and improving the debug experience (focused on decreasing MTTR further)
  - Needs everything underneath it first (all the signals)
- SLOs - Well established SLO Review process

## On Call, Escalations and Incidents

### On Call, Escalations and Incidents - Phase 1: The ‘Crawl’ Phase

You have a team with an on-call schedule.
It doesn’t have to be 24/7. It doesn’t have to be automated.
But there must be someone responsible for responding when things go bad.
Setting expectations at this early stage with a reduced SLO means you can tailor the schedule to more reasonable times for your team.

Following on from this, you have an escalation process. A way to be notified of problems.
It should be possible to raise a problem with the SRE team and the people that build the service, like engineers, QE, writers.
This can be done via a mailing list, a slack channel, an issue system or by other means.
Formalise it and share it.

If things go really bad, you have an Incident Management Process and do a Root Cause Analysis (RCA) (sometimes called a Post Mortem or Post Incident Review).
You should be starting to build up a library of RCAs that can feed into doing more proactive things as you mature e.g. Incident rehearsals.
Each RCA includes a *blameless* post mortem session with the people involved while the incident is still fresh in their minds.
Each post mortem feeds *extremely valuable* reliability improvements back to the team.
Your management team should ensure high priority of these actions & follow through on them.

### On Call, Escalations and Incidents - Phase 2: The 'Walk' Phase

*This is a stub. Please help by adding content. Ref: [SIGSRE-79](https://issues.redhat.com/browse/SIGSRE-79)*

### On Call, Escalations and Incidents - Phase 3: The 'Run' Phase

*This is a stub. Please help by adding content. Ref: [SIGSRE-80](https://issues.redhat.com/browse/SIGSRE-80)*

## Failures

### Failures - Phase 1: The ‘Crawl’ Phase

*This is a stub. Please help by adding content. Ref: [SIGSRE-81](https://issues.redhat.com/browse/SIGSRE-81)*

You understand how the service reacts to failures and feed the output into planning the environment accordingly while working on improving the areas that are weak

### Failures - Phase 2: The 'Walk' Phase

*This is a stub. Please help by adding content. Ref: [SIGSRE-82](https://issues.redhat.com/browse/SIGSRE-82)*

Validate well established and iterated SLOs under turbulent conditions in addition to making sure right alerts are in place given that observability maturity is part of this phase

- Disaster Recovery & Incident Rehearsals

### Failures - Phase 3: The 'Run' Phase

*This is a stub. Please help by adding content. Ref: [SIGSRE-83](https://issues.redhat.com/browse/SIGSRE-83)*

Chaos testing in production during the available time window while still meeting the SLA

## Security

### Security - Phase 1: The ‘Crawl’ Phase

Security is a set of controls (administrative, technical, physical) that are put in place to manage the risk of a company to an acceptable level.
In this phase, access to the service is limited to those that strictly require it.
Users that have access to the service have the minimum amount of permissions they need to operate the service.
Additionally, access is revoked as soon as possible when a user no longer needs to, for example when the user leaves the group / company.
All access to the system is logged.

A mechanism exists for managing credentials & secrets, and delivering them as configuration into your services.
Engineers are likely doing ad-hoc security activities such as assessments, vulnerability scans, and pen-testing.
These ad-hoc tests inform larger release milestones rather than continuous releases.

### Security - Phase 2: The 'Walk' Phase

In this phase you start to look at compliance.
Compliance relates to all the activities implemented to make sure that security controls meet requirements from compliance certifications/attestations (i.e. ISO 27001:2013, HIPAA, SOC 2 Type 2, PCI DSS, etc.).
Companies may also have your own internal compliance processes or security standards
Those compliance certifications/attestations are the tangible items you can give to your customers to provide assurances of your security posture.

Background checks are implemented for individuals with privileged access to the environment.
The number of background checks needed grows linearly with the individuals with privileged access

Security activities that were previously ad-hoc are now running regularly for each release, scanning your source & your production environment.
Doing 'security impact assessments' at the design phase of service features and architecture decisions pushes you security awareness earlier in the process.
This goes hand in hand with having a Common Vulnerabilities and Exposures (CVE) response process.
All code dependencies are being scanned for vulnerabilities and you are responsive to vulnerability reports and are able to push out fixes to production quickly in accordance with CVE severity.

### Security - Phase 3: The 'Run' Phase

*This is a stub. Please help by adding content. Ref: [SIGSRE-85](https://issues.redhat.com/browse/SIGSRE-85)*

- Automated Policy enforcement

## Room to improve

### Room to improve - Phase 1: The ‘Crawl’ Phase

Your team has sufficient time in their day to pursue improvement.
Your team needs room to practice processes, improve them and automate things.
Without this room, your team will mature more slowly and get bogged down in just keeping the service running day to day.
This can lead to scaling problems, both for the service and the team.
It isn't necessary to formally measure how much time is spent on keeping things running vs. feature development or automation.
That can come later, however you are familiar with the concept of Toil.

### Room to improve - Phase 2: The 'Walk' Phase

*This is a stub. Please help by adding content. Ref:[SIGSRE-86](https://issues.redhat.com/browse/SIGSRE-86)*

- Start measuring Toil more formally & management track it
  - Develop relationship with the upstream (eng and sre, or sre & upstream product) for managing toil

### Room to improve - Phase 3: The 'Run' Phase

*This is a stub. Please help by adding content. Ref:[SIGSRE-87](https://issues.redhat.com/browse/SIGSRE-87)*

## Releasing

*This is a stub. Please help by adding content. Ref: [SIGSRE-88](https://issues.redhat.com/browse/SIGSRE-88)*

### Releasing - Phase 1: The ‘Crawl’ Phase

- One-off Release Scripts

### Releasing - Phase 2: The 'Walk' Phase

- Robust CI/CD Practices

### Releasing - Phase 3: The 'Run' Phase

- Canary Releases
