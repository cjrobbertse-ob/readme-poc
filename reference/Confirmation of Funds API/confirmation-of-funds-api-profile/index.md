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
<Cards columns={1}>
  <Card title="Warning" icon="exclamation-triangle">
    This profile should be read in conjunction with a compatible Read/Write Data API Profile which provides a description of the elements that are common across all the Read/Write Data APIs, and compatible individual resources.
  </Card>
</Cards>

The Confirmation of Funds API Profile describes the flows and common functionality for the Confirmation of Funds API, which allows a Card Based Payment Instrument Issuer ('CBPII') to:

* Register an intent to confirm funds by creating a "funds confirmation consent" resource with an ASPSP, for agreement between the PSU and ASPSP. This consent is a long lived consent, and contains the length of time (expiration date) the customer (PSU) would like to provide to the CBPII; and
* Subsequently make a request to confirm funds are available.
  Funds can only be confirmed against the currency of the account.

<Cards columns={1}>
  <Card title="Important Notice" icon="exclamation-triangle">
    This profile should be read in conjunction with a compatible Read/Write Data API Profile which provides a description of the elements that are common across all the Read/Write Data APIs, and compatible individual resources.
  </Card>
</Cards>