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
ausdigital-dcp/1 | This specification (Digital Capability Publisher)
ausdigital-dcl/1 | Version 1 of the AusDigtial [Digital Capability Locator (DCL)](http://ausdigital.org/specs/ausdigital-dcl/1.0) specification
ausdigital-idp/1 | Version 1 of the AusDigital [Identity Provider (IDP)](http://ausdigital.org/specs/ausdigital-idp/1.0) specification.
ausdigital-tap/1 | Version 1 of the AusDigital [Transaction Access Point(TAP)](http://ausdigital.org/ausdigital-tap) specification.
ausdigital-tap/2 | Version 2 of the AusDigital [Transaction Access Point(TAP)](http://ausdigital.org/ausdigital-tap) specification.
ausdigital-nry/1 | Version 1 of the AusDigital [Notary (NRY)](http://ausdigital.org/ausdigital-nry) specification.

DCP - Digital Capability Publisher

business, business id or participant id - string like `urn:oasis:names:tc:ebcore:partyid-type:iso6523:0151::9999999999`

The DCP service depends on `ausdigital-dcl/1` and `ausdigital-idp/1`.

Other ausdigital services `ausdigital-tap`, `ausdigital-tapgw`, `ausdigital-nry` depend on the DCP service.


## Licence

Copyright (c) 2017 the Editor and Contributors. All rights reserved.

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

This framework operates on the basis that the issuer of a business identifier is best positioned to verify the identity of anyone attempting to authorise an update to the metadata registry. That is why for example we are proposing the `ausdigital-dcl/1` for the Australian Business Number (ABN) should be operated by the Australian Business Register (ABR).

The Digital Capability Publisher is functionally equivalent to a REST version of the European OASIS standard "Service Metadata Publisher". Users are expected to have used the `ausdigital-dcl/1` to discover the appropriate DCP service for a particular business. They then interact with the DCP using the REST protocol [documented here](https://app.swaggerhub.com/api/ausdigital/ausdigital-dcp/1.0) to access a collection of ServiceMetadata entries for the business.

The sample below shows a service metadata record example for a business with ABN 99999999999 that supports both standard invoice and RCTI processes. Fields will be explained in this document later.

```
  {
    "ProcessList": [
      {
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
          "TechnicalInformationUrl": "http://developer.myob.com/api/essentials-accounting/endpoints/"
          }
        ]
      },
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
            "TechnicalInformationUrl": "http://developer.myob.com/api/essentials-accounting/endpoints/"
          }
        ]
      }
    ],
    "id": "dbc::claims",
    "ParticipantIdentifier": {
      "scheme": "urn:oasis:names:tc:ebcore:partyid-type:iso6523:0151",
      "value": "99999999999"
    }
  }
```

## Informal description

Free-text explanation of the objects, used in this specification

* business
  * has participant identifier field
    * if you can provide JWT token then you can update this participant info:
      * if JWT contains participant id which is equal to business participant id
      * if JWT has been issued by some IDP which DCP trust
  * has ServiceGroups
    * with field name ("default")
    * with field extensions (free format object)
    * used to logically group the services
  * has service metadata list
    * with relation to ParticipantIdentifier (reference to containing business)
    * with relation to ServiceGroup name ('default' if nothing was specified on service creation step)
    * with field DocumentIdentifier (which document this service is about)
    * with proceses list
      * made of process object
        * with field ProcessIdentifier: which process is described
        * with field ServiceEndpointList: list of endpoints, which accept business messages
  * with public keys list
    * made of PublicKey items
      * with field fingerprint
      * with field keyid
      * with field pubKey
      * with field published
      * with field revoked
  * with list of linked participant identifiers

Business is a base entity, containing all business-related objects. Business info is easy discoverable by DCL-DCP requests chain:

* do NAPTR record to well-known DCL instance (like dcl.testpoint.io) with business participant ID encoded as `B-{md5_of_lowercased_participant_id}.{dcl_hostname}.` (example: `b-06cdeef89c79d08e77d8ea9a6c85e172.dcl.testpoint.io.`)
* get DCP instance hostname (for example. dcp.testpoint.io)
* query DCP instance using given url: `https://{dcp_hostname}/{participant_id}`
* if sender need endpoint to send his message:
  * read and iterate service metadata list of service groups list
  * find desired document workflow information
  * get remote endpoint which accepts the desired document in the given workflow
  * send your document to remote endpoint
* if sender need the public key to encrypt some document for the receiver:
  * iterate current public keys
  * select one which is fine (fresh and not revoked in next 5 minutes)

So, while having recipient participant ID, message body and DCL installation hostname (which is well-known) anyone can effectively send this message to this participant ID without any extra knowledge (specific endpoints, client software, etc) assuming that any protocol is implemented.


## Formal REST API description

DCP MAY deny processing of participant identifier if it starts not with `urn:oasis:names:tc:ebcore:partyid-type:` with 404 error

DCP MUST support json data format

DCP MAY support legacy OASIS xml data format (PEPPOL)

DCP MAY support any other data format

DCP MUST respect `Accept` HTTP header

Any valid DCP implementation (installation) MUST provide next endpoints:

```
GET service group info at least for 'default' group (all service metadatas)
GET service metadata
GET business keys list
GET business key by fingerprint/keyid
GET business linked participant ids ("also known as")
```

DCP internally MAY use any trusted data source (for example, local database, populated by valid users, or linked government data directory)

DCP SHOULD NOT require any auth for GET (readonly) endpoints

But it's not very helpful while businesses can't execute these actions:

```
PUT service metadata
DELETE service metadata
POST business public key
PATCH business public key (update revocation date)
```

so DCP SHOULD allow business managers to update public data

DCP MUST ensure that user have write permission for this business before doing any changes

DCP SHOULD accept JWT token from trusted idp as auth source

DCP MAY use any additional auth mechanism convenient for its users

DCP MAY offer additional endpoints while they don't collide with standard ones

### Endpoints description

**GET `/{participant_id}`**
* MUST contain participant ID
* MUST contain list of document types (service metadatas links)
* MUST NOT contain any data from linked participant identifiers (untill it's submitted directly to this one)
* service group MAY have additional json fields provided, implementations SHOULD ignore unknown fields
* response MUST include `ServiceMetadataReferenceCollection` element with the list of service metadatas for given participant ID

**GET `/{participant_id}/service/{document_id}`**
* Return service metadata for given `document_id` and `participant_id`
* service metadata MAY have additional json fields provided, implementations SHOULD ignore unknown fields
* response MUST include `ProcessList` element

**GET `/{participant_id}/keys/`**
* Return list of published public keys for this participant
* MUST be a list of PublicKey objects (todo: put that schema here, describe fields `fingerprint`, `keyid`, `published`, `pubKey`, `revoked`)
* MAY offer additioinal filtering parameters

**GET `/{participant_id}/keys/{id}`**
* Return specific public key for given business
* `id` parameter MUST be a fingerprint or keyid of given key
* MUST be a valid PublicKey object
* MUST return 404 if key doesn't exists
* MAY offer additioinal filtering parameters

**PUT `/{participant_id}/service/{document_id}`**
* Update and return updated service metadata
* MUST completely replace old service metadata
* MUST support auth and return 4xx error if auth is invalid
* MUST check user permission to make update operation
* response MUST contain updated service metadata in the same format as GET returns

**DELETE `/{participant_id}/service/{document_id}`**
* MUST do something so GET `/{participant_id}/service/{document_id}` starts to return 404

**GET /{participant_id}/aka**
* MUST return full list of participant ids, linked by business owner to this participant identifiers
* links works both ways
* if user linked PID1 to PID2 and PID2 to PID3 then PID1 linked to PID3 as well.

**POST /{participant_id}/aka**
* MUST accept parameter `linked_participant_id` which is equal to participant ID which business owner wants to link
* DCP MUST check auth and ensure that both participant id (base and linked) are owned by user
* MUST silently replace old link by new one if link already exists
* participant_id must appear in GET `/{linked_participant_id}/aka` (link works both ways)

**DELETE `/{participant_id}/aka/{linked_participant_id}`**
* used to remove link from first PID to second
* DCP MUST check auth and ensure that both participant ids (first and second) are owned by this user
* DCP MUST remove the link between first and second participant id


If business has 2 participant identifiers linked then services (documents) from ID1 MUST NOT appear in output for ID2, and vise versa


## Examples

**GET /urn:oasis:names:tc:ebcore:partyid-type:iso6523:0151::42140282984**

```
{
  "ServiceMetadataReferenceCollection": [
    "sap::invoice"
  ],
  "Name": "default",
  "Extension": {},
  "ParticipantIdentifier": {
    "scheme": "urn:oasis:names:tc:ebcore:partyid-type:iso6523:0151",
    "value": "42140282984"
  }
}
```

**GET /urn:oasis:names:tc:ebcore:partyid-type:iso6523:0151::42140282984/service/sap::invoice**

```
{
  "ProcessList": [
    {
      "ProcessIdentifier": {
        "scheme": "dbc",
        "value": "invoice-type1"
      },
      "ServiceEndpointList": [
        {
          "ServiceActivationDate": "2017-02-14",
          "Certificate": "...",
          "EndpointURI": "...",
          "transportProfile": "...",
          "ServiceExpirationDate": "2017-02-14",
          "RequireBusinessLevelSignature": "...",
          "TechnicalInformationUrl": "...",
          "MinimumAuthenticationLevel": "0",
          "ServiceDescription": "..."
        }
      ]
    }
  ],
  "DocumentIdentifier": {
    "scheme": "sap",
    "value": "invoice"
  },
  "ParticipantIdentifier":{
    "scheme": "urn:oasis:names:tc:ebcore:partyid-type:iso6523:0151",
    "value": "42140282984"
  }
}
```

# Related Material

 * ADBC DCP Implementation Guide (v1.0, available [here](https://github.com/ausdigital/ausdigital-dcp/blob/master/docs/1.0/Digital_Capability_Publisher_Implementation_Guide_v1.0.pdf)), which provides background to the [AusDigital](http://ausdigital.org) community process.
 * [GitHub issues](https://github.com/ausdigital/ausdigital-dcp/issues/) for collaborating on the development of the DCP.
 * A reference [DCP service](https://dcp.testpoint.io/) (for testing and development purposes).
 * Free, Open-Source Software [DCP implementation](https://github.com/test-point/testpoint-dcp).
 * An automated [DCP test suite](https://github.com/test-point/testpoint-dcp).
