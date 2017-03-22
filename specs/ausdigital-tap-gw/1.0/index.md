---
title: "AusDigtial Transaction Access Point Gateway (TAP-GW) 1.0 Specification"
specID: "ausdigital-tap-gw/1"
status: "![raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)"
editors: "[Chris Gough](mailto:christopher.d.gough@gmail.com)"
contributors: "[Steven Capell](mailto:steven.capell@gosource.com.au)"
---

This document describes the access point gateway (TAP-GW), which is an optional
extension to the ADBC access point (TAP). The TAP-GW allows ledger implementers
to use standard interfaces and protocols for communication between
trusted/secure ledger systems and public-facing TAP services.


# Introduction

There are various reasons why a business system architect may want a structural
separation between their trusted components (e.g. ledger service, ERP system,
etc) and their externally facing components, such as a TAP Gateway. These
include performance, reliability and security objectives, as well as a desire to
focus on features that differentiate their system while outsourcing generic
functionality to services with low-cost utility characteristics. The TAPGW
sub-protocol is designed to ensure Gateway services are generic and
interchangeable commodities.

A TAP Gateway service is an availability mediator (allowing trusted business
system components to have intermittent connectivity, and/or to sit behind a
firewall). It is however more than a simple asynchronous proxy
(store-and-forward service); additionally, it performs functions such as message
validation, logging, access control, and protocol callbacks (including to Notary
services).

Cryptography is used to prevent TAP Gateways from being able to inspect or
manipulate the content of business messages. A TAP Gateway is not custodian of
any business key material, it is only trusted to reliably send and receive
messages. Message signing and encryption/decryption is performed by systems
behind TAPs. The TAP is unable to verify signatures that have been encrypted,
but can verify signatures that are not encrypted.

Notarisation to the blockchain makes it possible for the business system to
audit the reliability of any TAP Gateway that it uses.


