---
layout: page
title: Digital Capability Publisher (DCP) Specification
permalink: /ausdigital-dcp/
---

# Digital Capability Publisher (DCP) Specification

The framework depends heavily on the ability to discover detailed service information for any given business identifier.  The DCP maintains a list of businesses, with a list of services for each business. Each service lists supported document formats and transport protocols and holds a digital certificate for message signing and encryption.

* [DCP Github Repository](https://github.com/ausdigital/ausdigital-dcp)
* [DCP Slack Channel](https://ausdigital.slack.com/messages/spec-dcp/)

| Specification URL | Version | Status | API Definition |  Issues List |
| ----------------- | ------- | ------ | -------------- |  ----------- |
| [DCP 1.0 spec](http://ausdigital.org/specs/ausdigital-dcp/1.0/) | 1.0 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg) | [DCP 1.0 API](http://ausdigital.org/specs/ausdigital-dcp/1.0/api)  | [DCP 1.0 Issues](https://github.com/ausdigital/ausdigital-dcp/issues)    |

## Known Implementations

Known implementations (open source or otherwise) are listed here.  Please modify this page and make a pull request to add your own.

|Provider|Implementation URL|Comments|
|--------|------------------|--------|
|[testpoint.io](http://testpoint.io/) | [dcp testpoint](http://testpoint.io/dcp)| Free dcp service and open source implementation|
|[Philip Helger](https://github.com/phax) | [phoss SMP](https://github.com/phax/peppol-smp-server)| Java based OSS solution (Apache2) that can be [configured](https://github.com/phax/peppol-smp-server/wiki/AusDigital-DCP) to run as DCP. Note: The read API is compatible but write API has some differences. |
|  |  |  |
