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
    - slug: getting-started
      title: Getting Started
      type: basic
---
## Overview

A **Card Based Payment Instrument Issuer (CBPII)** is a specialized payment service provider that issues modern payment instruments, including virtual cards and e-wallets, which can be linked to customer accounts held at different financial institutions. CBPIIs enable seamless digital payments while providing enhanced security and convenience.

## How CBPIIs Work

CBPIIs enable customers to use payment instruments such as virtual cards and e-wallets that are connected to their existing bank accounts without requiring separate account opening. The process is streamlined for better user experience:

1. **Transaction Initiation**: Customer uses the virtual card or e-wallet to make a payment.
2. **Funds Confirmation**: CBPII requests confirmation of available funds from the account provider.   **This is the capability that utilises Open Banking standards.**
3. **Authorization**: Transaction is authorized based on fund availability and authentication.
4. **Processing**: Payment is processed through the appropriate payment networks.

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

  <Card title="Global Reach" icon="globe">
    Access to international payment networks and cross-border payment capabilities.
  </Card>
</Cards>