---
title: "AusDigtial Transaction Access Point Gateway (TAP-GW) 1.0 Specification"
specID: "ausdigital-tap-gw/1"
status: "![raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)"
editors: "[Chris Gough](mailto:christopher.d.gough@gmail.com)"
contributors: "[Steven Capell](mailto:steven.capell@gosource.com.au)"
---

## Introduction

This document describes the access point gateway (TAP-GW), which is an optional extension
to the ausdigital-tap/2. The TAP-GW allows ledger implementers to standardise
interfaces and protocols for communication between trusted/secure ledger systems and
public-facing TAP services.
 
## Glossary:

phrase | Definition
------------ | -------------
ausdigital-tap/2 | Version 2 of the [AusDigtial](http://ausdigital.org) [TAP](http://ausdigital.org/specs/ausdigital-tap/2.0/) specification


## Status

This spec is a requirement for consultation.

If a trusted business system is persistently connected to the internet and natively
supports the TAP protocol, then it has no need for TAPGW interface, either as a client
or server. Gateways are not necessary in the TAP protocol, the TAPGW sub-protocol is
described as an optional extension to the TAP protocol.

There are various reasons why a business system architect may want a structural
separation between their trusted components (e.g. ledger service, ERP system, etc) and
their externally facing components, such as a TAP Gateway. These include performance,
reliability and security objectives, as well as a desire to focus on features that
differentiate their system while outsourcing generic functionality to services with
low-cost utility characteristics. The TAPGW sub-protocol is designed to ensure Gateway
services are generic and interchangeable commodities.

A TAP Gateway service is an availability mediator (allowing trusted business system
components to have intermittent connectivity, and/or to sit behind a firewall). It is
however more than a simple asynchronous proxy (store-and-forward service); additionally,
it performs functions such as message validation, logging, access control, and protocol
callbacks (including to Notary services).

Cryptography is used to prevent TAP Gateways from being able to inspect or manipulate
the content of business messages. A TAP Gateway is not custodian of any business key
material, it is only trusted to reliably send and receive messages. Message signing and
encryption/decryption is performed by systems behind TAPs. The TAP is unable to verify
signatures that have been encrypted, but can verify signatures that are not encrypted.

Notarisation to the blockchain makes it possible for the business system to audit the
reliability of any TAP Gateway that it uses.

This specification aims to support the Australian Digital Business Council
[eInvoicing initiative](https://ausdigital.github.io), as an extension of the
[https://github.com/ausdigital/ausdigital-tap](https://github.com/ausdigital/ausdigital-tap).
It is under active development at
[https://github.com/ausdigital/ausdigital-tap-gw](https://github.com/ausdigital/ausdigital-tap-gw).

## Licence

Copyright (c) 2016 the Editor and Contributors. All rights reserved.

This Specification is free software; you can redistribute it and/or modify it under the
terms of the GNU General Public License as published by the Free Software Foundation; 
either version 3 of the License, or (at your option) any later version.

This Specification is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR
PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program;
if not, see [http://www.gnu.org/licenses](http://www.gnu.org/licenses).


## Change Process

This document is governed by the [2/COSS](http://rfc.unprotocols.org/spec:2/COSS/) (COSS).


## Language

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT",
"RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in
RFC 2119.

# Related Material

 * [GitHub issues](https://github.com/ausdigital/ausdigital-tap-gw/issues/) for collaborating on the development of the TAP-GW.
 * A reference [TAP-GW service](http://testpoint.io/tap-gw) (for testing and development purposes).
 * Free, Open-Source Software [TAP-GW implementation](https://github.com/test-point/testpoint-tap-gw).
 * An automated [TAP-GW test suite](https://github.com/test-point/testpoint-tap-gw).
