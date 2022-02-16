# ADR-00001 Document architecture decisions using the Architecture Decision Records approach and define their templates

Authors: Jeremy Eder


## Status

Draft


## Problem Statement

We need to capture our architecture decisions for all of Red Hat’s SIG-SRE and consumers. This capture should make it easy for people to find a given decision and refer to it. The decision context should be captured so we can question that decision when changes arise.


## Goals

* Capture key decisions
* Let the team rely on these decisions
* Capture decision context so we can revisit when context changes
* Be easily discoverable


## Non-goals

* Does not aim at achieving perfection from the get go


## Current Architecture

* None


## Proposed Architecture

* Embrace a well formed template for each Architecture Decision
    * [[Template] Architecture Decision Record](ADR-00000%20Template.md)
* Store each Architecture Decision Record (ADR) in [Operate First’s SRE repository](https://github.com/operate-first/sre/tree/main/ADRs/RH/SIG-SRE).
* Each Architecture Decision Record is named “ADR-nnnnn Some title”
    * nnnnn is a quasi monotonic number assigned at ADR creation time
* ADRs are immutable once their status moves to accepted
* ADRs can supersede preceding ADRs: this is how a decision is changed.
* No ADR once moved past Draft can be ‘deleted’ or ‘removed’.
* Drafts can be developed as pull requests or using gdocs. However once they reach Proposed, they must become PRs against the ADR repository.

### ADR Status Fields

Expected life cycle for each ADR will be as follows:
1. **Draft**: An ADR in Draft indicates its a concept under consideration, being scoped, being written up. No action is expected from anyone other than the author, and there are no time pressures towards moving from the draft state.
2. **Proposed**: ADRs can move to the proposed state once a sponsor has signed up, and the ADR can then start to be socialized within the team / with PMs and with RFCs / RFEs can be scoped in.
3. **Reviewing**: Once moved to Reviewing state, the ADR must be brought to the SIG-SRE weekly call for consideration based on feedback already received. An ADR from this stage can either be moved back to the Proposed state, if gaps are identified or conversations need to be closed, or is Accepted / Rejected. And actions as follow-up should be executed.
4. **Accepted**: Once an ADR is ‘accepted’, it must be moved into read-only mode and no further changes are allowed.
5. **Rejected**: From the reviewing state, it's possible to move ADRs to a rejected state if they do not align with goals, or if stakeholders have fundamental concerns.
6. **Superseded**: ADRs once they move to Accepted state can no longer be changed, since goals and execution is established. Changes would be implemented by replacement ADRs with the previous ADR being moved to ‘superseded’ state, and a comment being added into the ADR metadata itself indicating which ADR now supersedes this specific one. The general pattern to follow is the IETF RFC flow.


## Challenges

* Each existing decisions should be identified and recaptured as Architecture Decision Records (ADR)
* Since ADRs are numbered at creation time, it is possible that an ADR with a higher number is in effect before an ADR with a lower number. Shouldn't be a problem as long as they don’t contradict (nor supersede) one another.


## Alternatives Considered

* Google doc free form documents: are hard to be versioned, searched and made to be immutable


## Dependencies

* [[Template] Architecture Decision Record](ADR-00000%20Template.md)
* Architecture Decision Records directory
* Some materials on the concept of ADR
    * [https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions.html](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions.html) 
    * [https://adr.github.io/](https://adr.github.io/) 
    * [https://adr.github.io/madr/](https://adr.github.io/madr/) 
    * [https://engineering.atspotify.com/2020/04/14/when-should-i-write-an-architecture-decision-record/](https://engineering.atspotify.com/2020/04/14/when-should-i-write-an-architecture-decision-record/) 
    * Note that we are deviating from these descriptions in some areas (including the template)


## Stakeholders

* SIG-SRE and other SRE and engineering teams contributing to these ADRs will consume (and generate) these Architecture Decision Records
* Engineering Management and Product Management personas putting requirements on SRE teams
* SIG-SRE workstream leads are the caretakers of these Architecture Decision Records and are Approvers of all ADR PRs


## Consequences if Not Completed

* Ad-hoc decision recording that might be hard to find
* Non-decisions slowing down the team progress


## Review Status

Proposition is circulated to internal stakeholders.

Status to converge within a week to accept unless concerns are arisen.

