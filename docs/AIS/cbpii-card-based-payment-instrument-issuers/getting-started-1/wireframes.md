---
title: Wireframes
excerpt: >-
  Customer Experience Guidelines that set out requirements and  best practice;
  key points listed below
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

<Accordion title="1 - Minimum Set of Parameters">
  CBPIIs **must** allow PSUs to enter their payment Account Identification details in at least one of the ways specified in the OBL V3 Read/Write API Specifications (e.g. account number and sort code – with additional roll number if required, IBAN, PAN, Paym and other formats).

  **Note 1:** In some of the above cases, CBPIIs **may** also need PSUs to provide their ASPSP name so that CBPIIs can check whether ASPSPs will be able to match the account identifier to the underlying PSU payment account.

  CBPIIs **could** also choose to allow PSUs to enter their payment account name.

  **Note 2:** The use of IBAN as an identification of the payer account for UK ASPSPs is not expected to be heavily used as account and sortcode are the main account identifiers used in the UK. IBAN however will be used by non UK ASPSPs implementing OBL standards and offering their services in the UK.

  <br />
</Accordion>

<Accordion title="2 - PSU Consent to CBPII">
  CBPIIs **must** provide PSUs with sufficient information to enable them to make an informed decision about whether to consent to the CBPII making CoF requests to their ASPSP accounts. For example, the CBPII should provide details on the purpose for which the funds checks will be used (including whether any other parties will have access to the information) and clear and reassuring messages about what information will be made available from the ASPSPs. This should include information such as the following:

  Prior to making Confirmation of funds requests to their ASPSPs, CBPIIs **must** have been given explicit consent by PSUs.

  CBPIIs will **only** received a ‘yes/no’ answer about the availability of funds at PSU's account, sufficient to cover a specific amount of a CBPII transaction.

  The Confirmation of Funds Response **will not** be stored by CBPIIs.

  Confirmation received by CBPIIs **cannot** be used for any other purpose than the execution of the transaction for which the request is made.

  The period over which CoF consent is requested and the reasons why.

  How PSUs will be able to revoke their consent through the CBPII environment.
</Accordion>

<Accordion title="3 - PSU Consent to CBPII">
  CBPIIs **must** request for the PSU's consent to in a clear and specific manner. CBPIIs **must** display the following information in the consent screen:

  **Note 1:** if PSU payment Account identification is selected in item 1, CBPIIs **should** mask the PSU payment Account details on the consent screen. Otherwise, if the PSU payment Account identification has been input by PSUs in item #1, CBPIIs **should not** mask these details to allow PSUs to check and verify correctness.PSU payment Account Identification and/or the selected ASPSP (based on item 1 options).

  **Note 2:** if PSU payment Account identification is provided by PSUs in item #1, CBPIIs **could** use this to identify and display the ASPSP without having to ask PSUs.

  Expiration Date & Time: Consent **could** be on-going or for set period of time. If this parameter is provided by CBPIIs, the consent will have limited life span and will expire on the specified date. CBPIIs **could** choose to align this expiry date with the expiration date of the card based instrument issued to PSUs. Alternatively, they **could** choose a different period for security or business reasons, or they **could** also allow PSUs to select their desired expiry date explaining however the implications this may have on the usage of their issued card.
  PSU payment Account name, if provided by PSUs in item 1.
</Accordion>

<Accordion title="4 - Generic CBPII to ASPSP redirection Screen and message">
  Please refer to Section Effective use of redirection screens.**We will need to link this when we add the other pages**
</Accordion>

<Accordion title="5 - Authentication">
  ASPSPs **must** apply SCA. The ASPSP authentication **must** have no more than the number of steps that the PSU would experience when directly authenticating via the ASPSP channel.
</Accordion>

<Accordion title="6 - Authentication">
  ASPSPs **could** display a message to prompt PSUs to authenticate to continue with setting up Funds Check.
</Accordion>

