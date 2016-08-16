# Purpose of this site

The [Australian Digital Business Council](http://digitalbusinesscouncil.com.au/) has published an interoperability framework that aims to increase national productivity through automation of common buisness processes such as invoicing.  This site makes the framework easy to implement by providing 
* simple and readable technical specifications that are the normative reference for what to build.
* links to reference implementations that you may use to speed up your own implementation.
* links to test cases and test end-points that you can use to be sure that your implementation is functioning correctly.
* links to collaboration forums and mailing lists for special interest groups that seek to contribute to the evolution of the framework.

As an implementer you may choose to just read the information and use the tools presented here - or you may wish to participate more actively by contributing to the specification development or reference implementations.  

# Framework Overview

Unlike single provoder APIs (eg google or facebook), a B2B community needs many different systems to implement the same service interfaces (eg an e-invoicing end-point) so that any business can send any other business an invoice.  The many-to-many aspect of B2B transactions requires a few extra components in the framework as shown in the conceptual overview diagram.

![Framework Diagram](AusDigitalHomepage.png)

For any of the millions of buisnesses in an economy to be able to exchange electronic business documents with any other business:
* Buyers and sellers may have different ledger systems but they must expose access points that conforms to a common interface standard.
* Independent and trusted identity providers need to be able to confirm business identity (to avoid every business having to issue passwords to every other business)
* Electronic service end-point information needs to be discoverable via a registry because a sender system will generally know the identity of a receiver (eg ABN 1234) but not necessarily the technical data about how and where to send and electronic invoice.
* Security measures such as signatures, encryption, and notaries are essential to provide trust and reduce fraud opportunities.

The success of the interoperability framework depends on uptake by the ledger software providers. Those systems must implement a numebr of interfaces in a consistent way - which requires clear standards, good test services, and easy to use tooling.  That is the purpose of this site.

# The Technical Framework Specifications

There is one or more interface specifications for each of the interactions in the overview diagram.  

## Specification Governance model

All technical specifications are developed using the [COSS](http://rfc.unprotocols.org/spec:2/COSS/) (Consensus Oriented Specification System) governance model.  COSS ensures that any interested party can participate (because it imposes no restrictins on contributions). It also maximises consensus because, if the editor does not accept your contribution, you can always fork the specification and become the new editor (if others agree they'll follow, but if nobody else likes your fork then you'll be editor of a lonely specification that will wither on the vine).

A new technical specification can be launched at any time via the following process:

1. [Raise a ticket](https://github.com/ausdigital/ausdigital.github.io/issues) in with title “Proposed SPEC”.  Document a high level scope and purpose of the proposed spec in the issue.
2. Prove evidence of participation interest by collecting "+1" in the form of comments on the issue from at least 6 other people from at least 3 different organisations. 
3. Nominate an Editor
4. Indicate acceptance of the [COSS](http://rfc.unprotocols.org/spec:2/COSS/) governance model and the [http://semver.org/](SemVer) versioning model for specification development.
5. Once steps 1 to 4 are complete, we will create the repository, give the editor write access, and add the default document template
6. The new editor should then notify relevant special interest groups of issues or questions regarding the new SPEC

## Implementation Compliance Statement

As a software application vendor seeking compliance with the framework you;
* MUST support the AP specification, and
* MUST support the client role in the DCL specification, and
* MUST support the client role in the SMP specification, and
* SHOULD support the RP (Relying Party) role in the IDP specification, and
* MAY support the client role in the NRY specification, and
* MAY choose to outsource these specification compliance requirements to a compliant third party

## The Identity Provider (IDP)

A federated set of one or more identity providers are the key source of trust for the network.  This specificaiton defines a standard taxonomy of OIDC claims and scopes, together with a set of identity assurance levels and a standard way to link identity claims.
* [IDP Working Group](https://github.com/ausdigital/identity-provider)
* [IDP Discussion Group](http://talk.testpoint.io/outreach-sig/channels/spec-idp)

| Specification URL | Status | Test Service | Comments |
| ----------------- | ------ | ------------ | -------- |
| Blah | Blah | Blah  | Blah |


## The Digital Capability Locator (DCL)

The framework assumes that there could be multiple SMP in the network and so the digital capability locator is essentially a DNS entry (NAPTR Record type) that is used to redirect a lookup query for a given business identifier to the correct SMP.

* [DCL Working Group](https://github.com/ausdigital/capability-locator)
* [DCL Discussion Group](http://talk.testpoint.io/outreach-sig/channels/spec-dcp)

| Specification URL | Status | Test Service | Comments |
| ----------------- | ------ | ------------ | -------- |
| Blah | Blah | Blah  | Blah |


## The Service Metadata Publisher (SMP)

The framework depends heavily on the ability to discover detailed service information for any given business identifier.  The SMP maintains a list of businesses, with a list of services for each business. Each service lists supported document formats and transport protocols and holds a digital certificate for message signing and encryption.

* [SMP Working Group](https://github.com/ausdigital/metadata-publisher)
* [SMP Discussion Group](http://talk.testpoint.io/outreach-sig/channels/spec-smp)

| Specification URL | Status | Test Service | Comments |
| ----------------- | ------ | ------------ | -------- |
| Blah | Blah | Blah  | Blah |

## The Access Point (AP)

The access point, usually provided by the ledger vendor, is the service gateway for a given business and so hosts the end-point to which business documents are sent.  The gateway is an avaialbility mediator (allowing specific businesses to have intermittent connectivity) and is responsible for signature validation and submitting transactions to the notary service.

* [AP Working Group](https://github.com/ausdigital/access-point])
* [AP Discussion Group](http://talk.testpoint.io/outreach-sig/channels/spec-ap)

| Specification URL | Status | Test Service | Comments |
| ----------------- | ------ | ------------ | -------- |
| Blah | Blah | Blah  | Blah |

## The Notary (NRY)

The notary serivce provides an irrefutable history of a specific "contract" (eg an invoice and it's status lifecycle), recorded in a blockchain distributed ledger.  This service supports dispute resolution and provides the foundation platform for financial services such as debtor financing.

* [NRY Working Group](https://github.com/ausdigital/notary)
* [NRY Discussion Group](http://talk.testpoint.io/outreach-sig/channels/spec-nry)

| Specification URL | Status | Test Service | Comments |
| ----------------- | ------ | ------------ | -------- |
| Blah | Blah | Blah  | Blah |

# The Business Document Semantic Specifications

The technical framework exists only to provide the foundation for the secure and reliable interchange of business documents such as electronic invoices.  The specifications in this section describe the semantics of each business document.  Note that;
* the semantics can vary depending on the process context - for example "commercial invoice" and "reciptient created tax invoice" are two different processes that leverage the same document type.   
* each process has at least two roles (eg Buyer and Seller) with different requirements under the specification.  

Therefore the semantic specifictions group compliance requirements by process and role.

Like the technical specifications, the semantic specification are developed using the [COSS](http://rfc.unprotocols.org/spec:2/COSS/) (Consensus Oriented Specification System) governance model.

## Compliance Statement

As a software application vendor seeking compliance with the framework you;
* SHOULD support one or more of the business document semantic specifications, and
* MAY choose to support one or more processes for the given business document, and
* MAY choose to support one or more roles (eg buyer or seller) in the relevant process, and
* MUST publish all supported semantic documents, processes, and roles to an SMP

## Billing Semantics

The Billing Specifications are based on [OASIS UBL2.1](http://docs.oasis-open.org/ubl/UBL-2.1.html) [billing semantics](http://docs.oasis-open.org/ubl/os-UBL-2.1/UBL-2.1.html#S-BILLING) and include the Invoice, Credit Note, Debit Note, and Application Response documents.  The process roles are buyer and seller.

* [Billing Working Group](https://github.com/ausdigital/billing-semantics)
* [Billing Discussion Group](http://talk.testpoint.io/outreach-sig/channels/spec-billing)

| Specification URL | Status | Test Service | Comments |
| ----------------- | ------ | ------------ | -------- |
| Blah | Blah | Blah  | Blah |

## Purchase Order Semantics

Coming soon - let us know if you'd like to lead this group.

## Shipping Notice Semantics

Coming soon - let us know if you'd like to lead this group

# The Special Interest Groups

Some interest groups cross multiple specifications and may have an impact on many of them but are not, in themselves, the logical owners of a particular specification.  We value the support and opinions of such groups and so we are happy to provide some collaboration tools to facilitate consultation and collaboration with such groups.  If you'd like to participate (or just watch the conversation) of a particular group then please follow the links to subscribe.

## Security Interest Group

Coming soon - let us know if you'd like to moderate this group

## Trade Finance Interest Group

Coming soon - let us know if you'd like to moderate this croup


