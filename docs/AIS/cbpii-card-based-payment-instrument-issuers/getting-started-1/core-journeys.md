---
title: Core journeys
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

Open Banking API specifications support CoF services for Card Based Payment Instrument Issuers (CBPIIs). These services allow PSUs to provide explicit consent to an ASPSP, so that they can respond to confirmation of funds requests from CBPIIs, limited to a Y/N. CBPIIs can subsequently submit confirmation of funds requests to the ASPSP provided that the PSU has also provided their explicit consent to the CBPII and has initiated a payment transaction with the payment instrument for the amount in question.

This section describes how each of the Participants (CBPIIs and ASPSPs) in the delivery of these services can optimise the customer experience for these. Furthermore, it provides some clarifications to these Participants on the usage of the APIs, which are not covered by the technical specifications and some best practice guidelines for implementation of the customer journeys.

Please note that the consent given to ASPSPs and CBPIIs can be “until further notice” and does not expire after 90 days. Thus, authentication does not need to occur after the initial set up for the specific CBPII has been completed. The consent to CBPIIs access will generally be ongoing or setup for a set period of time, after which PSUs will need to renew it.
