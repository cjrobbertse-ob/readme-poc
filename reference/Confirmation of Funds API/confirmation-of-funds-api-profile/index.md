---
title: Confirmation of Funds API Profile
excerpt: >-
  The Confirmation of Funds API Profile describes the flows and common
  functionality for CBPII
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
next:
  description: Check out the APIs below
---
## Overview

A **Card Based Payment Instrument Issuer (CBPII)** is a specialized payment service provider that issues modern payment instruments, including virtual cards and e-wallets, which can be linked to customer accounts held at different financial institutions. CBPIIs enable seamless digital payments while providing enhanced security and convenience.

<br />

<Callout icon="🚧" theme="warn">
  I wonder if having some obvious 'who this applies to' wording near the top would be useful. Should include the PSD2 role they need to access in UK, e.g. AISP for AIS etc
</Callout>

## How CBPIIs Work

CBPIIs enable customers to use payment instruments such as virtual cards and e-wallets that are connected to their existing bank accounts without requiring separate account opening. The process is streamlined for better user experience:

1. **Transaction Initiation:** Customer uses the virtual card or e-wallet to make a payment.
2. **Funds Confirmation:** CBPII requests confirmation of available funds from the account provider. This is the capability that utilises Open Banking standards.
3. **Authorization:** Transaction is authorized based on fund availability and authentication.
4. **Processing:** Payment is processed through the appropriate payment networks.

The diagram below provides a general outline of a confirmation of funds request and flow using the Confirmation of Funds APIs. It assumes a CBPII has issued a card to a PSU, and the PSU would like to use a PSD2 in-scope account as a funding mechanism for that card.

![](https://files.readme.io/7e880fd49d256bc7cc4803e06d3d73c1325d4ecdecd9bcbd1bf0d56a62fb5483-image.png)

<Callout icon="🚧" theme="warn">
  I like having the 'triangle' diagram on this page.  Having the sequence diagram in an accordion would also be useful, somewhere near the "what's in this PAI profile" below.
</Callout>

CBPIIs offer several advantages for businesses looking to modernize their payment infrastructure:

## Use Cases

### Consumer Applications

* **E-commerce Integration**: One-click payments for online shopping.
* **Mobile Payments**: In-app purchases and contactless transactions.
* **Subscription Management**: Recurring payment handling with enhanced security.

### Corporate Payments

* **Virtual Corporate Cards**: Streamlined expense management and procurement.
* **B2B Transactions**: Secure business-to-business payment processing.
* **Travel & Entertainment**: Dynamic spending controls and real-time approvals.

### Financial Services

* **Embedded Finance**: Payment capabilities integrated into non-financial platforms.
* **Marketplace Payments**: Multi-party transaction facilitation.
* **Cross-Border Transfers**: International payment processing with competitive rates.

## Benefits for Businesses

<Callout icon="🚧" theme="warn">
  Is this for us to call out in the spec?
</Callout>

<Cards columns={2}>
  <Card title="Speed & Efficiency" icon="bolt">
    Instant confirmation of funds availability and faster payment processing compared to traditional methods.
  </Card>

  <Card title="Cost Savings" icon="dollar-sign">
    Reduced processing fees and operational costs compared to traditional card processing systems.
  </Card>

  <Card title="Enhanced Security" icon="shield-alt">
    Advanced security features including tokenization, encryption, and multi-factor authentication.
  </Card>

  <Card title="Global Reach" icon="fa-globe">
    Access to international payment networks and cross-border payment capabilities.
  </Card>
</Cards>

## What's in this API profile?

The Confirmation of Funds API Profile describes the flows and common functionality for the Confirmation of Funds API, which allows a Card Based Payment Instrument Issuer ('CBPII') to:

* Register an intent to confirm funds by creating a "funds confirmation consent" resource with an ASPSP, for agreement between the PSU and ASPSP. This consent is a long lived consent, and contains the length of time (expiration date) the customer (PSU) would like to provide to the CBPII; and
* Subsequently make a request to confirm funds are available.
  Funds can only be confirmed against the currency of the account.
* The Consent model for the Confirmation of Funds API differs to the Payments API and the Account and Transactions API, as the consent is held between the PSU and the ASPSP, rather than between the PSU and the TPP. Whilst the flow follows the same process, the context for each step has a different meaning and is detailed in the text accompanying each API.

<br />

<br />
