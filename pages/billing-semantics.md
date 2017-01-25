---
layout: page
title: billing semantics
permalink: /billing-semantics/
---

# Billing Semantics specification

The Billing Specifications are based on [OASIS UBL2.1](http://docs.oasis-open.org/ubl/UBL-2.1.html) [billing semantics](http://docs.oasis-open.org/ubl/os-UBL-2.1/UBL-2.1.html#S-BILLING) and include the Invoice, Credit Note, Debit Note, and Application Response documents.  The process roles are buyer and seller.  The invoice specification is semantically identical to the to [ADBC e-invoice semantic model](http://digitalbusinesscouncil.com.au/accreditation/documents/42381/download) but adds more clarity around the invoice state lifecycle.

* [Billing GitHub repository](https://github.com/ausdigital/ausdigital-bill)
* [Billing Slack Channel](https://ausdigital.slack.com/messages/spec-bill/)

| Specification URL | Version | Status | API Definition | Issues List |
| ----------------- | ------  | ------ | -------------- | ----------- |
| [Billing 1.0 spec](http://ausdigital-bill.readthedocs.io/) | 1.0 | ![Raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg) | [Billing 1.0 API](https://swaggerhub.com/api/ausdigital/ausdigital-ubl-json/1.0) |  [Billing 1.0 Issues](https://github.com/ausdigital/ausdigital-bill/issues)  |

## Known Implementations

Known implementations (open source or otherwise) are listed here.  Please modify this page and make a pull request to add your own.

|Provider|Implementation URL|Comments|
|--------|------------------|--------|
|[testpoint.io](http://testpoint.io/) | [billing testpoint](http://testpoint.io/bill)| Free document validator and message sender|
|  |  |  |

