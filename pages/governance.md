# Governance Model

## Specification Governance
All technical specifications are developed in the public domain using the COSS ([Consensus Oriented Specification System](https://rfc.unprotocols.org/spec:2/COSS/)) governance model. COSS ensures that any interested party can participate (because it imposes no restrictions on contributions). It also maximises consensus because, if the editor does not accept your contribution, you can always fork the specification and become the new editor (if others agree they'll follow, but if nobody else likes your fork then you'll be editor of a lonely specification that will wither on the vine).

## Implementation Governance
The secure-by-design nature of the framework eliminates the need for implementation governance or any provider accreditations. Furthermore, the use of independent identity providers such as banks, government, or other entities subject to "know your customer" legislation means that identity assurance is, by definition, not governed by the ADBC. Therefore, implementation governance within this framework is reduced to;

Defining a set of assurance levels that are used to classify identity providers - so that particpants in the network can have a clear shared understanding of the identity integrity of any message sent or received. This is the role of the [IDP Specification](https://identity-provider.readthedocs.org/).
A key principle that relying parties (eg implementers of the SMP or TAP specifications) will stake their reputation on the strength of identity that they demand for their customers.
How to participate

All specifications are developed in the public domain. To make your voice heard, you can:

 * To comment on a specification, click on the relevant "Issues List" link against any technical specification and then hit "new issue" when you land in github.
 * To participate in a special interest group, click on the relevant "chat room" link in the special interest group table.
 * If you just want to be kept informed, then click on relevant "Mailing list" link in the special interest group table.

A new technical specification can be launched at any time via the following process:
 1. Raise a ticket in the root ausdigital repository with title “Proposed SPEC”. Document a high level scope and purpose of the proposed spec in the issue.
 2. Prove evidence of participation interest by collecting "+1" in the form of comments on the issue from at least 6 other people from at least 3 different organisations.
 3. Nominate an Editor
 4. Indicate acceptance of the COSS governance model and the [SemVer](http://semver.org/) versioning model for specification development.
  5. Once steps 1 to 4 are complete, we will create the repository, give the editor write access, and add the default document template
 6. The new editor should then notify relevant special interest groups of issues or questions regarding the new SPEC

## Compliance statement for technical specifications

As a software application vendor seeking compliance with the framework you;

 * MUST support the TAP specification, and
 * MUST support the client role in the DCL specification, and
 * MUST support the client role in the SMP specification, and
 * MUST support the RP (Relying Party) role in the IDP specification, and
 * MAY support the client role in the NRY specification, and
 * MAY choose to outsource these specification compliance requirements to a compliant third party services provider.

## Compliance statement for semantic specifications

As a software application vendor seeking compliance with the framework you;

 * SHOULD support one or more of the business document semantic specifications, and
 * MAY choose to support one or more processes for the given business document, and
 * MAY choose to support one or more roles (eg buyer or seller) in the relevant process, and
 * MUST publish all supported semantic documents, processes, and roles to an SMP
