---
title: "AusDigital Digital Capability Publisher (DCP) 1.0 Specification"
specID: "ausdigital-dcp/1"
status: "![raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)"
editors: "[Chris Gough](mailto:christopher.d.gough@gmail.com)"
contributors: "[Steven Capell](mailto:steven.capell@gosource.com.au)"
---

## Introduction

This document describes a standard service for discovering the integration surface of a
participant in RESTful business-to-business message exchange.

This specification aims to support the Australian Digital Business Council e-Invoicing
initiative, and is under active development at http://ausdigital.org/.


## Goals

The primary goal of the Digital Capability Publisher (DCP) 1.0 Specification is to TBA.

The Digital Capability Publisher (DCP) 1.0 Specification defines TBA.


## Status

This spec is an early draft for consuiltation.

This specification aims to support the Australian Digital Business Council
[eInvoicing initiative](http://ausdigital.org), and is under active
development at
[https://github.com/ausdigital/ausdigital-dcp](https://github.com/ausdigital/ausdigital-dcp).

Comments and feedback are encouraged and welcome. Pull requests with improvements are welcome too.


## Glossary

Phrase | Definition
------------ | -------------
ausdigital-dcp/1 | This specification.
ausdigital-dcl/1 | Version 1 of the AusDigtial [Digital Capability Locator (DCL)](http://ausdigital.org/specs/ausdigital-dcl/1.0) specification
ausdigital-idp/1 | Version 1 of the AusDigital [Identity Provider (IDP)](http://ausdigital.org/specs/ausdigital-idp/1.0) specification.
ausdigital-tap/1 | Version 1 of the AusDigital [Transaction Access Point(TAP)](http://ausdigital.org/transaction-access-point) specification.
ausdigital-tap/2 | Version 2 of the AusDigital [Transaction Access Point(TAP)](http://ausdigital.org/transaction-access-point) specification.
ausdigital-nry/1 | Version 1 of the AusDigital [Notary (NRY)](http://ausdigital.org/notary/) specification.

The DCP service depends on `ausdigital-dcl/1` and `ausdigital-idp/1`.

Other `ausdigital-tap` and `ausdigital-nry` services both depend on the DCP service.


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


## Application Programming Interface

Implementations MUST provide a compliant REST Application Programming Interface.

A draft [REST interface v1.0](https://swaggerhub.com/api/ausdigital/ausdigital-dcp/1.0) is available for comment.

## Protocol

For open B2B standards to be adopted, users must have confidence in the integrity:

 - confidence in business identity.
 - common business semantics.
 - dynamic service discovery.

This framework operates on the basis that the issuer of a business identifier is best positioned to verify the identity of anyone attempting to authorise an update to the metadata registry. That is why for example we are proposing the ausdigital-dcl/1 for the Australian Business Number (ABN) should be operated by the Australian Business Register (ABR).

The Digital Capability Publisher is functionally equivalent to a REST version of the European OASIS standard "Service Metadata Publisher". Users are expected to have used the ausdigital-dcl/1 to discover the appropriate DCP service for a particular business. They then interact with the DCP using the REST protocol [documented here](https://app.swaggerhub.com/api/ausdigital/ausdigital-dcp/1.0) to access a collection of ServiceMetaData entries for the business. 

The sample below shows a service metadata record example for a business with ABN 23601120601 that supports both standard invoice and RCTI processes.

```
    {"ServiceMetadata":[{
      "ParticipantIdentifier": {"scheme": "abn", "value": "23601120601"},
      "DocumentIdentifier": {"scheme": "dbc-docid", "value": "invoice-1"},
      "ProcessList": [{
        "ProcessIdentifier": {"scheme": "dbc-procid","value": "invoice-1"},
        "ServiceEndpointList": [
          {
          "transportProfile": "REST-POST",
          "EndpointURI": "https://api.myob.com/au/essentials/businesses/23601120601/purchase/invoice-1",
          "RequireBusinessLevelSignature": "true",
          "MinimumAuthenticationLevel": "2",
          "ServiceActivationDate": "2015-05-01",
          "ServiceExpirationDate": "2018-05-01",
          "Certificate": "TlRMTVNTUAABAAAAt7IY4gk....",
          "ServiceDescription": "invoice service",
          "TechnicalInformationUrl": "http://developer.myob.com/api/essentials-accounting/endpoints/"}
          {
        "ProcessIdentifier": {"scheme": "dbc-procid","value": "rcti-1"},
        "ServiceEndpointList": [
          {
          "transportProfile": "REST-POST",
          "EndpointURI": "https://api.myob.com/au/essentials/businesses/23601120601/sales/invoice-1",
          "RequireBusinessLevelSignature": "true",
          "MinimumAuthenticationLevel": "2",
          "ServiceActivationDate": "2015-05-01",
          "ServiceExpirationDate": "2018-05-01",
          "Certificate": "TlRMTVNTUAABAAAAt7IY4gk....",
          "ServiceDescription": "invoice service",
          "TechnicalInformationUrl": "http://developer.myob.com/api/essentials-accounting/endpoints/"}]
        }]
      },
    "Signature": "AD56YGNN8876TTFJ123…"
    },
    {... another signed service metadata structure ...
    }]
    
```

# Related Material

 * ADBC DCP Implementation Guide (v1.0, available [here](https://github.com/ausdigital/ausdigital-dcp/blob/master/docs/1.0/Digital_Capability_Publisher_Implementation_Guide_v1.0.pdf)), which provides background to the [AusDigital](http://ausdigital.org) community process.
 * [GitHub issues](https://github.com/ausdigital/ausdigital-dcp/issues/) for collaborating on the development of the DCP.
 * A reference [DCP service](https://dcp.testpoint.io/) (for testing and development purposes).
 * Free, Open-Source Software [DCP implementation](https://github.com/test-point/testpoint-dcp).
 * An automated [DCP test suite](https://github.com/test-point/testpoint-dcp).
