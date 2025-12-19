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
---
A **Card Based Payment Instrument Issuer (CBPII)** is a specialized payment service provider that issues modern payment instruments, including virtual cards and e-wallets, which can be linked to customer accounts held at different financial institutions. CBPIIs enable seamless digital payments while providing enhanced security and convenience.

The Confirmation of Funds API Profile describes the flows and common functionality for the Confirmation of Funds API, which allows a Card Based Payment Instrument Issuer ('CBPII') to:

* Register an intent to confirm funds by creating a "funds confirmation consent" resource with an ASPSP, for agreement between the PSU and ASPSP. This consent is a long lived consent, and contains the length of time (expiration date) the customer (PSU) would like to provide to the CBPII; and
* Subsequently make a request to confirm funds are available.
  Funds can only be confirmed against the currency of the account.

<NoticeProfileReadInConjunction />

<br />
