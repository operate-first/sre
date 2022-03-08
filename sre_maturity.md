# SRE Maturity Model

## Phase 1: The ‘Crawl’ Phase

### Crawl Phase Overview

You’re starting from zero, with a net new team.
You may only have a small SRE team, or an SRE function within your development team.
You and your team are technically capable of surviving.
You are probably providing a ‘white glove’ experience to your users at this stage.

### Crawl Phase Characteristics

#### People and Culture

You have a strong SRE voice in your team, someone who advocates for reliability features.
They establish people focused mantras like "It's OK to fail", "Hope is not a strategy" and "Trust by default & extend on it".
Communication is important in your team and you hire diverse people based on soft skills & leadership rather than specific technologies.

At this phase, having buy-in from executive level leadership is essential.
Without this it will be very difficult to get their support later, and eventually their engagement.

The product manager for you service should have a good understanding of SRE.
They should help you advocate for service features that make the service more reliable.

#### Observability

The foundations for monitoring and observing your service are in place.
Being able to measure something meaningful about your service is important, and supplements any feedback you get from initial users.
A common way to do this is via metrics exposed by your service.

You have a simple Service Level Objective (SLO) for you service to start out with.
It doesn't have to be completely representative of what users expect from your service, but it forms the building blocks of an SLO review process and improving on them in time.
Starting with a lower SLO than where you want to get to sets expectations early.

#### “Admin” access to the service

Your team has the level of access required to fix production problems.
If not, you can’t expect them to debug and fix problems in a timely manner.
Being overly controlling of access shouldn’t be a priority at this phase.
That can come later with things like audited access, permissions escalation & tiered access as you mature the debugging experience of your service.
You should trust your team and assume positive intent.

#### On Call, Escalations and Incidents

You have a team with an on call schedule.
It doesn’t have to be 24/7. It doesn’t have to be automated.
But there must be someone responsible to respond when things go bad.
Setting expectations at this early stage with a reduced SLO means you can tailor the schedule to more reasonable times for your team.

Following on from this, you have an escalation process. A way to be notified of problems.
It should be possible to raise a problem with the SRE team and the people that build the service, like engineers, QE, writers.
This can be a mailing list, slack channel, issue system, whatever.
Formalise it and share it.

If things go really bad, you write up an RCA.
You should be starting to build up a library of RCAs that can feed into doing more proactive things as you mature e.g. Incident rehearsals.
Each RCA includes a 'blameless' post mortem session with the people involved while the incident is still fresh in their head.
This post mortem feeds important reliability improvements back to the team.

#### Room to improve

Your team has sufficient time in their day to pursue improvement.
Your team needs room to practice processes, improve them and automate things.
Without this room, your team will mature more slowly and get bogged down in just keeping the service running day to day.
This can lead to scaling problems, both for the service and the team.
It isn't necessary to formally measure how much time is spent on keeping things running vs. feature development or automation.
That can come later, however you are familiar with the concept of Toil.

## Phase 2: The ‘Walk’ Phase (WIP)

### Walk Phase Overview

Your team is well established, has working processes and is familiar with SRE principles.
A lot of those principles are baked into their processes & daily work.
In this phase your team is building on the foundations of observability and starting to reflect on their learnings about the service.
Feedback loops, automation and 'shifting left' with different types of testing are the main theme of this phase.
Your team is capable of scaling the service and number of users in a profitable way.

### Walk Phase Characteristics

* SLOs - SLOs have been iterated on, and you have more than 1 meaningful SLO. You understand and track error budgets
* Observability
  * Actionable Alerts
  * Self healing
    * Avoid SRE having sub-systems that automagically work around the inefficiencies of upstream - needs a good argument why it can’t be fixed upstream - pushing left
  * Combination of internal (whitebox) and external (blackbox) monitoring - tied to SLOs
  * Dashboards, logging (easily accessible)
* Chaos Testing (possible candidate for Phase 1, but what would that look like? Ad-hoc testing?)
* Starting to get Exec support (improvment on 'buy-in')
* Start measuring Toil more formally & management track it
  * Develop relationship with the upstream (eng and sre, or sre & upstream product) for managing toil
* Improving the architecture for lower cost to serve (Is there a prereq here - calculating & knowing the cost to serve)
* DR & Incident Rehearsals (Identifying failure modes could be a prerequisite in phase 1)

## Phase 3: The 'Run' Phase (WIP)

### Run Phase Overview

Your team has found a balance between keeping things running and building reliability into the service.
They have the ability to scale the service without having to increase team size.
There is sufficient confidence in the service that your team looks at 'shifting right' with things like canary releases and production testing.
Automation and observability are mature enough to start looking at concepts like AI Ops.

### Run Phase Characteristics

* Observability correlation beteween logs, metrics, alerts, events etc..
* AI Ops
  * Needs everything underneath it first (all the signals)
* Chaos Engineering
* SLOs - Well established SLO Review process
* Exec engagement
* Testing in Production
* Canary Releases