<Accordion title="7 - ASPSP Consent">
  Prior to receiving the first request from each CBPII, ASPSPs **must** obtain explicit consent from the PSU to provide confirmation of funds to CBPII requests.

  ASPSPs **must** be able to introduce an additional screen to display Information associated with the Confirmation of Funds consent. ASPSPs **must** display to PSUs all the information related to the CoF consent. This information includes the following:

  * CBPII requesting CoF to the PSU account.
  * PSU payment Account Name.
  * PSU payment Account Identification.
    * Consent Expiration Date & Time: (this could also be on-going).

  **Note:** PSU’s payment account details **may** be shown in account number and sort-code format in cases when PSU in item 1 provided account identification details in other formats such as a PAN, IBAN, Paym mobile number, etc., subject to CBPII and ASPSPs offering these options.
</Accordion>

<Accordion title="8 - ASPSP Supplementary Information">
  ASPSPs **should** provide some supplementary information in relation to their obligations for CoF requests and how these will be handled. This **may** include but not limited to the following:

  * ASPSPs will **only** respond with a ‘yes/no’ answer about the availability of funds at the PSUs’ account, sufficient to cover a specific amount of a CBPII transaction.
  * ASPSPs **are not permitted** to provide additional account information (such as the account balance) or block funds on the PSU’s account for the CBPII transaction.
  * PSUs **may** be able to view their history of Confirmation of Funds requests including the identity of CBPIIs which made CoF requests and the provided response, using their Access Dashboard at their ASPSPs.
  * How PSUs will be able to revoke their consent from the ASPSP Access Dashboard.
</Accordion>

<Accordion title="9 - PSU Review">
  ASPSPs **should** allow PSUs to review, as a part of the authentication process, all the information related to the CoF. PSUs can either proceed with the CoF consent or cancel it, on the same screen with items 7 & 8, using ‘equal weight’ options.
</Accordion>

<Accordion title="10 - Generic ASPSP to CBPII redirection screen and message">
  Please refer to Section Effective use of redirection screens.**We will need to link this when we add the other pages**
</Accordion>

<Accordion title="11 - CBPII Confirmation">
  CBPIIs **should** confirm to PSUs the successful completion of the Confirmation of Funds account access request. CBPIIs **could** also choose to display again:

  The PSU payment account identification details (this can now be in masked form).
  The expiration date of the Confirmation of Funds consent.
</Accordion>

<br />

CEG Checklist

<br />

| Topic                                     | Participant Type | Question                                                                                                                                                         | Notes                                                                                                              | OBL Requirement | CMA Order | PSD2/RTS/FCA AD | Regulatory Reference                                                                           |
| :---------------------------------------- | :--------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------- | :-------------- | :-------- | :-------------- | :--------------------------------------------------------------------------------------------- |
| Explicit consent                          | ASPSP            | Do you, prior to receiving the 1st request from each CBPII, obtain explicit consent from the PSU to provide confirmation of funds in response to CBPII requests? | Answer must be "Yes"                                                                                               | Required        | N/A       | Mandatory       | PSRs Reg. 68(5)(b)               FCA Approach Document 17.18                                   |
| Explicit consent                          | CBPII            | Do you obtain explicit consent from the customer to request the confirmation of funds?                                                                           | Answer must be "Yes”  Minimum set of parameters are defined in the Section 5 of the Customer Experience Guidelines | Required        | N/A       | Mandatory       | PSRs Reg. 68(3)(a)  FCA Approach Document 17.52,17.54                                          |
| Functionality                             | CBPII            | Do you only request confirmation of funds when the PSU has initiated a payment transaction for the amount in question using the card based instrument?           | Answer must be "Yes"                                                                                               | Required        | N/A       | Mandatory       | PSRs Reg. 68(3)(b)                                                                             |
| Confirmation of funds ("yes/no" response) | ASPSP            | Do you provide immediate confirmation of funds in the form of a ‘yes’ or ‘no’ answer to a CBPII request where the payment account is accessible online?          | Answer must be "Yes"                                                                                               | Required        | N/A       | Mandatory       | PSRs Reg. 68(4) RTS Art. 36(1)(c) EBA Opinion paragraph 22  FCA Approach Document 17.21, 17.22 |

| Topic | Participant Type | Question | Notes | OBL Requirement | CMA Order | PSD2/RTS/FCA AD | Regulatory Reference |
| :---- | :--------------- | :------- | :---- | :-------------- | :-------- | :-------------- | :------------------- |
|       |                  |          |       |                 |           |                 |                      |
|       |                  |          |       |                 |           |                 |                      |

<br />

<br />
