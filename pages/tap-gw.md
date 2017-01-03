---
layout: page
title: TAP Gateway
permalink: /tap-gateway/
---

# The TAP Gateway specification

The Transaction Access Point Gateway (TAP-GW) is an optional, standardised interface for integrating ledger systems with a TAP service layer. This is an optional extension to the TAP protocol that separation ledger systems from the TAP service layer.

Significantly, the TAP layer can (and therefor should) be kept out of the ledger service's trust zone. It does not need access to key material used to sign, encrypt or decrypt business messages. Be cleanly separating the TAP service from the ledger service, the TAP-GW protocol ensures the TAP is a neutral carrier of business messages.

Supporting the TAP-GW specification helps to driving trust out of the TAP layer, concentrating it at the ledger systems. This maximises autonomy and security of network participants.

* [TAP GitHub repository](https://github.com/ausdigital/gateway)
* [TAP Slack channel](https://ausdigital.slack.com/messages/spec-tap-gw/)

| Specification URL | Version | Status | API Definition | Test Service | Issues List |
| ----------------- | ------  | ------ | -------------- | ------------ | -------- |
| [TAP-GW 0.1 spec](http://gateway.readthedocs.io/) | 0.1 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)  | N/A | N/A | [TAP-GW Issues](https://github.com/ausdigital/gateway/issues)  |
