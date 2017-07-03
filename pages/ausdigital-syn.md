---
layout: page
title: UBL Syntax (SYN) Specification
permalink: /ausdigital-syn/
---

# UBL Syntax (SYN) Specification

This specification describes a syntax and processing model for UBL semantics. 

# SYN-XML Version:

* An XML syntax model for UBL semantics.
* The XSD/Schematron/Genericode validation.

* [SYN-XML GitHub repository](https://github.com/ausdigital/ausdigital-syn-xml/)
* [SYN-XML Slack channel](https://ausdigital.slack.com/messages/spec-syn-xml/) ([you must signup to ausdigital slack first](https://chat.ausdigital.org/))

# SYN-JSON Version:

* A simple JSON syntax model for UBL semantics.
* A lossless transformation model between UBL XML (UBL XML Syntax 1.0 spec) and JSON (UBL JSON Syntax 1.0 spec) representations.
* A simple JSON processing model based on a RESTful Validation API.

The intent of UBL JSON Syntax 1.0 spec is to provide developers with a much simpler implementation model than the XSD/Schematron/Genericode alternative whilst maintaining interoperability with the UBL XML standard.

* [SYN-JSON 1.0 GitHub repository](https://github.com/ausdigital/ausdigital-syn-json)
* [SYN-JSON 1.0 Slack channel](https://ausdigital.slack.com/messages/spec-syn-json/)

# SYN-SOL Version

* A Solidity Syntax stadard used in Ethereum Blockchain smart contracts representing UBL semantics. 
* Supported by an Oracle implementation that provides interchange with parties outside of the Ethereum network.

* [SYN-SOL 1.0 GitHub repository](https://github.com/ausdigital/ausdigital-syn-sol)
* [SYN-JSON 1.0 Slack channel](https://ausdigital.slack.com/messages/spec-sol)

| Specification URL | Version | Status | API Definition | Issues List |
| ----------------- | ------  | ------ | -------------- | ----------- |
| [SYN-XML 1.0 spec](http://ausdigital.org/specs/ausdigital-syn-xml/1.0/) | 1.0 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg) | N/A | [SYN-XML 1.0 Issues](https://github.com/ausdigital/ausdigital-syn-xml/issues)  |
| [SYN-JSON 1.0 spec](http://ausdigital.org/specs/ausdigital-syn-json/1.0/) | 1.0 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg) | [SYN-JSON 1.0 API](http://swagger.testpoint.io?url=http://ausdigital.org/specs/ausdigital-syn-json/1.0/swagger.json){:target="_blank"}   | [SYN-JSON 1.0 Issues](https://github.com/ausdigital/ausdigital-syn-json/issues)  |
| [SYN-SOL 1.0 spec](http://ausdigital.org/specs/ausdigital-syn-sol/1.0/) | 1.0 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg) | [SYN-SOL 1.0 API](http://swagger.testpoint.io?url=http://ausdigital.org/specs/ausdigital-syn-sol/1.0/swagger.json){:target="_blank"}   | [SYN-SOL 1.0 Issues](https://github.com/ausdigital/ausdigital-syn-sol/issues)  |

## Known Implementations

Known implementations (open source or otherwise) are listed here.  Please modify this page and make a pull request to add your own.

|Provider|Implementation URL|Comments|
|--------|------------------|--------|
|[testpoint.io](http://testpoint.io/) | [UBL JSON Syntax testpoint](http://testpoint.io/syn)| Free UBL JSON Syntax 1.0 spec transformation service and docker container|
|  |  |  |
