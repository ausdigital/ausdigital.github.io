---
title: "AusDigital Digital Capability Locator (DCL) 1.0 Specification"
specID: "ausdigital-dcl/1"
status: "![raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)"
editors: "[Steven Capell](mailto:steven.capell@gosource.com.au)"
contributors: 
---

## Introduction

This document describes a method for discovering where (which Service Metadata Provider, SMP) a Business publishes information about how to interface their business systems, for the purpose of digital protocols such as electronic invoicing.
The framework assumes that there could be multiple SMP in the network, and so the Digital Capability Locator (DCL) is essentially a Domain Name System (DNS) entry that is used to redirect a lookup query for a given business identifier to the correct SMP.

## Goals

The primary goal of the Digital Capability Locator (DCL) 1.0 Specification is to facilitate integration between Australian businesses, for the purpose of exchanging formal electronic messages (such as digital invoices).

The Digital Capability Locator (DCL) 1.0 Specification defines the interfaces and protocols a central address book, published through the internet Domain Name System, that allows anyone to discover the location of authoratitive metadata describing the integration surface of an Australian business.


## Status

This spec is an early draft for consuiltation.

This specification aims to support the Australian Digital Business Council
[eInvoicing initiative](http://ausdigital.org), and is under active
development at
[https://github.com/ausdigital/ausdigital-dcl](https://github.com/ausdigital/ausdigital-dcl).

Comments and feedback are encouraged and welcome. Pull requests with improvements are welcome too.

## Glossary

Phrase | Definition
------------ | -------------
ausdigital-dcl/1 | This specification.
ausdigital-nry/1 | Version 1 of the AusDigtial [Notary (NRY)](http://ausdigital.org/specs/ausdigital-nry/1.0) specification
ausdigital-dcp/1 | Version 1 of the AusDigtial [Digital Capability Provider (DCP)](http://ausdigital.org/specs/ausdigital-dcp/1.0) specification
ausdigital-idp/1 | Version 1 of the AusDigital [Identity Provider (IDP)](http://ausdigital.org/specs/ausdigital-idp/1.0) specification.
ausdigital-tap/1 | Version 1 of the AusDigital [Transaction Access Point(TAP)](http://ausdigital.org/ausdigital-tap) specification.


# Discovery API

Section 7 of the ADBC DCL Implementation Guide (v1.0 available [here](https://github.com/ausdigital/ausdigital-dcl/blob/master/docs/1.0/Digital_Capability_Locator_Implementation_Guide_v1.0.pdf)) specifies DNS NAPTR records as a DCL query API.

This requires client to create an appropriately formed query, which is then sent through the DNS system where it is matched with a NAPTR record (maintained by the DCL service)


## Hashing Function

The ADBC document specifies an MD5 hash function, which is compatible with the OASIS standard.

```
Feature: MD5 hexdigest function
    As an eInvoicing participant,
    I need to calculate an MD5 hexdigest of a string
    so that I can generate a hashed business identifier

Scenario Outline: Check MD5 calculation correctness
    Given I have string 14247983785
    When I calculate MD5 hexdigest of string
    Then I get hashed value of string 68f746c52284aed8d84db4b20092ead7
```

Unresolved canonical input formatting issues:

 * String encoding is not specified, We have assumed utf-8 but this requires validation.
 * Input case sensitivity String is not specified. We have assumed lower case, but this requires validation.


## URN Encoding

The ADBC document specifies an URN-encoded business identifier, using the NID prefix and ISO 6523 identifier type schemes.

```
Feature: URN encoded Identifiers
    As an eInvoicing participant,
    I need to URN encode business identifiers
    So that I can form a valid DCL query

Scenario Outline: urn encoded ABN 33767197359 (LOWER CASE urn)
    Given I know a business has the identifier 33767197359
    And I know the identifier type is ABN
    When I calculate NID format identifier
    Then I get the URN urn:oasis:names:tc:ecore:partyid-type:iso6523:0151::33767197359
```

Unresolved issues:

 * The document explains how NID URNs can encode various business identifier schemes, but is not explicit about which schemes are required. Do we need to support non-ABN identifiers?


## MD5 Hexdigest of URN encoded business identifier

A well-formed Discovery API query requires an MD5 hexdigest of the URN encoded identifier.

```
Feature: HexDigest of URN encoded business identifier
    As an eInvoicing participant,
    I need to calculate the MD5 hexdigest of a urn encoded business identifier
    So that I can form a valid DCL query

Scenario Outline: hexdigest of urn encoded ABN 14247983785
    Given I know a business has the identifier 14247983785
    And I know the identifier type is ABN
    When I calculate the MD5 hexdigest of the NID format identifier
    Then I get the value bd9aaa006d6a9ee5856da34d3b64cfa7
```


##  Combining the hashed URN into a DCL query string

Given a MD5 hexdigest of the URN encoded business identifier, the DCL query string is formed by prepending 'b-' and postpending the DCL domain name.

```
Feature: Calculate DCL query string
    As an eInvoicing participant,
    I need to calculate a valid DCL query string
    So I can access the DCL query API through DNS


Scenario Outline: Calculate DCL query for ABN 33767197359 at dcl.testpoint.io
    Given I know a business has the identifier 33767197359
    And I know the identifier type is ABN
    And the DCL domain name is dcl.testpoint.io
    When I calculate the DNS query string
    Then I get the address b-94dee132ff9f681ecb17a8d0efc43270.dcl.testpoint.io
```


## Perform NAPTR type DNS query using the DCL query string.

With a well-formed DCL query string, a client application can retrieve the CNAME of the businesses SMP by performing a NAPTR record query using the DNS system.

```
Feature: DCL lookup
    As an eInvoicing participant,
    I need to make DCL queries
    so that I can locate the SMP for identified businesses

Scenario: Check reference values
    Given I know a DCL with expected lookup values 
    When I query the DCL with a lookup fixture
    Then the results match the expected value
```

The NAPTR type query may return multiple records. The usual precedence and order rules are used to identify the applicable record.

# Management API

The DCL Management API allows creation, deletion and update of business records in the DCL.

There are potentially two user-stories for the DCL Management API:

Self Service
```
As an Australian Business
I need the ability to update my DCP specification in the DCL
So that I have control over my own DCP provider 
```

Service Provider
```
As a Service Provider
I need the ability to update my customer's DCP specification in the DCL
So that I can configure the DCL on their behalf
```

The current AusDigital specification is in a raw status (not yet draft). Please contribute to the discussion at the [DCL issue system](https://github.com/ausdigital/ausdigital-dcl/issues/).


## ADBC Proposal

Section 8 of the ADBC DCL Implementation Guide (v1.0, available [here](https://github.com/ausdigital/ausdigital-dcl/blob/master/docs/1.0/Digital_Capability_Locator_Implementation_Guide_v1.0.pdf)) specifies the Management API "used to register a relationship between a Participant
Identifier and a Digital Capability Publisher".

This specifies HTTPS interfaces with client certificate authentication and json or XML payloads. The CREATE and DELETE interfaces are mandatory, and the UPDATE interface is optional. More work is required to resolve how these client certificates might be issued and managed. In it's current form, there appear to be practical limits on supportability of the Self Service user-story.

It also specifies a "List Accredited Publishers" and "List Accredited Access Points" interface. The document suggests the ADBC would be responsible for accreditation. More work is required to resolve this process, and evaluate if these kinds of accreditation process are necessary or even desirable.


## Simplified Web UI

A DCL Management API seems necessary for B2B integration (especially for the Ledger Service Provider user-story).

```
Given I am an Australian Business
And I have credentials with a supported Identity Provider
When I authenticate to the DCL Simplified Web UI
Then I am able to update my DCP entry
```

The current DCL reference implementation:
 * Uses an OIDC Identity Provider as a simulation of a trusted business identity provider that is loosely decoupled from the DCL and enables consent-based authorisation.
 * Assumes Australian Businesses (or providers acting on their behalf) will be able to nominate arbitrary DCPs, rather than assuming a authorised or certified list of DCPs.
 * Assumes Australian Businesses will be able to directly control their own DCL records. It does not have a restrict access to a group of Accredited Access Points

This simplified Web User Interface (Web UI) has been specified to support integration testing, and possibly as a "minimum viable product" for the self-service user-story.  It is not meant to imply that a DCL Management API is unnecessary, and the Simplified Web UI may be become redundant once a satisfactory Management API Specification has been agreed to.

The following Simplified Web UI SPEC is proposed as an interim measure
```
Feature: Simplified DCP update
    As an eInvoicing participant,
    I need to update my DCP entry with the simplified DCL web interface
    So that I can chose my DCP provider

Scenario: Log in and see the update form
    Given I have ABN credentials at the DCL web interface
    When I authenticate
    Then I see "Update DCP"
    Then I click "Update DCP"
    Then I see "Here you can change your DCP to any domain name."
    And I see "New DCP Value"

Scenario: Update DCP value
    Given I have ABN credentials at the DCL web interface
    When I authenticate
    Then I see "Update DCP"
    Then I click "Update DCP"
    Then I see "Here you can change your DCP to any domain name."
    And I see "New DCP Value"
    Then I fill the 'new_dcp_value' field by 'just.another.dcp.testpoint.io' value
    Then I submit the form
    And I see "Value update scheduled"

Scenario: Check the update form
    Given I have ABN credentials at the DCL web interface
    When I authenticate
    And click the "update my DCP" button
    Then I see the DCP update form

Scenario: Check the save button
    Given I have ABN credentials at the DCL web interface
    When I authenticate
    And click the "update my DCP" button
    And I enter new value in the DCP update form
    Then I see "save" button

Scenario: Check the confirm button
    Given I have ABN credentials at the DCL web interface
    When I authenticate
    And click the "update my DCP" button
    And I enter new value in the DCP update form
    And then I click the "save" button
    Then I see the "confirm" button

Scenario: Save changes to the DCP
    Given I have ABN credentials at the DCL web interface
    When I authenticate
    And click the "update my DCP" button
    And I enter new value in the DCP update form
    And then I click the "save" button
    And I click the "confirm" button
    Then I see "DCP updated" message
```

# Normative Examples

## Discovery

TODO: howo to perform a DCL query

## Management

TODO: how to perform a DCL update

# Related Material

 * ADBC DCL Implementation Guide (v1.0, available [here](https://github.com/ausdigital/ausdigital-dcl/blob/master/docs/1.0/Digital_Capability_Locator_Implementation_Guide_v1.0.pdf)), which provides background to the [AusDigital](http://ausdigital.org) community process.
 * [GitHub issues](https://github.com/ausdigital/ausdigital-dcl/issues/) for collaborating on the development of the DCL.
 * A reference [DCL service](https://dcl.testpoint.io/) (for testing and development purposes).
 * Free, Open-Source Software [DCL implementation](https://github.com/test-point/testpoint-dcl).
 * An automated [DCL test suite](https://github.com/test-point/testpoint-dcl).
