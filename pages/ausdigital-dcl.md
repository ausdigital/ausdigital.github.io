---
layout: page
title: Digital Capability Locator (DCL) Specification
permalink: /ausdigital-dcl/
---

# Digital Capability Locator (DCL) Specification

The framework assumes that there could be multiple publishers of business meta-data and e-business capabilities. Therefore, a simple way to ask, "where can I find information about the e-business capabilities of business X ?" is needed.  That is the purpose of the DCL. It is essentially a DNS lookup (NAPTR Record) using a business identifier (eg ABN) as the query and it returns the URL of the detailed metadata about that business.  In a given economy, there is usually only one DCL - often operated by a government authority.

* [DCL Github Repository](https://github.com/ausdigital/ausdigital-dcl)
* [DCL Slack Channel](https://ausdigital.slack.com/messages/spec-dcl/)

| Specification URL | Version | Status | API Definition | Issues List |
| ----------------- | ------  | ------ | -------------- | -------- |
| [DCL 1.0 spec](http://ausdigital.org/specs/ausdigital-dcl/1.0) | 1.0 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)  | [DCL 1.0 API](http://ausdigital.org/specs/ausdigital-dcl/1.0/api) | [DCL 1.0 Issues](https://github.com/ausdigital/ausdigital-dcl/issues)   |
| [DCL 2.0.0 spec](http://ausdigital.org/specs/ausdigital-dcl/2.0.0) | 2.0.0 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)  | [DCL 2.0.0 API](http://ausdigital.org/specs/ausdigital-dcl/2.0.0/api) | [DCL 2.0.0 Issues](https://github.com/ausdigital/ausdigital-dcl/issues)   |

## Known Implementations

Since there is usually only one DCL for a given national economy, the DCL service is normally implemented by a statutory authority - usually the issuer and registrar of the relevant business identifier.  In the Australian case, the identifier is the ABN and the DCL operator is expected to be the ATO.

Known implementations (open source or otherwise) are listed here.  Please modify this page and make a pull request to add your own.

|Provider|Implementation URL|Comments|
|--------|------------------|--------|
|[testpoint.io](http://testpoint.io/) | [dcl testpoint](http://testpoint.io/dcl)| Free test service and open source implementation|
|  |  |  |

