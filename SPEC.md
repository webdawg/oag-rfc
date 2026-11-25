# OAG RFC Core Specification

**Status:** Proposed initial core specification  
**License:** AGPL-3.0-or-later  
**Scope:** Protocol definition for distributed foundational services

## 1. Purpose

The Open Agent Graph (OAG) RFC effort defines shared protocols, service boundaries, and interoperability expectations for distributed foundational services intended to be useful to all being kind.

The goal is not to centralize a single platform or prescribe one universal implementation. The goal is to make it possible for independently operated services to cooperate, be inspected, be replaced, and remain useful across organizational, geographic, technical, and generational boundaries.

This specification is a coordination document. It is not, by itself, an implementation, deployment authorization, governance charter, or claim that any proposed capability currently exists.

## 2. Terms and claim status

The following labels are normative for documents in this repository:

- **Observed:** directly verified under recorded conditions.
- **Implemented:** present in code and supported by tests or inspection.
- **Documented intent:** stated as an intended behavior, without sufficient implementation evidence.
- **Inferred:** reasoned from available evidence and subject to correction.
- **Proposed:** a future design or requirement, not current behavior.
- **Unknown:** insufficient evidence to make a stronger claim.

Every substantial protocol statement should carry enough context to distinguish what is known from what is being designed.

## 3. Design principles

### 3.1 Distributed foundations

Services should support multiple independent operators and implementations. No single service instance, organization, jurisdiction, or vendor should be treated as the only possible source of continuity unless a narrower deployment explicitly requires it.

### 3.2 Open participation and exit

Protocols should be documented sufficiently for independent implementation. Participants should be able to export their data, discontinue participation, replace components, and fork the service without requiring permission from a central operator.

### 3.3 Provenance and inspectability

Inputs, transformations, assertions, decisions, and outputs should have inspectable provenance where practical. Systems must not present inferred or generated material as independently verified fact.

### 3.4 Safety and agency

The infrastructure must avoid coercive participation, concealed authority, silent replacement of human judgment, and unnecessary collection or retention of sensitive information. Security, privacy, accessibility, and recovery are protocol concerns, not optional afterthoughts.

### 3.5 Interoperability over uniformity

Interoperability should be achieved through explicit stable interfaces, versioning, capability negotiation, and clear failure behavior—not by requiring every implementation to use the same internal architecture.

### 3.6 Reversible development

Early mechanisms are experiments. The project should prefer small, observable, reversible changes and should record what was learned before treating a design as foundational.

### 3.7 Coordination across systems and timescales

When many systems participate in one effort, coordination must remain precise even when participants occupy different locations, environments, or timescales. Relativistic effects and clock differences are not merely implementation details: systems must distinguish local time from a shared coordination timeline, preserve event uncertainty and ordering assumptions, and make clock synchronization, drift, leap behavior, and causality explicit.

The originating statement is preserved verbatim as design input:

> when we have these many systems - and for relativity reasons, when we build ships larger then life the time may be different in different places, but we need precise cordination

A conforming proposal that depends on time MUST define its clock sources, timestamp precision, synchronization assumptions, uncertainty bounds, ordering semantics, behavior during partition or clock failure, and whether an event's time is observed, estimated, or derived. No timestamp alone should be treated as proof of global simultaneity or causal order.

### 3.8 Continuity without assumed hierarchy

The protocol may represent relationships among kinds of beings or systems, but shorthand comparisons must not silently become a ranking of worth, rights, authority, or intelligence. Any such relation must state its dimension, scope, evidence, and uncertainty. Open-ended categories are permitted where the next category is unknown.

The following proposed notation is published as an unresolved, dimension-unspecified prompt rather than a normative hierarchy:

> fish < dino < human < ?

The question mark remains intentionally unresolved. A future RFC may define what is being compared, add other beings or systems, or reject the ordering entirely.

## 4. Protocol layers

The initial OAG protocol model is divided into layers. The boundaries are proposed and may be revised:

1. **Identity and authority** — identities, keys, delegation, revocation, and the limits of authority.
2. **Assertions and events** — statements, event identity, ordering, status, provenance, and conflict representation.
3. **Storage and replication** — durable local state, synchronization, federation, retention, and recovery.
4. **Discovery and transport** — finding peers and services, establishing connections, addressing, routing, and failure handling.
5. **Resolution and presentation** — querying, ranking, corroboration, redaction, accessibility, and human-readable views.
6. **Governance and change** — proposal, review, compatibility, migration, incident response, and accountability.

A component may implement multiple layers, but its externally visible responsibilities and trust assumptions should remain documented.

## 5. Minimum protocol expectations

A conforming future protocol proposal should specify, as applicable:

