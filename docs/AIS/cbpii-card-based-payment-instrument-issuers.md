---
title: CBPII - Card Based Payment Instrument Issuers
excerpt: >-
  Understanding CBPII regulations, virtual cards, and e-wallets under PSD2.
  Learn about confirmation of funds services, authorization requirements, and
  compliance frameworks.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
## Overview

A **Card Based Payment Instrument Issuer (CBPII)** is a regulated payment service provider that issues card-based payment instruments, including virtual cards and e-wallets, which can be linked to customer accounts held at other payment service providers. CBPIIs operate under strict regulatory frameworks to ensure consumer protection and security in digital payments.

## Key Functions

<Cards columns={2}>
  <Card title="Payment Instrument Issuance" icon="credit-card">
    Issue virtual cards, e-wallets, and other card-based payment instruments that can be linked to accounts at different banks or financial institutions.
  </Card>
  <Card title="Confirmation of Funds (CoF)" icon="check-circle">
    Request real-time confirmation from account providers to verify sufficient funds are available before processing transactions.
  </Card>
</Cards>

## How CBPIIs Work

CBPIIs enable customers to use payment instruments that are connected to their existing bank accounts without requiring separate account opening. When a customer initiates a payment using a CBPII-issued instrument:

1. **Transaction Initiation**: Customer uses the virtual card or e-wallet to make a payment
2. **Funds Confirmation**: CBPII requests confirmation of available funds from the account provider
3. **Authorization**: Transaction is authorized based on fund availability and authentication
4. **Processing**: Payment is processed through the appropriate payment networks

## Virtual Cards & E-Wallets

### Virtual Cards

Virtual cards are digital payment instruments that function like traditional payment cards but exist only in digital form. They feature:

- 16-digit PAN (Primary Account Number)
- Expiry date and CVV code
- Integration with major payment networks (Visa, Mastercard, etc.)
- Enhanced security through tokenization

### E-Wallets (Digital Wallets)

E-wallets are virtual accounts that store payment information and enable easy online transfers. Popular examples include:

- Apple Pay
- Google Pay
- Samsung Pay
- PayPal

<Accordion title="Wallet Categories" icon="wallet">
Under PSD3/PSR regulations, wallets are classified into two main categories:

**Pass-Through Wallets (PT Wallets)**
- Act as containers for virtual payment cards
- Facilitate payments without storing funds

**Staged Wallets**
- Store funds directly within the wallet
- Function as payment accounts themselves
</Accordion>

## Regulatory Framework

### Authorization Requirements

CBPIIs must be registered and authorized by their Local Competent Authority as one of the following:

- Payment Initiation Service Provider (PISP)
- Account Information Service Provider (AISP)
- Card Based Payment Instrument Issuer (CBPII)

### PSD2 Compliance

Under the Payment Services Directive 2 (PSD2), CBPIIs must comply with:

<Tabs>
  <Tab title="Strong Customer Authentication">
    Multi-factor authentication requiring at least two of:
    - **Knowledge**: Something the user knows (password, PIN)
    - **Possession**: Something the user has (phone, token)
    - **Inherence**: Something the user is (biometrics)
  </Tab>
  <Tab title="Consumer Protection">
    - Transaction monitoring and fraud prevention
    - Liability protection for unauthorized transactions
    - Transparent fee structures
    - Dispute resolution mechanisms
  </Tab>
  <Tab title="Data Security">
    - Secure API connections
    - Data encryption and protection
    - Regular security assessments
    - Incident reporting requirements
  </Tab>
</Tabs>

## Benefits for Businesses

CBPIIs offer several advantages for businesses looking to modernize their payment infrastructure:

- **Faster Payments**: Instant confirmation of funds availability
- **Enhanced Security**: Multi-factor authentication and tokenization
- **Cost Efficiency**: Reduced processing fees compared to traditional cards
- **Global Reach**: Access to international payment networks
- **Digital Integration**: Seamless integration with e-commerce platforms

## Implementation Considerations

When working with CBPIIs, consider the following:

1. **Regulatory Compliance**: Ensure your CBPII partner is properly authorized
2. **Technical Integration**: Plan for API integration and testing
3. **Customer Experience**: Design smooth authentication flows
4. **Security Measures**: Implement proper tokenization and encryption
5. **Monitoring**: Set up transaction monitoring and reporting systems

## Future Developments

The payment landscape continues to evolve with upcoming regulations like PSD3, which will further define the scope and requirements for digital wallets and virtual payment instruments. CBPIIs will play an increasingly important role in enabling secure, efficient digital payments across various channels and devices.