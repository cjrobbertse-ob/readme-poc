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

A **Card Based Payment Instrument Issuer (CBPII)** is a payment service provider authorised under PSD2 that issues payment instruments — such as virtual cards and e-wallets — linked to customer accounts held at other financial institutions. To verify that a customer's account has sufficient funds before authorising a transaction, the CBPII uses the **Confirmation of Funds (CoF) API** defined in the Open Banking standard.

<Callout icon="👤" theme="info">
**Who is this for?** This profile applies to firms operating as a CBPII under PSD2. In the UK, you need FCA authorisation with the CBPII permission to access this API. ASPSPs (banks and building societies) implement the API endpoints that CBPIIs call.
</Callout>

<Callout icon="⚠️" theme="warning">
**Consent model difference:** Unlike the Account Information and Payment Initiation APIs — where consent is between the PSU and the TPP — the Confirmation of Funds consent is held **between the PSU and the ASPSP**. The CBPII requests the consent, but the agreement is between the customer and their bank. This affects the authorisation flow and how consent is managed.
</Callout>
The diagram below shows the end-to-end flow when a PSU uses a CBPII-issued card backed by a PSD2 in-scope account. Steps 2 and 5 in the [Core Flow](#core-flow) above correspond to the Open Banking API calls; the remaining steps happen outside the API.

![](https://files.readme.io/7e880fd49d256bc7cc4803e06d3d73c1325d4ecdecd9bcbd1bf0d56a62fb5483-image.png)

## What's in this API Profile?

The Confirmation of Funds API Profile describes the flows and common functionality for the CoF API, which allows a CBPII to:

* **Create a funds confirmation consent** — Register an intent to confirm funds by creating a `funds-confirmation-consent` resource with the ASPSP. This is a long-lived consent that contains an optional expiration date set by the PSU.
* **Confirm funds availability** — Make a request to check whether the debtor account holds sufficient funds for a specified amount. Funds can only be confirmed against the currency of the account.

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

