---
title: Create Funds Confirmation
excerpt: >-
  This explains how the CBPII performs an individual funds availability check
  with the ASPSP.
api:
  file: confirmation-funds-openapi.json
  operationId: CreateFundsConfirmations
hidden: false
---
<br />

**Step 4: Initiate Card Payment**

A card payment is initiated by the PSU (directly or indirectly). This process is outside the scope of the Confirmation of Funds API.

**Step 5: Confirm Funds**

The CBPII connects to the ASPSP that services the PSU's account(s) and creates a **funds-confirmation resource**. This informs the ASPSP that the CBPII would like to confirm funds are available in the specific payment account.
The ASPSP responds with a yes/no (boolean) for the resource.

This step is carried out by making a **POST** request to the /funds-confirmations endpoint, under an authorization code grant.

The setup payload will include these fields - which describe the data that the PSU has consented with the CBPII:
Amount - the amount to be confirmed available.

ConsentId - an ID that relates the request to a **funds-confirmation-consent**, and specific account with the ASPSP. This ID must match the intent identifier.

**Step 6: Get Funds Confirmation Consent Status**

The CBPII may check the status of the **funds-confirmation-consent** resource (with the ConsentId).

This step is carried out by making a **GET** request to the /funds-confirmation-consents endpoint, under a client credentials grant.

<br />