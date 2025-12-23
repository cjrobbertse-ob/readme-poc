---
title: Create Funds Confirmation Consent
api:
  file: confirmation-funds-openapi.json
  operationId: CreateFundsConfirmationConsents
hidden: false
---
<NoticeProfileReadInConjunction />

<br />

**Step 1: Agree Funds Confirmation**

This flow begins with a PSU committing to give explicit consent, to their ASPSP to respond to confirmation of funds requests from the CBPII.

**Step 2: Setup Funds Confirmation Consent**

The CBPII connects to the ASPSP that services the PSU's account(s) and creates a funds-confirmation-consent resource. This informs the ASPSP that one of its PSUs would like to grant access to confirm the availability of funds to a CBPII. The ASPSP responds with an identifier for the resource (the ConsentId - which is the intent identifier).

This step is carried out by making a POST request to the /funds-confirmation-consents endpoint, under a client credentials grant.

The setup payload will include these fields:

* Expiration Date Time - an optional expiration for when the CBPII will no longer have access to confirm funds on a PSU's account.
* Debtor Account - mandatory debtor account details to capture the account from which the availability of funds will be confirmed.

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
