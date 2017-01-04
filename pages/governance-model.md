---
layout: page
title: Governance Model
permalink: /governance-model/
---
# Governance Model

## Specification Governance
All technical specifications are developed in the public domain using the COSS ([Consensus Oriented Specification System](https://rfc.unprotocols.org/spec:2/COSS/)) governance model. COSS ensures that any interested party can participate (because it imposes no restrictions on contributions). It also maximises consensus because, if the editor does not accept your contribution, you can always fork the specification and become the new editor (if others agree they'll follow, but if nobody else likes your fork then you'll be editor of a lonely specification that will wither on the vine).

All specifications are developed in the public domain. To make your voice heard, you can:

 * To comment on a specification, click on the relevant "Issues List" link against any technical specification and then hit "new issue" when you land in github.
 * Join the conversation by clicking on the slack channel link link in each specification page.
 * If you just want to be kept informed, then click on the Newsletter sign up link on the left hand menu.

A new specification can be launched at any time via the following process:

 1. Raise a ticket in the root ausdigital repository with title “Proposed SPEC”. Document a high level scope and purpose of the proposed spec in the issue.
 2. Prove evidence of participation interest by collecting "+1" in the form of comments on the issue from at least 6 other people from at least 3 different organisations.
 3. Nominate an Editor
 4. Indicate acceptance of the COSS governance model and the [SemVer](http://semver.org/) versioning model for specification development.
  5. Once steps 1 to 4 are complete, we will create the repository, give the editor write access, and add the default document template
 6. The new editor should then notify relevant special interest groups of issues or questions regarding the new SPEC

## Implementation Governance
The secure-by-design nature of the framework eliminates the need for implementation governance or any provider accreditations. Furthermore, the use of independent identity providers such as banks, government, or other entities subject to "know your customer" legislation means that identity assurance is, by definition, governed outside of this specification. Therefore, implementation governance within this framework is reduced to defining a set of assurance levels that are used to classify identity providers - so that particpants in the network can have a clear shared understanding of the identity integrity of any message sent or received. This is the role of the [IDP Specification](https://identity-provider.readthedocs.org/).

## Compliance statement for technical specifications

As a network service provider seeking compliance with the framework you;

 * MUST provide a TAP service
 * MUST provide the TAP-GW interface
 * MUST implement a DCL client (there is only one DCL provider)
 * MUST provide a DCP service (or choose a DCP service provider)
 * MAY provide a NRY service

As a business software application vendor seeking compliance with the framework you;

 * MUST implement a TAP client (to send messages), and
 * MAY implement a TAP-GW client (if not implementing your own haigh availability TAP service), and
 * MUST implement a DCL client, and
 * MUST implement a DCP client, and
 * MUST support at least one IDP as relying party, and
 * MAY implement an NRY client

## Compliance statement for semantic specifications

As a software application vendor seeking compliance with the framework you;

 * MUST support one or more of the semantic specifications in at least one role (eg buyer or seller), and
 * MUST support the JSON and CODE specifications (because all semantic specifications depend on them), and
 * MUST publish all supported semantic services to a DCP.
