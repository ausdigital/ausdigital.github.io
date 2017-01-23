---
layout: page
title: TAP Gateway
permalink: /tap-gateway/
---

# The TAP Gateway specification

The Transaction Access Point Gateway (TAP-GW) is an optional, standardised interface for integrating ledger systems with a TAP service layer. This is an optional extension to the TAP protocol that separation ledger systems from the TAP service layer.

Significantly, the TAP layer can (and therefore should) be kept out of the ledger service's trust zone. It does not need access to key material used to sign, encrypt or decrypt business messages. Be cleanly separating the TAP service from the ledger service, the TAP-GW protocol ensures the TAP is a neutral carrier of business messages.

Supporting the TAP-GW specification helps to commoditise the network so that ledger software providers or their individual business custoemrs can choose any provider and easily switch between them because they all provide the same gateway interface.

* [TAP-GW GitHub repository](https://github.com/ausdigital/ausdigital-tap-gw)
* [TAP-GW Slack channel](https://ausdigital.slack.com/messages/spec-tap-gw/)

| Specification URL | Version | Status | API Definition |  Issues List |
| ----------------- | ------  | ------ | -------------- |  ----------- |
| [TAP-GW 0.1 spec](http://ausdigital-tap-gw.readthedocs.io/) | 0.1 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)  | coming soon | [TAP-GW Issues](https://github.com/ausdigital/ausdigital-tap-gw/issues)  |

## Known Implementations

Known implementations (open source or otherwise) are listed here.  Please modify this page and make a pull request to add your own.

|Provider|Implementation URL|Comments|
|--------|------------------|--------|
|[testpoint.io](http://testpoint.io/) | [gateway testpoint](http://testpoint.io/tap-gw)| Free gateway testing service coming soon|
|  |  |  |
