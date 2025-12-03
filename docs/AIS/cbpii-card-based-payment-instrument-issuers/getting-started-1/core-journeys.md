---
title: Core Journeys
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

Open Banking API specifications support CoF services for Card Based Payment Instrument Issuers (CBPIIs). These services allow PSUs to provide explicit consent to an ASPSP, so that they can respond to confirmation of funds requests from CBPIIs, limited to a Y/N. CBPIIs can subsequently submit confirmation of funds requests to the ASPSP provided that the PSU has also provided their explicit consent to the CBPII and has initiated a payment transaction with the payment instrument for the amount in question.

This section describes how each of the Participants (CBPIIs and ASPSPs) in the delivery of these services can optimise the customer experience for these. Furthermore, it provides some clarifications to these Participants on the usage of the APIs, which are not covered by the technical specifications and some best practice guidelines for implementation of the customer journeys.

Please note that the consent given to ASPSPs and CBPIIs can be “until further notice” and does not expire after 90 days. Thus, authentication does not need to occur after the initial set up for the specific CBPII has been completed. The consent to CBPIIs access will generally be ongoing or setup for a set period of time, after which PSUs will need to renew it.

<br />

<br />

<br />

<Image border={false} src="https://files.readme.io/af45fa87b42ded80dc610d141d7350400121a31f4d0e5f9229595887ea3df41d-image.png" />

<Cards columns={4}>
  <Card title="First Card" href="https://readme.com" icon="fa-home" target="_blank">
    Regulation 68(3)(a) of the PSRs, requires that the CBPIIs must have the explicit consent of the PSU prior to making Confirmation of Funds requests to the PSUs ASPSPs.
  </Card>

  <Card title="Second Card" icon="fa-user">
    *Lorem ipsum dolor sit amet, consectetur adipiscing elit*
  </Card>

  <Card title="Third Card" icon="fa-star">
    > Ut enim ad minim veniam, quis nostrud ullamco
  </Card>

  <Card title="Fourth Card" icon="fa-question">
    **Excepteur sint occaecat cupidatat non proident**
  </Card>
</Cards>
