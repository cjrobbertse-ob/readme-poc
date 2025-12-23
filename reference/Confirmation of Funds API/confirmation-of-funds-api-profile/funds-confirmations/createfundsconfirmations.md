---
title: Create Funds Confirmation
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

**Step 3: Agree Funds Confirmation Consent**

* The CBPII requests the PSU to agree the consent. The ASPSP may carry this out by using a _redirection flow_ or a _decoupled flow_.
  * In a redirection flow, the CBPII redirects the PSU to the ASPSP.
    * The redirect includes the ConsentId generated in the previous step.
    * This allows the ASPSP to correlate the **funds-confirmation-consent** that was setup.
    * The ASPSP authenticates the PSU.
    * The PSU gives explicit consent to the ASPSP to respond to confirmation of funds requests from the CBPII.
    * The ASPSP updates the state of the **funds-confirmation-consent** resource internally to indicate that the resource has been authorised.
      Once the consent has been authorised, the PSU is redirected back to the CBPII.

* In a decoupled flow, the ASPSP requests the PSU to authorise consent on an _authentication device_ that is separate from the _consumption device_ on which the PSU is interacting with the CBPII.

* The decoupled flow is initiated by the CBPII calling a back-channel authorisation request.

* The request contains a 'hint' that identifies the PSU paired with the consent to be authorised.

* The ASPSP authenticates the PSU.

* The PSU gives explicit consent to the ASPSP to respond to confirmation of funds requests from the CBPII.

* The ASPSP updates the state of the **funds-confirmation-consent**  resource internally to indicate that the resource has been authorised.

Once the consent has been authorised, the ASPSP can make a callback to the PISP to provide an access token.
