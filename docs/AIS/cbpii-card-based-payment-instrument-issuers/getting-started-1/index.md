---
title: Getting started
excerpt: This section explains the prerequisites for confirmation of funds
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
Open Banking API specifications support CoF services for Card Based Payment Instrument Issuers (CBPIIs). These services allow PSUs to provide explicit consent to an ASPSP, so that they can respond to confirmation of funds requests from CBPIIs, limited to a yes or no.

<Accordion title="Legal Background - Regulation 68 of the PSRs" icon="exclamation-triangle">
  Regulation 68 of the PSRs provides a mechanism whereby payment service providers (PSPs) issue a card based instrument which is linked to an account or accounts held at one or more different ASPSPs (provided those accounts are accessible online) and request a confirmation on the availability of funds.
</Accordion>

One of the primary ambitions of these guidelines is to provide simplification and consistency throughout each stage of the Open Banking implementation.
As such, we have defined a core set of PSU journeys for CBPIIs.

The payment service provider that issues the payment instrument is known as a Card-Based Payment Instrument Issuer or CBPII.

When the PSU uses the card-based payment instrument to initiate a payment transaction, the CBPII is entitled to request a confirmation from the PSUs ASPSP to which the account is linked, to confirm whether there are sufficient funds available for the transaction amount. The ASPSP is obliged to respond with an immediate 'yes/no' answer, provided the relevant regulatory requirements are met.
