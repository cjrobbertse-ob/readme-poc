---
title: Core Journeys
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: Review the wireframes for inspiration & guidance
  pages:
    - slug: wireframes
      title: Wireframes
      type: basic
---
<br />

Open Banking API specifications support CoF services for Card Based Payment Instrument Issuers (CBPIIs). These services allow PSUs to provide explicit consent to an ASPSP, so that they can respond to confirmation of funds requests from CBPIIs, limited to a Y/N. CBPIIs can subsequently submit confirmation of funds requests to the ASPSP provided that the PSU has also provided their explicit consent to the CBPII and has initiated a payment transaction with the payment instrument for the amount in question.

This section describes how each of the Participants (CBPIIs and ASPSPs) in the delivery of these services can optimise the customer experience for these. Furthermore, it provides some clarifications to these Participants on the usage of the APIs, which are not covered by the technical specifications and some best practice guidelines for implementation of the customer journeys.

<Demo />

<br />

<br />

<br />

<Image border={false} src="https://files.readme.io/af45fa87b42ded80dc610d141d7350400121a31f4d0e5f9229595887ea3df41d-image.png" />

<Cards columns={3}>
  <Card title="Note:" href="https://readme.com" icon="fa-info" target="_blank">
    The above journey illustrates the consent given by PSUs for CoF purposes.
  </Card>

  <Card title="Regulatory Driver" icon="fa-book">
    Regulation 68(3)(a) of the PSRs, requires that the CBPIIs must have the explicit consent of the PSU prior to making Confirmation of Funds requests to the PSUs ASPSPs.
  </Card>

  <Card title="Regulatory Driver" icon="fa-book">
    Regulation 68(5)(b) of the PSRs requires that the ASPSPs must have the explicit consent of the PSU prior to responding to the first CBPII Confirmation of Funds request. This applies to each specific CBPII and each PSU payment account, that is accessible online.
  </Card>
</Cards>