---
title: Get Funds Confirmation Consent
api:
  file: confirmation-funds-openapi.json
  operationId: GetFundsConfirmationConsentsConsentId
hidden: false
---
<br />

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
