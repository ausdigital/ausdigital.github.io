---
layout: page
title: Business Case
permalink: /business-case/
---

# The e-Invoicing Business Case

## Executive Summary

Businesses in the Australian economy exchange approximately 1 Billion invoices per year to a total value of around AUD $4 trillion and, on average, payment is made 55 days after the invoice is issued.    

* Each invoice costs an average of $20 AUD to process due to manual handling (re-keying) and errors (mis-keying). If all invoices were exchanged automatically between buyer and seller financial systems then there is a potential to avoid mistakes and re-keying and consequently improve national productivity by up to $20 billion per year.
* Around $600 billion ($4 trillion x 55/365 days) is held in accounts payable processes at any time and about 20% of that is debt to cashflow contrained small business suppliers that have no alternative than to fund cashflow from homeloans and credit cards.  If every invoice and invoice response were digitally signed and written to the block-chain then small business would have access to a new trade financing instrument that could inject an additional $100 Billion of growth-funding cashflow into the national economy.

But the uptake of e-invoicing in Australia is approximately 10% to 15% and almost none of them are suitable for trade financing.  By world standards, Australia is a laggard.   [Ausdigital standards](http://ausdigital.org/) represent the most modern and lowest cost model for e-invoicing that, if adopted widely, would allow Australia to leapfrog the rest of the world.

Numbers like $20Bn of annual productivity gains and $100Bn of additional cashflow funding are too big to throw around without some evidence to support them.  The list of references at the bottom of this page and the assessment of each should provide confidence that the numbers are, if anything, conservative.

## e-Invoicing and efficiency

e-Invoicing efficiency gains are mostly derived from accounts payable (AP) automation;

* Straight-through-processing for the invoice recipient means there is no manual re-keying.
* Straight through processing of strucutured invoice data is also less error prone than bulk scanning & OCR processes.
* Automated reconciliation against orders and goods reciepts allows for automated internal AP workflows.
* Status responses (eg received, approved / disputed, paid) to the seller avoids manual handling of payment status enquiries.
* Reduced errors (around 15% of paper invoices have some kind of processing mistake in Australia).

These benefits are realised when buyer and seller ledger systems exchange structured invoice data in accordance to an agreed standard that different ledger systems can understand. The benefits mostly accrue to the buyer through AP automation and amount to between $10 and $50 per invoice depending on the efficiency of the manual process which are replaced. 

The seller system is already the source of invoice data and so there is little efficiency difference for the seller between e-mailing a PDF and sending structured data.  However the main advantage for the seller is confidence that the buyer has received the invoice.

## e-Invocing and cashflow

As described above, there is a very large amount of cashflow tied up in buyer accounts payable at any one time. Large suppliers have relatively good access to lines of credit at competitive rates and so suffer less from cashflow constraints.  However small suppliers face much greater challenges because lenders are generally unwilling to risk lending to small suppliers without independent personal collateral such as the family home or personal credit cards.  Even though a small supplier may have a large receivables balance from large and low risk buyers, lenders will not mormally fund that balance based on paper invoices because they are open to fraud - it's easy to fake a paper invoice.

However, if implemented correctly, an e-invoicing framework can deliver new cashflow funding sources if the lender can trust the electronic messages.  This requires three things of the e-invoicing framework;

* The invoice must be digitally signed by the seller using a trusted identity provider.
* Invoice response documents (eg "I got your invoice number 1234 and have approved it for payment in 60 days") must also be digitally signed by the buyer using a trusted identity provider.
* Both the invoice and response messages must be notarised by an independent third party so that the conversation is on a permanent and non-repudiable record.  

The signed and notarised invocing conversation is effectively a financial grade tradeable instrument and allows lenders to make a risk assessment based on the likelihood that the buyer will pay rather than seeking peronsal equity collateral from the seller.  The user experience for the SME seller can be that payment from trade financers can be made immediately after receiving a signed invoice response - irrespective of the actual buyer payment terms.  

## e-invoicing solution choices do matter!

Although the benefits sound compelling, there is a significant risk that they may not be realised.  

* Although there are efficiency savings in the order of $20 per invoice, if the transaction costs imposed by the e-invoicing framework are of a similar order of magnitude then the net benefit to the economy is zero. Frameorks such as the european "4-corner model" that are based on connecting up traditional EDI hubs are costly.  Some of the largest EDI hubs in operation today charge trasaction fees as a % of invoice value at prices that are only a little less than the potential efficiency savings.  
* Cashflow financing for SME sellers will be optimised when signed and notarised invoice messages are tradeable in a competitive financial market. Although invoice factoring is a service that is often available via EDI hubs, it is usually within a closed market of value-add services from the Hub provider, which inevitably increases the finance costs to the seller.

The Ausdigital specifications published on this site avoid both these problems;

* Messaging is peer-to-peer between ledger systems and uses ubiquitous internet protocols.  There is no lock-in opportunity and fees from network service providers will reflect a commodity style "race to the bottom" allowing ledger software vendors to choose the best value provider.  Our modelling indicates that transactions costs should be no more than a few cents per invoice.
* Digital signatures from independant trust providers (typically banks or government) coupled with independent notarisation avoids lock in by any factoring provider and allows the seller to seek the best funding terms from a competitive market using a very high quality record. Financial service providers have confirmed that the market would offer immediate payment of notarised invoices for around 1% of invoice value.

## The role for government

e-Invocing is very much a business-to-business process so it's tempting to think that there should be no government "interference".  Whilst it is certainly true that the market is likely to deliver the best technical solutions at the lowest cost, there are two important things that a government can do to help realise the efficiency and cashflow potential described here.

* Identity services.  As the authoritative registrar of business identifers (ie the ABN), the government is uniquely positioned to provide the highest integrity identity services at the lowest cost to the economy.  Identity is a foundational service and would be much more costly for any provider other than government to implement. Fortunately, the Australian government already has the necessary infrastructure in the form of the [VANguard](http://www.vanguard.business.gov.au/Pages/default.aspx) service from the Department of Industry.  Unfirtunately, although technically VANguard is immediately usable, policy constraints currently limit it's to B2G transactions only.  We hope that this constraint will be removed very soon.
* implement the Ausdigital standards as a large buyer.  This would stimulate the market and provide incentives for ledger vendors to support the standard so that their customers can send electronic invoices to government.  Notarised responses from government buyers would also stimulate the trade financing market with a high value (government represents around 15% of the economy) and very low risk buyer. Aside from the national economy benefits, government as a large buyer would recover any implementation costs very quickly as it will enjoy the same AP automation benefits that any commercial buyer would experience.

There should be no need for any government mandate of any e-invoicing framework.  Just leadership by example.

## References

The following references provide the necessary evidence to support this business case.

1.  This [e-invoicing white paper](https://fedpaymentsimprovement.org/wp-content/uploads/e-invoicing-white-paper.pdf) from the [US Federal Reserve Banks](https://fedpaymentsimprovement.org/) provides a nice summary of many other studies and reports.  It confirms a general rule of thumb that a developed economy will have a total annual B2B invoice volume (in billions of invoices) between one and two times it's GDP in trillions.  The USA issues about 25 billion invoices and has a GDP of $18 trillion.  Australia has a GDP of $1.4 trillion and should therefore issue between 1 and 2 billion B2B invoices per year.
2. This [2016 payments annual review](http://www.apca.com.au/docs/default-source/annual-reviews/apca-annual-review-2016.pdf) from [APCA] shows both volume and value for Australia's main payment methods. Ignoring the high value clearing system (which would be mostly financial securities trading) and EFTPOS/Cards (which would be mostly B2C purchases), then the remaining direct credits volume can reasonably be taken to represent the majority of B2B payments.  There are 2.3 billion direct credit payment transactions to a value of $8 trillion in Australia - which would seem to confirm that 1 billion B2B invoices with a total value of $4 trillion is a conservative estimate for the Australian economy - and roughly the same as top down GDP based estimate.
3. This [late payments discussion paper](https://industry.gov.au/smallbusiness/Documents/PromptPaymentProtocolDiscussionPaper22July2013.pdf) from the Australian [Federal Dept of Industry](https://industry.gov.au) confirms the average payment times for Austrlain invoices at around 55 days - one of the worst in the world.  The 55 day figure is also verified by this [State of Late Payments Reposrt](http://info.marketinvoice.com/hubfs/The_State_of_Late_Payment_MarketInvoice_2016.pdf) from [MarketInvoice](https://www.marketinvoice.com), a UK trade financing business.  It shows Australia at the bottom of the late payers leage table at 26 days later than the standard 30 days terms (so totalling 56 days).  If the total annual value of B2B invoices is conservtively $4 trillion then this late payment fiugure means that around $600 billion of cashflow is locked up Buyer's accounts payable at any one time in Australia.
4. This [e-Invoicing in Australia Report](http://www.sbr.gov.au/about-sbr/reports/digital-transformation-sbr-strategic-reports/implementing-e-invoicing-on-a-broad-scale) commissioned by the ATO and provided by [Billentis](http://www.billentis.com/), a European e-invoicing advisory confirms the rough volume of about 1 billion B2B invoices per year in Australia.  It also estimates a procesing cost of around $30 per paper invoice - which includes both seller and buyer costs for a single invoice document.  It also estimates about 10% to 15% uptake of e-invocing in Australia which is below the european average, far below the latin american average and roughly equal to the US average.
5. This [GDP and Gross Output Statistics](https://www.bea.gov/iTable/iTable.cfm?ReqID=51&step=1#reqid=51&step=51&isuri=1&5114=a&5102=15) table from the US [Dept of Commerce Bureau of Economic Analysis](https://www.bea.gov) defines a measure of national productivity called [gross output](https://www.bea.gov/faq/index.cfm?faq_id=1034) which is a better indicator of total B2B sales in an eoonomy because, unlike GDP calculations, it does not look only at the final output of the supply chain but also includes the transactions along the supply chain.  Gross output is roughly double GDP.  This measure provides an additional verification for Australian total B2B sales (ie invoice) value at double $1.4 trillion USD - about $4 trillion AUD.  
6. This Reserve bank of Australia [Small Business Conditions and Finance](http://www.rba.gov.au/publications/confs/2015/) report includes a number of separate research papers that provide considerable depth of analysis on the question of how Australian small businesses fund their growth.  One paper shows quite clearly that the propensity for financial institutions to provide trade financing (ie loans against invoices) virtually evaporated after the financial crisis and has not substantially returned (especially in Australia).  Not surprisingly, there is a corresponding finding that 80% of small busineses with debt include home family home equity and personal credit card collateral - because these loans are considered less risky.  The extent to which lack of access to business finance is choking SME growth and employment is also found to be more significant in the Ausrtalian economy than some others that have more mature trade finance markets.
7. These are a multitude of reports that provide some estimates of the average processing cost of a paper invoice.  Estimates vary from around $5 UD to as much as $50 USD.  Not surprisingly, estimates from reports that are funded by e-invoicjng service providers attach a higher cost to paper processing.  This [assessment of accounts payable cost](http://ww2.cfo.com/expense-management/2015/06/metric-month-accounts-payable-process-cost/) from CFO magazine is drawn from a survey of US firms and simply divides total AP costs by invoice volume for a numebr of firms.  It is likely to be less biased by solution marketing imperitives and it finds a median AP costs of $8 USD (about $12 AUD) per invoice.  This represents only the buyer side (AP) costs.  Seller side (AR) costs must also be factored but are usually less than AP costs because invoices are issued by AR systems and re-keyed by AP system administrators.  Nevertheless, an average benchmark of around AUD $20 per invoice for total AR and AP processing is likley to be a conservative estimate.
