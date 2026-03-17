---
title: CBPII - Card Based Payment Instrument Issuers
excerpt: >-
  Understanding CBPII services, virtual cards, and e-wallets. Learn about
  payment instrument issuance, confirmation of funds, and modern digital payment
  solutions.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
next:
  description: >-
    Read on to understand exactly how the Open Banking standards support
    confirmation of funds for CBPIIs
  pages:
    - slug: getting-started-1
      title: Getting started
      type: basic
---
## Overview

A **Card Based Payment Instrument Issuer (CBPII)** is a specialized payment service provider that issues modern payment instruments, including virtual cards and e-wallets, which can be linked to customer accounts held at different financial institutions. CBPIIs enable seamless digital payments while providing enhanced security and convenience.

## Confirmation of Funds API

The Confirmation of Funds (CoF) API is the Open Banking interface that CBPIIs use to check whether a customer's account has sufficient funds before authorising a transaction. The API uses a **consent-based model** — the customer must first authorise the CBPII to query their account, and then the CBPII can make repeated funds checks against that consent.

The API returns a **boolean response** (`FundsAvailable: true` or `false`) for a specified amount and currency. Funds can only be confirmed against the currency of the account.

### Core Flow

1. **PSU gives consent** — The customer (PSU) agrees to let the ASPSP respond to funds confirmation requests from the CBPII.
2. **CBPII creates consent** — `POST /funds-confirmation-consents` with the debtor account and an optional expiration date. Uses a client credentials grant.
3. **PSU authorises** — The customer authorises the consent via a redirect (Authorization Code Grant) or decoupled flow (CIBA).
4. **Customer initiates payment** — The customer uses their virtual card or e-wallet to make a purchase (outside the scope of the CoF API).
5. **CBPII checks funds** — `POST /funds-confirmations` with the consent ID, a reference, and the instructed amount. The ASPSP responds with `FundsAvailable: true/false`.
6. **CBPII monitors consent** — `GET /funds-confirmation-consents/{ConsentId}` to check the consent status at any time.

<Accordion title="API Endpoints" icon="code">

| Method | Endpoint | Description | Grant Type |
|--------|----------|-------------|------------|
| `POST` | `/funds-confirmation-consents` | Create a funds confirmation consent | Client Credentials |
| `GET` | `/funds-confirmation-consents/{ConsentId}` | Retrieve a consent | Client Credentials |
| `DELETE` | `/funds-confirmation-consents/{ConsentId}` | Delete a consent | Client Credentials |
| `POST` | `/funds-confirmations` | Check funds availability | Authorization Code |

All endpoints use the `fundsconfirmations` scope. None require message signing or an idempotency key.

</Accordion>

<Accordion title="Consent Lifecycle" icon="rotate">

Consents are **long-lived** — if no `ExpirationDateTime` is set, the consent remains valid indefinitely. The consent moves through these statuses:

| Status | Code | Description |
|--------|------|-------------|
| Awaiting Authorisation | `AWAU` | Created by the CBPII, waiting for PSU to authorise |
| Authorised | `AUTH` | PSU has authorised the consent — funds checks can proceed |
| Rejected | `RJCT` | Consent was rejected |
| Cancelled | `CANC` | Consent was revoked by the PSU or deleted by the CBPII |
| Expired | `EXPD` | Consent has passed its expiration date |

A PSU can revoke consent at any time through the ASPSP's banking interface. If revoked via the CBPII, the CBPII must call `DELETE` on the consent resource and cease API access.

</Accordion>

## How CBPIIs Work

CBPIIs enable customers to use payment instruments such as virtual cards and e-wallets that are connected to their existing bank accounts without requiring separate account opening. The process is streamlined for better user experience:

1. **Transaction Initiation**: Customer uses the virtual card or e-wallet to make a payment.
2. **Funds Confirmation**: CBPII requests confirmation of available funds from the account provider.   **This is the capability that utilises Open Banking standards.**

<Callout icon="🏦" theme="info">
Step 2 — Funds Confirmation — is the capability that utilises Open Banking standards. The CBPII queries the customer's account provider to verify sufficient funds before authorising the transaction.
</Callout>

3. **Authorization**: Transaction is authorized based on fund availability and authentication.
4. **Processing**: Payment is processed through the appropriate payment networks.

## Use Cases

<Tabs>
  <Tab title="Consumer Applications">

  * **E-commerce Integration**: One-click payments for online shopping.
  * **Mobile Payments**: In-app purchases and contactless transactions.
  * **Subscription Management**: Recurring payment handling with enhanced security.

  </Tab>
  <Tab title="Corporate Payments">

  * **Virtual Corporate Cards**: Streamlined expense management and procurement.
  * **B2B Transactions**: Secure business-to-business payment processing.
  * **Travel & Entertainment**: Dynamic spending controls and real-time approvals.

  </Tab>
  <Tab title="Financial Services">

  * **Embedded Finance**: Payment capabilities integrated into non-financial platforms.
  * **Marketplace Payments**: Multi-party transaction facilitation.
  * **Cross-Border Transfers**: International payment processing with competitive rates.

  </Tab>
</Tabs>

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

  <Card title="Global Reach" icon="globe">
    Access to international payment networks and cross-border payment capabilities.
  </Card>
</Cards>