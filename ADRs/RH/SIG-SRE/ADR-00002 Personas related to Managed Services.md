# ADR-00002 Personas related to Managed Services

Authors: Craig Robinson


## Status

Draft


## Problem Statement

A successful SRE practice requires a cross-functional group of stakeholders to engage and work across teams to focus on reliability. This document lists the Personas involved in supporting a cloud service. For example, as a stakeholder of SLOs, I want to be able to consume the data in a relevant and consistent way in accordance with my "persona". The roles and responsibilities of each Persona will be documented in [RACI](https://en.wikipedia.org/wiki/Responsibility_assignment_matrix) format in a future PR.

## Goals

This ADR hopes to resolve the problem statement by identifying and documenting the key personas in a summary format. The output will be a document which will be referenced from other assets.


## Non-goals

* This ADR does not aim at capturing every form or type of persona. It is purposefully generalised, utilising the most frequent persona types as experienced within the Red Hat 'Managed Services' context. The reason is that every organisation calls their personas by different names (and they will inevitably have different role descriptions). Nevertheless, this document hopes to capture the main types in a translatable way.


## Current Architecture

* There was some pre-existing art in an internal Red Hat document entitled the "Application Services Primer". That was used as a source for this ADR.


## Proposed Architecture

The proposed content is as follows:

***

### Personas related to "Managed Services"

Purpose
To underpin many other Site Reliability Engineering-related topics, we must define the group of "personas" describing  the interaction of that person (or group of people) with an environment supported by SREs.

#### Service Owner

Every service needs an "owner". That is, a persona that has the primary interest in the commercial success of that service. The Service Owner takes responsibility for the success of the service and provides the strategic leadership and business context that is needed by engineers, especially during the difficult times. Without this persona, the service would not exist, and thus all other personas rely on this one. They are often referred to as the 'Champions' of this service.

#### Product Owner/Manager

With the strategic guidance of the Service Owner, this persona (also sometimes referred to as the Product Manager) decides on the priority of work (in this context, that may be categorized as 'feature' work or 'reliability work'). They take their inputs from many sources. Reliability, of course, is a significant input, but it is not the only input. There are many other factors which affect their decision-making. Often, they need to balance the inputs from customers and the business, with the engineering resources that are available and these demands can often be conflicting. It is the task of this role to successfully navigate all the demands, providing a path forward.

Additionally, many services are dependent on other services, which have their own Product Owners. Therefore, this persona also plays a critical role in managing those dependencies, liaising with other Product Owners and Engineering resources to effectively prioritize work. Using agile concepts, this role is analogous to a 'Product Owner'.

#### Engineering Managers

Work needs to be done. The majority of this work is undertaken by Developers, who comprise teams led by an Engineering Manager. The primary role of this persona is to enable those teams to do the (best) work they need to do, as it is prioritized by the Product Owner. This role must also maintain working relationships with peer Engineering managers, especially where co-dependencies, shared goals and natural affinities exist.

#### Developers/Software Engineers

This persona implements the service in accordance with the 'plan' (as mostly determined by the Product Owner). They turn this plan into reality, creating and maintaining the code which underpins the service. Not only are they most often responsible for implementing the functionality of the service (in this context "feature work"), but they are also key contributors to helping the software operate reliably ("reliability work"). However, it is also important to acknowledge that it is not only Developers who are concerned with how the service 'operates'. Everyone has a significant part to play. However, in this context, Developers were highlighted to emphasize the concept of identifying operational concerns right up-front at the beginning of any project, and the developers, themselves, taking a special care for how it runs.

Also, it is important to acknowledge that there are developers who are also functioning as SREs, and in fact this is definitely in the spirit of Site Reliability Engineering in general. An example may be a smaller Engineering team who fill many roles, or maybe a newer service that is early in its stages of maturity. However, for the purpose of these personas, consider the person acting in the role of a "Developer" when performing that function, and similarly acting in the role of an SRE when performing that function.

#### Engineering/Architecture Lead

The Developers and SREs do not work in isolation. To obtain the economies of scale that are necessary, and to make sure that work is not duplicated, they need to conform to the 'systems (including processes)' and 'architecture' that best suits the business goal. This is the primary role of this persona. They provide the "guard-rails" for the developers, and help keep the services aligned with accepted strategic technical direction. They also have a key role in developing best practices, and coaching teams to avoid anti-patterns.

#### QE Manager

Much like the Engineering manager, QE managers need to help cross-functional team relationships as well as drive the work related to creating transparency around functional quality and that higher-level business requirements continue to perform as needed.  This persona should also help the engineering teams to drive conversations around defects management in general, customer tickets, usability concerns, along with metrics around the testing effort related to the various environments in play.

#### Quality Engineer

QE is responsible for developing, maintaining, executing, and delivering various tests to ensure service quality. QE is also responsible for providing product and service quality metrics so other personas can check them and act on them as needed. QE covers the service quality through the whole service life-cycle, development, release, and production testing.

#### Site Reliability Engineer (SRE)

The Site or Service Reliability Engineer is an essential part of the service. Their primary focus is ensuring that the services are "running". When there is a problem, it is up to them to resolve the issue as quickly as possible. However, this is only the end goal. The role of an SRE is to contribute to the reliability of the service so that the need to fix something is the exception rather than the rule. This is best epitomized in this quote by one of Red Hat's SRE Managers: "Do not accept repeated failure". That is, if something fails (e.g. SRE is alerted), then follow through with all "actions" so that the problem does not repeat. These actions can be things like: from identifying the issue with the responsible engineering team through to actually fixing the problem in code, personally. 

In many organizations, SRE functions support more than one service. Many projects undertaken by SRE teams provide the tooling, workflows and platforms needed to operate at scale. A key metric is for the SRE team to grow sub-linearly with "hockey stick" customer growth while minimizing toil and technical debt.

SREs are also valuable consultants, particularly in these key areas: observability; automation; resilience; toil prevention; capacity planning; and, operability. They are most familiar with their operational boundaries, they own the core of the incident and problem management processes and are accountable for it and their continuous improvement, and can best articulate the problems being encountered since they are hands-on.

#### Support Engineer

This persona provides assistance to Service Consumers, usually in the form of support cases raised by customers. They may require elevated levels of access to the service internals in order to help consumers, but in a way that ensures they cannot degrade the service itself. 

#### Exec (VP+)

Ultimately reporting to the board, the executive is responsible for implementing the strategies that are designed to meet the goals of the company. Therefore, the executive leadership has an indirect interest in the success of the service, insofar as it is reinforces the company goals. While the Service Owner has a direct interest in the commercial success of the service, they are empowered and enabled by the Executive arm of the organization.

#### Service Consumer (End Users)

These are consumers of the services (and, often, the source of revenue). While this persona often does not know or care what or where the underlying technology is, there are also cases where they do (e.g. regulatory, privacy or internal deployment policies). It is important to note that services can be consumers of other services.

***


## Challenges

* There are an almost infinite number of permutations with respect to these personas, depending upon the circumstances and structure of the organisation. For example, small teams may have developers and SREs doing the same role. However, the purpose of this document is not to cover every nuance or situation otherwise this document would never have an endpoint.


## Alternatives Considered

No alternatives were considered.


## Dependencies

There are no dependencies.


## Stakeholders

* Relevant SIG-SRE members who are dependent on the content in this document.


## Consequences if Not Completed

* This ADR is timely because it is a dependency for other efforts currently underway in the SIG-SRE.