This specification aims to support the Australian Digital Business Council
[eInvoicing initiative](http://ausdigital.org), as an extension of the
[https://github.com/ausdigital/ausdigital-tap](https://github.com/ausdigital/ausdigital-tap).
It is under active development at
[https://github.com/ausdigital/ausdigital-tap-gw](https://github.com/ausdigital/ausdigital-tap-gw).


## Goals

 * Standard interface for administering an ausdigital-tap service, so that
   TAP services can be interchangeable commodities (prevent vendor lock-in).
 * Clearly delineate the boundary between private trusted systems and commodity
   message processing infrastructure.
 * Manage a potentially large number of TAP endpoints, including bespoke
   metadata that supports custom search features.
 * Provide safe and convenient methods for processing messages.
 * Abstract `ausdigital-ney` away from the message handling protocol, so that
   they support auditing and verification requirements without adding complexity
   to message handling.
 * Abstract `ausdigital-dcl`, `ausdigital-dcp` and `ausdigital-idp` behind safe
   and convenient API methods for publishing endpoints.


## Status

This spec is a requirement for consultation.

This spec is optional: If a trusted business system is persistently connected to
the internet and natively supports the TAP protocol, then it has no need for a
TAP-GW interface, either as a client or server. Gateways are not necessary in
the TAP protocol, the TAPGW sub-protocol is described as an optional extension
to the TAP protocol.


## Glossary

phrase | Definition
------------ | -------------
ausdigital-tapgw/1 | This document
ausdigital-tap/2 | Version 2 of the [AusDigtial](http://ausdigital.org) [TAP](http://ausdigital.org/specs/ausdigital-tap/2.0/) specification
ausdigital-dcl/1 | Version 1 of the [AusDigtial](http://ausdigital.org) [DCL](http://ausdigital.org/specs/ausdigital-dcl/1.0) specification
ausdigital-dcp/1 | Version 1 of the [AusDigtial](http://ausdigital.org) [DCP](http://ausdigital.org/specs/ausdigital-dcp/1.0) specification
ausdigital-nry/1 | Version 1 of the [AusDigtial](http://ausdigital.org) [NRY](http://ausdigital.org/specs/ausdigital-nry/1.0/) specification
ausdigital-idp/1 | Version 1 of the [AusDigtial](http://ausdigital.org) [IDP](http://ausdigital.org/specs/ausdigital-idp/1.0/) specification


## Licence

Copyright (c) 2016 the Editor and Contributors. All rights reserved.

This Specification is free software; you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the Free
Software Foundation; either version 3 of the License, or (at your option) any
later version.

This Specification is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more
details.

You should have received a copy of the GNU General Public License along with
this program; if not, see
[http://www.gnu.org/licenses](http://www.gnu.org/licenses).


## Change Process

This document is governed by the
[2/COSS](http://rfc.unprotocols.org/spec:2/COSS/) (COSS).


## Language

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in RFC 2119.


# Manage Endpoints

The ausdigital-tap specification describes how a multipart/form-data message
is sent to an HTTPS endpoint (TAP_URL) with a POST verb. The TAP-GW sub-protocol
provides methods for creating, configuring and deleting these endpoints.

These endpoints are identified with a URL, comprised of an the TAP-GW provider's
DNS domain followed by an RFC 4122 Universally Unique Identifier (UUID).

For example:
```
https://tap.testpoint.io/886313e1-3b8a-5372-9b90-0c9aee199e5d/
```

This endpoint does not directly reveal any information about the message
receiving party, however the `ausdigital-dcp` reference to the endpoint will (if
metadata about the endpoint has been published).

TODO: as a TAP-GW user:

 * list my endpoints, filter on bespoke metadata (arbitrary key/values
   associated with the endpoints) `GET /endpoints/?{filter}`
 * GET endpoint details `GET /endpoints/{uuid}`
 * PUT new endpoint details `PUT {details} /endpoints/{uuid}`
 * create endpoint `POST {details} /endpoints/`

schema of endpoint details:

 * does not include uuid (that is generated by the TAP-GW)
 * includes endpoint_type (this implies validation rules, allowable value
   currently limited to `ausdigital-tap/2`)
 * includes notary policy (durability, default 1 year)
 * includes arbitrary metadata `{'k1':'v1', 'k2':'v2', ...}`
 * 'status' metadata keyword is forbidden (used internally by the TAP-GW,
   see bellow)


Note:

 * do we use a different domain for tap-gw? I think so
 * basepath like `https://tap-gw.testpoint.io/api/v0/` ?
 * For creating endpoints, authentication to TAP-GW uses JWT from the TAP-GW
   client (the TAP-GW is the RP)?

TAP-GW customers can create an arbitrary number of endpoints, however these
endpoints are "anonymous" until they are mapped to the integration surface of an identified business (via endpoint publishing mechanism)


# Endpoint Publishing

When endpoints are first created they are anonymous (there is not public
information associated with them). Anonymous endpoints can receive messages, but
they are a "dark channel" (not discoverable) until they have metadata published
about them in a DCP (see `ausdigital-dcp`) and DCL (see `ausdigital-dcl`).

There are two ways to publish metadata about an endpoint in a DCP:

 * Directly, via the DCP or DCL interface
 * Indirectly, via TAP-GW convenience methods.

## Directly updated DCP and DCL

Publicly associating an endpoints with a service interface for a business
identity, directly in the DCP requires an appropriate authorisation token from
an IDP (see `ausdigital-idp` for details). Similarly, associating a DCP with a
business identity requires an appropriate authorisation token from an IDP (see
`ausdigital-dcl` for details).

If the TAP-GW interface is used to create an endpoint, and the DCL and DCP are
directly updated to reference this endpoint, no further action is required (the
endpoint is published)

## Updating DCP and DCL via TAP-GW

In addition to directly updating the DCL and DCP, it is also possible to use the
TAP-GW to update the DCL and DCP indirectly, via a convenience interface that
abstracts `ausdigital-dcl` and `ausdigital-dcp` away from the integrated system.

While the TAP-GW interface for updating DCL and DCP is simple, it still requires
an appropriate authorisation token per `ausdigital-idp`. There is more than one
way to accomplish this:

 * The TAP-GW may be a client of an IDP, which is trusted to an appropriate
   level of assurance by the resource (DCP or DCL). If the business identity
   provides authorisation to the TAP-GW, the IDP will issue a token to the
   TAP-GW authorising it to update that business metadata associated with that
   business identity in the resource. This requires the business to authenticate themselves directly to the IDP, and then provide authorisation directly to
   the IDP.
 * The user of the TAP-GW may operate a private (or 3rd party IDP) which is
   trusted by the resource (DCP or DCL) with an appropriate level of assurance,
   including certification for known customer relationship authorisations. If
   the TAP-GW is a Relying Party of this IDP, then the user may use the known
   customer interface of the IDP to issue tokens to the TAP-GW, that the TAP-GW
   can then use to update the resource.
 * The TAP-GW may operate a private IDP on behalf of the user, which is trusted
   by the resource (DCP or DCL) at an appropriate level of assurance. This would
   require the TAP-GW to prove to the satisfaction of the resource that their
   user has 'known customer relationship' with their clients (the TAP-GW's
   customer's customer), and that the TAP-GW is authorised to operate the
   private IDP on behalf of their client. In this situation, the TAP-GW could be
   an OIDC relying party of the private, trusted IDP and use it to issue tokens
   with business identity claims associated with the TAP-GW's customer's
   customer, to the TAP-GW, on behalf of the TAP-GW's customer.


Assuming the TAP-GW has access to appropriate authorisation tokens, the simplest
way to publish metadata about the endpoint in the DCP (or DCL) is to use the
convenience methods in the TAP-GW. This provides a simplified interface for
associating an endpoint with a business identity, service group and purpose.IDP.

TODO: document `PUT /endpoints/{uuid}/business`.
Schema:

 * JWT required
 * business identifier URN?
 * which ServiceGroup?
 * Which endpoint type?
 * requires an appropriate JWT for the business and DCP (update business
   metadata scope)

Notes/Rules:

 * The TAP-GW uses `ausdigital-dcl` to identify which DCP to post the change to.
 * the JWT must come from an `ausdigital-idp` that the DCP is a client of, in
   other words the DCP is the RP (not the TAP_GW)
 * The JWT must contain a claim matching the URN


Question: Do we (or the DCP) prevent  a business from associating the same
endpoint with multiple businesses, multiple service groups, or multiple endpoint
types? - that's a question for the DCP spec.

 * pro: forcing endpoint uniqueness (within a DCP) protects ledger customers
   from lock-in.
 * con: it's not our problem, but we wear the cost of the complexity.
 * I propose we do force endpoint uniqueness, but we should discuss this a bit
   more widely.


When a valid `PUT /endpoints/{uuid}/business` is received by the TAP-GW, the
TAP-GW will use the JWT to interact with the DCP and configure the endpoint
appropriately (for that message type, in the specified service group, for the
identified URN).

That should probably be asynchronous, so PUTting should return a status URL,
which can be used to check the status of the update (in progress, complete,
failed).


# Receive Messages

This is done on a per-endpoint basis.

 * get list of new messages with `GET /endpoints/{uuid}/{filter}`. This returns
   a simple collection of message_id, datetime received, size in bytes.
 * get individual message with `GET /messages/{uuid}`
 * view message status (new/read) with `GET /messages/{uuid}/metadata`
 * mark message as read with `PATCH {'status':'read'} /messages/{uuid}/metadata`
 * mark message as new/unread with
   `PATCH {'status':'new'} /messages/{uuid}/metadata`
 * update message metadata with
   `PATCH {'k1':'v3', 'k2':'v5'}` /messages/{uuid}/metadata`


# Send Messages

There is no need to send messages via the TAP-GW, even if the TAP-GW is being
used to receive messages. However, it is possible

 * `POST {base64 encoded message, TAP_URL} /sender`
 * this will return a UUID, subsequently
 * `GET /sender/{uuid}` will return status of the message (still trying, sent,
   failed)

TODO:

 * add callback for unsuccessful sends
 * is base64 encoding right, or should this be multipart/form-data with new
   parts? is that how we include callback(s)?



# Related Material

 * [GitHub issues](https://github.com/ausdigital/ausdigital-tap-gw/issues/) for collaborating on the development of the TAP-GW.
 * A reference [TAP-GW service](http://testpoint.io/tap-gw) (for testing and development purposes).
 * Free, Open-Source Software [TAP-GW implementation](https://github.com/test-point/testpoint-tap-gw).
 * An automated [TAP-GW test suite](https://github.com/test-point/testpoint-tap-gw).
