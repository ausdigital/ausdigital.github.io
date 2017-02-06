 * Spec ID: ausdigital.org/ausdigital-syn/1.0
 * ![raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)
 * Editor: the Digital Business Council (Council)
 * Contributors: 

# AusDigital UBL Syntax (SYN) 1.0 Specification

## Introduction

This eInvoicing Semantic Model Specification:

 * Incorporates common Invoice requirements for commercial, technical, financial and regulatory (e.g. Tax) usage;
 * Aligns with the Australian Reporting Dictionary (through incorporation);
 * Exploits the ability to share the model and gain efficiencies of a standardised data model;
 * Identifies a common ‘Core’ model;
 * Consistent reuse of standardised definitions and meanings provide greater opportunities to optimise Business Processes and ability to integrate information with further cost reduction; and
 * Makes use of a proven methodology;
  
The eInvoicing Semantic Model has been defined and elaborated in a consultative manner – reusing existing international standards

[Ausdigital eInvoice Semantic Model](https://github.com/ausdigital/ausdigital-bill/blob/master/docs/1.0/eInvoicing_Semantic_Model_v1.0.pdf)

[Ausdigital eInvoice Implementation Guide](https://github.com/ausdigital/ausdigital-syn/blob/master/docs/1.0/eInvoicing_Implementation_Guide_v1.0.pdf) 

The XML instances MUST comply with the [UBL 2.1 Specification](http://docs.oasis-open.org/ubl/UBL-2.1.html).

## Goals

The primary goal of the UBL Syntax (SYN) 1.0 Specification is to TBA.

The UBL Syntax (SYN) 1.0 Specification defines TBA.


## Status

This spec is an early draft for consuiltation.

This specification aims to support the Australian Digital Business Council
[eInvoicing initiative](http://ausdigital.org), and is under active
development at
[https://github.com/ausdigital/ausdigital-syn](https://github.com/ausdigital/ausdigital-syn).

Comments and feedback are encouraged and welcome. Pull requests with improvements are welcome too.


## Glossary

Phrase | Definition
------------ | -------------
ausdigital-syn/1 | This specification.
ausdigital-code/1 | Version 1 of the AusDigital [Code Lists Management (CODE)](http://ausdigital.org/code-lists) specification.
ausdigital-bill/1 | Version 1 of the AusDigital [Bill Semantics (BILL)](http://ausdigital.org/bill) specification.
ausdigital-syn/2 | Version 2 of the AusDigital [UBL Syntax(SYN)](http://ausdigital.org/syn) specification.

This service depends on - TBA.

The TBA specification depends on this document. Note, TBA.
 
## Licence

Copyright (c) 2016 the Editor and Contributors. All rights reserved.

This work is licensed under a Creative Commons Attribution 4.0 International License.

## Change Process

This document is governed by the [2/COSS](http://rfc.unprotocols.org/spec:2/COSS/) (COSS).


## Language

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119.


# XML Syntax for UBL documents

The eInvoicing Semantic Model also makes no assumption about the Data Format, syntax or transmission technology used. However in the Council's eInvoice Interoperability Framework the model is applied to a specific Data Format (UBL) [(OASIS UBL Technical Committee, 2013)](https://www.oasis-open.org/committees/ubl/).

The normative form for UBL documents is XML and the normative definition is the UBL XSD Schema library.


# Transformation API

The transformation API specification defiens a standard interface for lossless, schema-aware transformations 

* UBL2JSON : from standard namespace qualified UBL 2.1 XML and a simple JSON representation. 

The XML instances MUST comply with the [UBL 2.1 Specification](http://docs.oasis-open.org/ubl/UBL-2.1.html).

## API Specification

Is maintained at swaggerhub : **[UBL-JSON APIs](https://app.swaggerhub.com/api/ausdigital/ausdigital-syn/1.0)**

## UBL2JSON Error Response Codes

All error responses will comply with the ausdigital standard [RESTful Errors structure](https://app.swaggerhub.com/domains/ausdigital/ErrorModel/1.0).   

|Error Code | Error Message|
|-----------|--------------|
|ubl2json-01 |The source document is not a valid UBL 2.1 XML instance   |
|ubl2json-02 |Standard code-list scheme not found for {schemeID} at {XML element path}|
|ubl2json-02 |   |

## Sample UBL 2.1 XML

```
<n2:Invoice 
  xmlns:n2="urn:oasis:names:specification:ubl:schema:xsd:Invoice-2" 
  xmlns:cbc="urn:oasis:names:specification:ubl:schema:xsd:CommonBasicComponents-2" 
  xmlns:cac="urn:oasis:names:specification:ubl:schema:xsd:CommonAggregateComponents-2">
  <cbc:UBLVersionID>2.1</cbc:UBLVersionID>
  <cbc:CustomizationID schemeAgencyID="dbc">urn:resources.digitalbusinesscouncil.com.au:dbc:invoicing:documents:core invoice:xsd::core invoice 1##urn:resources.digitalbusinesscouncil.com.au:dbc:einvoicing:process:einvoicing03:ver1.0</cbc:CustomizationID>
  <cbc:ProfileID schemeAgencyID="dbc">urn:resources.digitalbusinesscouncil.com.au:dbc:einvoicing:ver1.0</cbc:ProfileID>
  <cbc:ID>TOSL-108-A</cbc:ID>
  <cbc:IssueDate>2016-07-01</cbc:IssueDate>
  <cbc:DueDate>2016-08-01</cbc:DueDate>
  <cbc:InvoiceTypeCode listAgencyID="6" listAgencyName="International Organization for Standardization" listName="Document Type Code" listVersionID="D10B" name="DocumentTypeCode" languageID="en" listURI="http://docs.oasis-open.org/ubl/os-UBL-2.1/cl/gc/special-purpose/DocumentTypeCode-2.1.gc" listSchemeURI="urn:un:unece:uncefact:codelist:standard:UNECE:DocumentNameCodeAccounting">81</cbc:InvoiceTypeCode>
  <cbc:Note>Credit Note</cbc:Note>
  <cbc:DocumentCurrencyCode listID="ISO 4217 Alpha" listAgencyID="5" listAgencyName="International Organization for Standardization" listName="Currency Code" listVersionID="2012-01-12" name="CurrencyCode" languageID="en" listURI="http://docs.oasis-open.org/ubl/os-UBL-2.1/cl/gc/default/CurrencyCode-2.1.gc" listSchemeURI="urn:un:unece:uncefact:codelist:standard:5:ISO42173A">AUD</cbc:DocumentCurrencyCode>
  <cbc:BuyerReference>CC-3352626</cbc:BuyerReference>
  <cac:InvoicePeriod>
    <cbc:StartDate>2016-05-01</cbc:StartDate>
    <cbc:EndDate>2016-06-01</cbc:EndDate>
  </cac:InvoicePeriod>
  <cac:OrderReference>
    <cbc:ID>SB002</cbc:ID>
  </cac:OrderReference>
  <cac:AccountingSupplierParty>
    <cac:Party>
      <cac:PartyIdentification>
        <cbc:ID schemeID="urn:oasis:names:tc:ebcore:partyid-type:iso6523:088" schemeAgencyID="GS1">4035811611014</cbc:ID>
      </cac:PartyIdentification>
      <cac:PartyName>
        <cbc:Name>ACME Holdings</cbc:Name>
      </cac:PartyName>
      <cac:PostalAddress>
        <cbc:CityName>Adelaide</cbc:CityName>
        <cbc:PostalZone>5000</cbc:PostalZone>
        <cbc:CountrySubentity>South Australia</cbc:CountrySubentity>
        <cac:AddressLine>
          <cbc:Line>88 Grenfell St</cbc:Line>
        </cac:AddressLine>
        <cac:Country>
          <cbc:IdentificationCode listAgencyID="5" listAgencyName="International Organization for Standardization" listName="Country Identification Code" listVersionID="SecondEdition2006VI-12" name="CountryIdentificationCode" languageID="en" listURI="http://docs.oasis-open.org/ubl/os-UBL-2.1/cl/gc/default/CountryIdentificationCode-2.1.gc" listSchemeURI="urn:un:unece:uncefact:identifierlist:standard:5:ISO316612A">AU</cbc:IdentificationCode>
        </cac:Country>
      </cac:PostalAddress>
      <cac:PartyLegalEntity>
        <cbc:CompanyID schemeID="urn:oasis:names:tc:ebcore:partyid-type:iso6523:0151" schemeAgencyID="GS1">987654321</cbc:CompanyID>
      </cac:PartyLegalEntity>
    </cac:Party>
  </cac:AccountingSupplierParty>
  <cac:AccountingCustomerParty>
    <cac:Party>
      <cac:PartyIdentification>
        <cbc:ID schemeID="urn:oasis:names:tc:ebcore:partyid-type:iso6523:0151" schemeAgencyID="GS1">51083392303</cbc:ID>
      </cac:PartyIdentification>
      <cac:PartyName>
        <cbc:Name>Governmment Agency</cbc:Name>
      </cac:PartyName>
      <cac:PostalAddress>
        <cbc:CityName>Willunga</cbc:CityName>
        <cbc:PostalZone>5172</cbc:PostalZone>
        <cbc:CountrySubentity>South Australia</cbc:CountrySubentity>
        <cac:AddressLine>
          <cbc:Line>Delabole Road</cbc:Line>
        </cac:AddressLine>
        <cac:Country>
          <cbc:IdentificationCode listAgencyID="5" listAgencyName="International Organization for Standardization" listName="Country Identification Code" listVersionID="SecondEdition2006VI-12" name="CountryIdentificationCode" languageID="en" listURI="http://docs.oasis-open.org/ubl/os-UBL-2.1/cl/gc/default/CountryIdentificationCode-2.1.gc" listSchemeURI="urn:un:unece:uncefact:identifierlist:standard:5:ISO316612A">AU</cbc:IdentificationCode>
        </cac:Country>
      </cac:PostalAddress>
      <cac:PartyLegalEntity>
        <cbc:CompanyID schemeID="urn:oasis:names:tc:ebcore:partyid-type:iso6523:0151" schemeAgencyID="GS1">51083392303</cbc:CompanyID>
      </cac:PartyLegalEntity>
    </cac:Party>
    <cac:BuyerContact>
      <cbc:ID>Tony Curtis</cbc:ID>
      <cbc:Telephone>(08) 8556 2345</cbc:Telephone>
      <cbc:ElectronicMail>curtis@willunga.gov.au</cbc:ElectronicMail>
    </cac:BuyerContact>
  </cac:AccountingCustomerParty>
  <cac:Delivery>
    <cbc:ActualDeliveryDate>2016-03-02</cbc:ActualDeliveryDate>
    <cac:DeliveryAddress>
      <cbc:CityName>Adelaide</cbc:CityName>
      <cbc:PostalZone>5000</cbc:PostalZone>
      <cbc:CountrySubentity>South Australia</cbc:CountrySubentity>
      <cac:AddressLine>
        <cbc:Line>202 North Terrace</cbc:Line>
      </cac:AddressLine>
      <cac:Country>
        <cbc:IdentificationCode listAgencyID="5" listAgencyName="International Organization for Standardization" listName="Country Identification Code" listVersionID="SecondEdition2006VI-12" name="CountryIdentificationCode" languageID="en" listURI="http://docs.oasis-open.org/ubl/os-UBL-2.1/cl/gc/default/CountryIdentificationCode-2.1.gc" listSchemeURI="urn:un:unece:uncefact:identifierlist:standard:5:ISO316612A">AU</cbc:IdentificationCode>
      </cac:Country>
    </cac:DeliveryAddress>
  </cac:Delivery>
  <cac:PaymentMeans>
    <cbc:ID>EFT</cbc:ID>
    <cbc:PaymentMeansCode listID="UN/ECE 4461" listAgencyID="6" listAgencyName="United Nations Economic Commission for Europe" listName="Payment Means Code" listVersionID="D10B" name="PaymentMeansCode" languageID="en" listURI="http://docs.oasis-open.org/ubl/os-UBL-2.1/cl/gc/default/PaymentMeansCode-2.1.gc" listSchemeURI="urn:un:unece:uncefact:codelist:standard:UNECE:PaymentMeansCode">2</cbc:PaymentMeansCode>
    <cbc:InstructionID>888276612262653</cbc:InstructionID>
    <cac:PayeeFinancialAccount>
      <cbc:ID>2000987211</cbc:ID>
      <cac:FinancialInstitutionBranch>
        <cbc:ID schemeName="BSB">086016</cbc:ID>
        <cbc:Name>NAB Adelaide</cbc:Name>
      </cac:FinancialInstitutionBranch>
    </cac:PayeeFinancialAccount>
  </cac:PaymentMeans>
  <cac:TaxTotal>
    <cbc:TaxAmount>250.00</cbc:TaxAmount>
  </cac:TaxTotal>
  <cac:LegalMonetaryTotal>
    <cbc:LineExtensionAmount>2500.00</cbc:LineExtensionAmount>
    <cbc:TaxExclusiveAmount>2500.00</cbc:TaxExclusiveAmount>
    <cbc:TaxInclusiveAmount>2750.00</cbc:TaxInclusiveAmount>
    <cbc:PayableAmount>2750.00</cbc:PayableAmount>
  </cac:LegalMonetaryTotal>
  <cac:InvoiceLine>
    <cbc:ID>1</cbc:ID>
    <cbc:Note>A variety of Widgets</cbc:Note>
    <cbc:InvoicedQuantity>200</cbc:InvoicedQuantity>
    <cbc:LineExtensionAmount>2000.00</cbc:LineExtensionAmount>
    <cac:TaxTotal>
      <cbc:TaxAmount>200.00</cbc:TaxAmount>
      <cac:TaxSubtotal>
        <cbc:TaxAmount>10.00</cbc:TaxAmount>
        <cac:TaxCategory>
          <cac:TaxScheme>
            <cbc:ID>GST</cbc:ID>
          </cac:TaxScheme>
        </cac:TaxCategory>
      </cac:TaxSubtotal>
    </cac:TaxTotal>
    <cac:Item>
      <cbc:Description>Widget</cbc:Description>
      <cac:SellersItemIdentification>
        <cbc:ID>WDGT-A1733-0436</cbc:ID>
      </cac:SellersItemIdentification>
      <cac:StandardItemIdentification>
        <cbc:ID schemeID="GTIN" schemeAgencyID="GS1">9501101021037</cbc:ID>
      </cac:StandardItemIdentification>
    </cac:Item>
    <cac:Price>
      <cbc:PriceAmount>10.00</cbc:PriceAmount>
      <cbc:BaseQuantity>1</cbc:BaseQuantity>
    </cac:Price>
  </cac:InvoiceLine>
  <cac:InvoiceLine>
    <cbc:ID>2</cbc:ID>
    <cbc:Note>Widget attachments</cbc:Note>
    <cbc:InvoicedQuantity>200</cbc:InvoicedQuantity>
    <cbc:LineExtensionAmount>500.00</cbc:LineExtensionAmount>
    <cac:TaxTotal>
      <cbc:TaxAmount>50.00</cbc:TaxAmount>
      <cac:TaxSubtotal>
        <cbc:TaxAmount>10.00</cbc:TaxAmount>
        <cac:TaxCategory>
          <cac:TaxScheme>
            <cbc:ID>GST</cbc:ID>
          </cac:TaxScheme>
        </cac:TaxCategory>
      </cac:TaxSubtotal>
    </cac:TaxTotal>
    <cac:Item>
      <cbc:Description>Widget screws</cbc:Description>
      <cac:SellersItemIdentification>
        <cbc:ID>WDGT-A1733-0437</cbc:ID>
      </cac:SellersItemIdentification>
      <cac:StandardItemIdentification>
        <cbc:ID schemeID="GTIN" schemeAgencyID="GS1">9501101021038</cbc:ID>
      </cac:StandardItemIdentification>
    </cac:Item>
    <cac:Price>
      <cbc:PriceAmount>2.50</cbc:PriceAmount>
      <cbc:BaseQuantity>1</cbc:BaseQuantity>
    </cac:Price>
  </cac:InvoiceLine>
</n2:Invoice>
```

# Validation Specification

The validation specification defines a standard for the validation of UBL XML instances at three levels:

* Structure : that the XML instance conforms to the corresponding XSD schema
* Codes : that the code values used in the XML instance are defined in a relevant code-list, which may be either a core code-list or a context specific code list. 
* Rules : that the XML instance complies with the specific business rules for the implementation context identified by the "ProfileID" element in the XML instance.

The following standards are used there:

[Oasis Code List Representation (Genericode) Version 1.0](http://docs.oasis-open.org/codelist/cs-genericode-1.0/doc/oasis-code-list-representation-genericode.html)

[Context/value association using genericode 1.0](http://docs.oasis-open.org/codelist/cs01-ContextValueAssociation-1.0/doc/context-value-association.html)

[ISO Schematron](http://schematron.com/)

The XML instances MUST comply with the [UBL 2.1 Specification](http://docs.oasis-open.org/ubl/UBL-2.1.html).

## Validation Context

As defined by the [UBL Customisation Guide](http://docs.oasis-open.org/ubl/guidelines/UBL2-Customization1.0cs01.pdf) and as implemented by the DBC, UBL allows for the notions of "CustomizationID" and "ProfileID" that are used to define addiotnal restrictions or rules that apply in a specific geographic or industry or porcess context. In general, the "CustomizationID" represents a broad context whilst "ProfileID" reflects further restritions within that broad context. The Ausdigital.org suite of semantic specifications uses these two identifiers as follows:

* There is one "CustomizationID" value that indicates the Australian Digitial Business Council restrictions on the global UBL documents. The set of DBC restrictions is evident when comparing the DBC [CoreInvoice Schema](https://github.com/ausdigital/ausdigital-bill/blob/master/resources/ausdigital-syn/1.0/spec/maindoc/CoreInvoice-1.0.xsd) with the equivalent global UBL 2.1 [Invoice Schema](http://docs.oasis-open.org/ubl/os-UBL-2.1/xsdrt/maindoc/UBL-Invoice-2.1.xsd).  
* There are a number of "ProfileID" values that represent the rules that apply when the core invoice is used in specific business processes such as RCTI, TaXReceipt, CreditNote, etc.  The rules are defined with each semantic specification (eg [billing semantics](https://github.com/ausdigital/ausdigital-bill)

All validation rules are tagged with the relevant customizationID(s) and profileID(s) that apply. Each instance document also contains both these identifiers. Therefore the validation model is to examine the instance document to determine which validation rules should be applied.


# Related Material

 * AusDigital eInvoicing Implementation Guide (v1.0, available [here](https://github.com/ausdigital/ausdigital-syn/blob/master/docs/1.0/eInvoicing_Implementation_Guide_v1.0.pdf)), which provides background to the [AusDigital](http://ausdigital.org) community process.
 * [GitHub issues](https://github.com/ausdigital/ausdigital-syn/issues/) for collaborating on the development of the SYN.
 * A reference [SYN service](https://syn.testpoint.io/) (for testing and development purposes).
 * Free, Open-Source Software [SYN implementation](https://github.com/test-point/testpoint-syn).
 * An automated [SYN test suite](https://github.com/test-point/testpoint-syn).
