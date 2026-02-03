---
title: Create Funds Confirmation Consent
excerpt: >-
  Creates the Consent (between PSU, the ASPSP and the CBPII) that allows the
  CBPII to perform funds availability checks with the PSU's ASPSP.
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

* Expiration Date Time - an optional expiration for when the CBPII will no longer have access to confirm funds on a PSU's account.  If no DateTime is present, the consent will only end if the PSU explicitly cancels it with either the ASPSP or the CBPII.
* Debtor Account - **mandatory** debtor account details to capture the account from which the availability of funds will be confirmed.

<br />