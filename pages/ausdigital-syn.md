---
layout: page
title: UBL Syntax (SYN) Specification
permalink: /ausdigital-syn/
---

# UBL Syntax (SYN) Specification

This specification describes a syntax and processing model for UBL semantics. 

Version 1.0:

* An XML syntax model for UBL semantics.
* The XSD/Schematron/Genericode validation.

* [SYN 1.0 GitHub repository](https://github.com/ausdigital/ausdigital-syn-v1/)
* [SYN 1.0 Slack channel](https://ausdigital.slack.com/messages/spec-syn-v1/) ([you must signup to ausdigital slack first](https://chat.ausdigital.org/))

Version 2.0:

* A simple JSON syntax model for UBL semantics.
* A lossless transformation model between UBL XML (UBL Syntax 1.0 spec) and JSON (UBL Syntax 2.0 spec) representations.
* A simple JSON processing model based on a RESTful Validation API.

The intent of UBL Syntax 2.0 spec is to provide developers with a much simpler implementation model than the XSD/Schematron/Genericode alternative whilst maintaining interoperability with the UBL XML standard.

* [SYN 2.0 GitHub repository](https://github.com/ausdigital/ausdigital-syn)
* [SYN 2.0 Slack channel](https://ausdigital.slack.com/messages/spec-syn/)

| Specification URL | Version | Status | API Definition | Issues List |
| ----------------- | ------  | ------ | -------------- | ----------- |
| [SYN 1.0 spec](http://ausdigital.org/specs/ausdigital-syn/1.0/) | 1.0 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg) | N/A | [SYN 1.0 Issues](https://github.com/ausdigital/ausdigital-syn-v1/issues)  |
| [SYN 2.0 spec](http://ausdigital.org/specs/ausdigital-syn/2.0/) | 2.0 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg) | [SYN 2.0 API](http://ausdigital.org/specs/ausdigital-syn/2.0/api)   | [SYN 2.0 Issues](https://github.com/ausdigital/ausdigital-syn/issues)  |

## Known Implementations

Known implementations (open source or otherwise) are listed here.  Please modify this page and make a pull request to add your own.

|Provider|Implementation URL|Comments|
|--------|------------------|--------|
|[testpoint.io](http://testpoint.io/) | [UBL Syntax testpoint](http://testpoint.io/syn)| Free UBL Syntax 2.0 spec transformation service and docker container|
|  |  |  |
