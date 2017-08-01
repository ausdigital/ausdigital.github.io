---
layout: page
title: Transaction Access Point (TAP) Specification
permalink: /ausdigital-tap/
---

# Transaction Access Point (TAP) Specification

The ledger access point, is the service interface for a given business and so hosts the end-point to which business documents are sent. The access point is an availability mediator (allowing specific businesses to have intermittent connectivity) and is responsible for signature validation and submitting transactions to the Notary service.

* [TAP GitHub repository](https://github.com/ausdigital/ausdigital-tap)
* [TAP Slack channel](https://ausdigital.slack.com/messages/spec-tap/) ([you must signup to ausdigital slack first](https://chat.ausdigital.org/))

| Specification URL | Version | Status | API Definition | Issues List |
| ----------------- | ------  | ------ | -------------- |  ---------- |
| [TAP 1.0 spec](http://ausdigital.org/specs/ausdigital-tap/1.0/) | 1.0 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)  | N/A |  [TAP 1.0 Issues](https://github.com/ausdigital/ausdigital-tap-v1/issues)  |
| [TAP 2.0 spec](http://ausdigital.org/specs/ausdigital-tap/2.0/) | 2.0 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)  | [TAP 2.0 API](http://swagger.testpoint.io?url=http://ausdigital.org/specs/ausdigital-tap/2.0/swagger.yaml){:target="_blank"}, [TAP 2.0 Callback API](http://swagger.testpoint.io?url=http://ausdigital.org/specs/ausdigital-tap/2.0/callback-swagger.yaml){:target="_blank"} |  [TAP 2.0 Issues](https://github.com/ausdigital/ausdigital-tap/issues)  |

## Known Implementations

Known implementations (open source or otherwise) are listed here.  Please modify this page and make a pull request to add your own.

|Provider|Implementation URL|Comments|
|--------|------------------|--------|
|[testpoint.io](http://testpoint.io/) | [access point testpoint](http://testpoint.io/tap)| Free access point testing service coming soon|
|  |  |  |
