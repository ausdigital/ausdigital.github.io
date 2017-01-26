---
layout: page
title: Governance Model
permalink: /governance-model/
---
# Governance Model

## Specification Governance
All technical specifications are developed in the public domain using the COSS ([Consensus Oriented Specification System](https://rfc.unprotocols.org/spec:2/COSS/)) governance model. COSS ensures that any interested party can participate (because it imposes no restrictions on contributions). It also maximises consensus because, if the editor does not accept your contribution, you can always fork the specification and become the new editor (if others agree they'll follow, but if nobody else likes your fork then you'll be editor of a lonely specification that will wither on the vine).

All specifications are developed in the public domain. To make your voice heard, you can:

 * To comment on a specification, click on the relevant "Issues List" link against any technical specification and then hit "new issue" when you land in github.  If the discussion around your ticket indicates that it's a good idea likely to be accepted then feel free to make a corresponding pull request referencing your ticket.
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
The secure-by-design nature of the framework eliminates the need for implementation governance or any provider accreditations. Furthermore, the use of independent identity providers such as banks, government, or other entities subject to "know your customer" legislation means that identity assurance is, by definition, governed outside of this specification. Therefore, implementation governance within this framework is reduced to defining a set of assurance levels that are used to classify identity providers - so that particpants in the network can have a clear shared understanding of the identity integrity of any message sent or received. This is the role of the [IDP Specification](https://ausdigital-idp.readthedocs.org/).


## Compliance statement for business software vendors

Business software systems (eg ledgers) are the ultimate sender and receivers of business messages such as invoices. 

As a minimum, business sofware systems;

 * MUST implement a TAP-GW client.
 * MUST implement the IDP relying party client.
 * MUST support one or more semantic specifications - eg the BILL specification for invoicing.
 
Business software systems that choose to develop their own access point and capability register ;

 * MUST implement the TAP service as a receiver of messages.
 * MUST implement the TAP client as a sender of messages.
 * MUST implement the DCP service as a register of capabilites.
 * MUST implement the IDP relying party client.
 * MUST implement the DCL and DCP clients to discover capabilites.
 * MAY implement the NRY client to notarise messages.
 * MUST support one or more semantic specifications - eg the BILL specification for invoicing.
 
## Compliance statement for network service providers

As a network service provider seeking compliance with the framework you;

 * MUST provide a TAP service
 * SHOULD provide a TAP-GW service
 * MUST provide a DCP service (or choose a DCP service provider)
 * MUST implement a DCL client (there is only one DCL provider)
 * MUST implement an IDP client (identity providers are logically seaprate services)
 * MAY provide a NRY service

## Compliance statement for identity providers

As an identity provider seeking compliance with the framework you;

* MUST provide an OIDC IDP service with the scopes and claims defined in the IDP specification, and
* MUST provide evidence to support claims at any identity asurance levwl above zero.
* MUST provide an open framework to adopt relying parties such as business software and network service providers.