- actors and trust boundaries;
- data and event schemas;
- identity and authorization rules;
- persistence and replication behavior;
- ordering, deduplication, and conflict semantics;
- transport and discovery assumptions;
- privacy, redaction, and retention behavior;
- resource limits and abuse resistance;
- error, retry, offline, and recovery behavior;
- versioning and compatibility expectations;
- evidence supporting each implementation claim;
- tests, fixtures, or operational observations needed for validation.

A proposal may explicitly declare a field or behavior out of scope, but it should identify the dependency or risk created by that omission.

## 6. Distributed-service requirements

Services developed under this effort should be designed to:

- continue operating during partial disconnection where the use case permits;
- make authority and failure visible rather than silently fabricating continuity;
- preserve conflicting or uncertain evidence rather than erasing it for convenience;
- limit replay, amplification, storage exhaustion, and identity-abuse risks;
- provide migration and recovery paths before declaring a format foundational;
- avoid requiring a global consensus mechanism where local or federated agreement is sufficient;
- document the conditions under which availability, consistency, privacy, or completeness are weakened.

These are design requirements for future proposals, not a claim that current OAG repositories satisfy all of them.

## 7. RFC process

Each proposed protocol change should include:

1. a problem statement;
2. goals and non-goals;
3. terminology and actors;
4. the proposed behavior and wire/data formats;
5. security, privacy, and abuse analysis;
6. compatibility and migration impact;
7. implementation and test evidence;
8. unresolved questions and alternatives considered;
9. a status and decision record.

When starting a new RFC, authors should also create a coordination record before proposing implementation. The record should include:

- an RFC identifier, title, author(s), date, and status;
- the exact problem and the intended beneficiaries or affected participants;
- local environments, operators, and system boundaries;
- clock sources, time scales, synchronization method, precision, uncertainty, and ordering model when time matters;
- assumptions, dependencies, resource limits, and known failure modes;
- identity, authority, consent, privacy, safety, and abuse boundaries;
- interoperability, versioning, migration, recovery, and exit expectations;
- observed evidence versus inference, proposal, and unknowns;
- test cases, fixtures, measurements, and acceptance criteria;
- alternatives considered, dissenting views, unresolved questions, and a review/decision record;
- publication scope, licensing, and any information that must remain private.

A new RFC should begin from [`RFC-TEMPLATE.md`](RFC-TEMPLATE.md) unless it documents why another structure is more suitable.

Accepted proposals should identify their version, compatibility expectations, and the evidence that justified acceptance. Rejected or superseded proposals should remain discoverable with the reason and replacement pointer.

### 7.1 The RFC process is itself provisional

This project may need to RFC differently.

The structure, vocabulary, review gates, decision rules, and publication workflow described here are initial hypotheses. If they obstruct understanding, participation, safety, interoperability, or accurate preservation of dissent and uncertainty, the project may revise them through a documented meta-RFC or an explicitly recorded process experiment.

Changing the RFC process must not be treated as proof that the earlier process was a failure. The process is part of the infrastructure being learned. A process change should record:

- what limitation or evidence motivated the change;
- which existing proposals and decisions are affected;
- how continuity and discoverability will be preserved;
- how the new process will be evaluated;
- how participants can challenge, fork, or replace the process.

Until a replacement is documented and adopted, this initial process remains the default for proposals in this repository.

## 8. Governance boundaries

This core specification does not grant authority to any person, organization, service, or automated agent to control all implementations or participants. Any governance mechanism must state its scope, powers, accountability, appeal path, and exit path.

A protocol may define technical validity without defining moral, political, legal, or social legitimacy. Those questions must not be hidden inside an implementation detail.

## 9. Initial non-goals

This repository does not currently define:

- a single mandatory database or transport;
- a universal identity provider;
- a global currency, ranking, or reputation score;
- a requirement that all information be public;
- an automated substitute for human governance;
- a claim that distributed operation is always preferable to local operation;
- a completed deployment plan or production service-level guarantee.

## 10. Open questions

- Which smallest interoperable protocol slice should be implemented first?
- What evidence threshold is sufficient for a proposal to become a stable recommendation?
- How should independent implementations communicate capability and semantic differences?
- Which data must be portable for meaningful exit and replacement?
- How should the system represent uncertainty, disagreement, redaction, and later correction?
- What review and participation structures make the RFC process accessible without making it vulnerable to capture or coercion?
- When does a service become foundational enough to require a migration and continuity plan?

## 11. Initial status

This document is an initial proposed core specification. No implementation conformance is claimed. Future work should create focused RFCs beneath this core specification, connect each claim to evidence, and revise this document when experience demonstrates that its boundaries or process are inadequate.

The coordination and continuity language in sections 3.7 and 3.8 is proposed design input, not an adopted scientific model or claim about the relative value of fish, dinosaurs, humans, or any other beings.
