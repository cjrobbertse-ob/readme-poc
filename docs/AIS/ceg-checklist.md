---
title: CEG Checklist
deprecated: false
hidden: false
metadata:
  robots: index
---
Check your customer journeys against the CEG requirements for your participant role.

1. Review the **General** checks and the relevant service areas: **AIS**, **PIS**, and **CBPII**.
2. Within each topic, review the checks for your participant role.
3. Compare your journey with the **Expected answer**, including any exceptions, and consult the references below each table.

The **Expected answer** and **OBL requirement** columns retain their separate meanings: a check labelled Required may still specify that an answer _should_ be Yes.&#x20;

## General

### Authentication

| Ref. | Participant | Checklist question                                                                                                                                                                | Expected answer                                                  | OBL requirement |
| ---- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- | --------------- |
| 1    | ASPSP       | Is your OB authentication journey equivalent to the journey experienced by a PSU when authenticating directly within your existing online channel (e.g. browser and app)?         | Must be **Yes**                                                  | Required        |
| 2    | ASPSP       | At any point during the OB customer journey, do you ask the PSU for consent for the TPP to access account information or initiate a payment?                                      | Must be **No**                                                   | Required        |
| 3    | ASPSP       | Can a PSU identify your firm as genuine and legitimate within the authentication journey?                                                                                         | Should be **Yes**                                                | Recommended     |
| 4    | ASPSP       | Can a PSU authenticate using all channels (e.g. browser, app) offered by the ASPSP for authentication, irrespective of the channel via which the TPP is presenting their service? | Should be **Yes**                                                | Required        |
| 4b   | ASPSP       | Do you ensure that your journey does not include any steps, language or features that could constitute an obstacle?                                                               | Should be **Yes**                                                | Required        |
| 5a   | ASPSP       | Do you support app-to-app redirection?                                                                                                                                            | Must be **Yes** for CMA9, and should be **Yes** for other ASPSPs | Required        |
| 5b   | TPP         | If your proposition includes a mobile app, do you support app-to-app redirection?                                                                                                 | Should be **Yes**                                                | Recommended     |
| 6    | ASPSP       | Do you support Decoupled authentication?                                                                                                                                          | Could be **Yes**                                                 | Recommended     |
| 6a   | ASPSP       | Do you support Redirection authentication?                                                                                                                                        | Must be **Yes**                                                  | Required        |

**Regulatory references**

- **1:** CMA: Trustee P3/P4 letter Actions P3 A2 and P3 A6; EBA: Final Guideline 5.2(a); FCA Approach Document: 17.130, 17.134, 17.136.
- **2:** EBA: Opinion paragraph 13; EBA: Final Guideline 5.2(c) and 5.2(d); RTS: Art. 32(3); FCA Approach Document: 17.57.
- **3:** OBL: Consumer priorities.
- **4:** EBA: Final Guideline 5.1(b) and 5.2(a); EBA: Opinion paragraph 50; FCA Approach Document: 17.130, 17.134, 17.136.
- **4b:** EBA: Final Guideline 5.1(b); RTS: Art. 32(3); FCA Approach Document: 17.120–17.122; 17.128.
- **5a:** EBA: Final Guideline 5.1(b) and 5.2(a); EBA: Opinion paragraph 50; CMA Order: Trustee P3/P4 letter Action P3 A6; FCA Approach Document: 17.130, 17.134, 17.136.
- **6:** EBA: Opinion paragraph 50; CMA Order: Trustee P3/P4 letter Action P4 A2; EBA: Final Guideline 5.1.
- **6a:** EBA: Opinion paragraph 50; CMA Order: Trustee P3/P4 letter Action P4 A2; EBA: Final Guideline 5.1.

### Product and service set up

| Ref. | Participant | Checklist question                                                                                                                                                                                          | Expected answer   | OBL requirement |
| ---- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- | --------------- |
| 5c   | TPP         | Do you adhere to the 5 OB Customer Experience Principles (Trust, Control, Security, Speed, Transparency)?                                                                                                   | Should be **Yes** | Recommended     |
| 5d   | TPP         | Where you onward share data to firms outside the PSD2 perimeter, do you explain this clearly and transparently, including the purpose, the names of firms data will be shared with and what data is shared? | Should be **Yes** | Recommended     |
| 5e   | TPP         | Are your materials and processes inclusive and designed to cater for all customers including those with vulnerabilities?                                                                                    | Should be **Yes** | Recommended     |

**Regulatory references**

- **5e:** FCA: FG21/1.

### Error codes

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 7 | ASPSP | Do you provide error codes to the TPP as per the error codes specified in the Read/Write Data API Specification v3.1.2 for failed requests? | Must be **Yes** | Required |

**Regulatory references**

- **7:** RTS: Art. 36(2); EBA: Opinion Table 1.

### Consent

| Ref. | Participant | Checklist question                                                                                                                                                                                                                                                                                                                                                                   | Expected answer | OBL requirement |
| ---- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------- | --------------- |
| 8    | TPP         | Do you gather consent in a clear, specific and straightforward manner as per the principles described in Sections Account Information Consent (AIS), Single Domestic Payments – a/c selection @ PISP (PIS) and Consent for Confirmation of Funds (CoF) (CBPII) of the Customer Experience Guidelines?                                                                                | Must be **Yes** | Required        |
| 8a   | PISP        | Do you gather consent in a clear, specific and straightforward manner as per the principles described in Section – Payment Refunds of the Customer Experience Guidelines?                                                                                                                                                                                                            | Must be **Yes** | Required        |
| 8b   | PISP        | Do you gather consent in a clear, specific and straightforward manner and ensure that all the standardised set of consent parameters (if applicable) are clearly displayed to the PSU as per the principles described in Sections VRP Payments with delegated SCA, VRP Payments with an SCA exemption, and VRP Payments under sweeping access of the Customer Experience Guidelines? | Must be **Yes** | Required        |
| 8c   | PISP        | Do you make Terms available in a clear, specific and straightforward manner to the PSU before taking consent as per the principles described in Sections VRP Payments with delegated SCA, VRP Payments with an SCA exemption, and VRP Payments under sweeping access of the Customer Experience Guidelines?                                                                          | Must be **Yes** | Required        |
| 8d   | TPP         | Do you display TPP Trading name/brand name (i.e. Client Name) clearly to the PSU while taking consent and on the consent dashboard?                                                                                                                                                                                                                                                  | Must be **Yes** | Required        |
| 8e   | AISP        | Do you display the Agent company name if the customer facing entity is an Agent acting on behalf of the AISP and do you ensure that the Consent Dashboard is easy and intuitive to find and use when a PSU is using one of your agents (as per Section Consent Dashboards When Using an Agent of an AISP)?                                                                           | Must be **Yes** | Required        |
| 8f   | PISP        | Do you also display the customer facing service provider name and the PISP Trading name if they are different entities? Do you add the customer facing service provider name in the 'on behalf of' field of software statement only if it is different than the PISP Trading name?                                                                                                   | Must be **Yes** | Required        |
| 8j   | CBPII       | Do you display the Agent company name if the customer facing entity is an Agent acting on behalf of the CBPII and do you ensure that the Consent Dashboard is easy and intuitive to find and use when a PSU is using one of your agents (as per Section Consent Dashboards When Using an Agent of an AISP)?                                                                          | Must be **Yes** | Required        |

**Regulatory references**

- **8:** PSRs: Reg. 68(3)(a), 69(2) and 70(3)(a); FCA Approach Document: 17.52, 17.54, 17.55.
- **8a:** PSRs: Reg. 69(3)(g), 69(3)(c); FCA Approach Document: 17.67.
- **8b:** PSRs: Reg. 68(3)(a), 69(2) and 70(3)(a); FCA Approach Document: 17.52, 17.54, 17.55.
- **8c:** OBL: Roadmap item A10 & A2 b(i).
- **8e:** FCA: PERG Q25A.
- **8f:** OBL: Roadmap item A10 & A2 b(i).
- **8j:** FCA: PERG Q25A.

### Consent dashboard

| Ref. | Participant | Checklist question                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Expected answer   | OBL requirement |
| ---- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- | --------------- |
| 8g   | TPP         | When PSUs leave a product or service and revoke their consent for the payment service, do you provide them with information which clearly outlines the consequences of revocation, including what happens to any data you may hold?                                                                                                                                                                                                                                                                            | Should be **Yes** | Recommended     |
| 8h   | TPP         | Do you display TPP Trading name/brand name (i.e. Client Name) clearly to the PSU while taking consent and on the consent dashboard?                                                                                                                                                                                                                                                                                                                                                                            | Must be **Yes**   | Required        |
| 8i   | AISP        | Do you display the Agent company name if the customer facing entity is an Agent acting on behalf of the AISP and do you ensure that the Consent Dashboard is easy and intuitive to find and use when a PSU is using one of your agents (as per Section Consent Dashboards When Using an Agent of an AISP)?                                                                                                                                                                                                     | Must be **Yes**   | Required        |
| 8k   | CBPII       | Do you display the Agent company name if the customer facing entity is an Agent acting on behalf of the CBPII and do you ensure that the Consent Dashboard is easy and intuitive to find and use when a PSU is using one of your agents (as per Section Consent Dashboards When Using an Agent of an AISP)?                                                                                                                                                                                                    | Must be **Yes**   | Required        |
| 8l   | PISP        | Do you also display the customer facing service provider name and the PISP Trading name if they are different entities? Do you add the customer facing service provider name in the 'on behalf of' field of software statement only if it is different than the PISP Trading name?                                                                                                                                                                                                                             | Must be **Yes**   | Required        |
| 9a   | TPP         | Do you refer to your dashboard as "open banking connections" or "open banking connected accounts" and do you provide clear instructions on the location and purpose of the consent dashboard?                                                                                                                                                                                                                                                                                                                  | Must be **Yes**   | Required        |
| 9b   | TPP         | Can a PSU view their on-going consent in a Consent Dashboard on all channels which is easy and intuitive for PSUs to find and use (as per Sections AIS Consent Dashboards and Revocation, CBPII Consent Dashboard and Revocation, Variable Recurring Payments (VRP) Consent Dashboard and Revocation)?                                                                                                                                                                                                         | Must be **Yes**   | Required        |
| 9c   | TPP         | Do you make available a consent dashboard which allows PSUs to revoke access which has been previously granted without obstruction (as per Sections AIS Consent Dashboards and Revocation, CBPII Consent Dashboard and Revocation, Variable Recurring Payments (VRP) Consent Dashboard and Revocation)? After revocation, do you make a call to DELETE the consent resource as soon as practically possible (as described in Version 3 of the API specifications) to ensure that no new data can be retrieved? | Must be **Yes**   | Required        |
| 9d   | TPP         | Does your consent dashboard give PSUs sufficient information to enable them to make informed decisions, including clear status flags as per Sections AIS Consent Dashboards and Revocation, CBPII Consent Dashboard and Revocation, Variable Recurring Payments (VRP) Consent Dashboard and Revocation?                                                                                                                                                                                                        | Must be **Yes**   | Required        |
| 9e   | TPP         | Do you provide a list of old connections for the PSU, including consents that have been revoked or have expired or accesses that have been revoked (as per Sections AIS Consent Dashboards and Revocation, CBPII Consent Dashboard and Revocation, Variable Recurring Payments (VRP) Consent Dashboard and Revocation)?                                                                                                                                                                                        | Must be **Yes**   | Required        |
| 9f   | TPP         | Does your consent management tool make it clear to your customers if any data is being onward shared, the purpose for that sharing and how to manage or cancel that onward sharing?                                                                                                                                                                                                                                                                                                                            | Should be **Yes** | Recommended     |

**Regulatory references**

- **8i:** FCA: PERG Q25A.
- **8k:** FCA: PERG Q25A.
- **8l:** OBL: Roadmap item A10 & A2 b(i).
- **9b:** OBL: P2 and P15 of Agreed Arrangements.
- **9c:** OBL: P2 and P15 of Agreed Arrangements.
- **9f:** CMA Order: Trustee action A14 from A2021/4.

## AIS

### Access dashboard

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 10a | ASPSP | Do you refer to your dashboard as "open banking connections" or "open banking connected services" or "connections"? | Must be **Yes** | Required |
| 10b | ASPSP | Do you make available on all channels an access dashboard which allows PSUs to view long-lived access which has been granted and is it easy and intuitive for PSUs to find and use (as per Section AIS Access Dashboard & Revocation, PIS Variable Recurring Payments (VRP) Access Dashboard and Revocation and / or CBPII Access Dashboard and Revocation)? | Must be **Yes** | Required |
| 10c | ASPSP | Do you make available an access dashboard which allows PSUs to revoke access which has been previously granted (as per Section AIS Access Dashboard & Revocation, PIS Variable Recurring Payments (VRP) Access Dashboard and Revocation and / or CBPII Access Dashboard and Revocation)? | Must be **Yes** | Required |
| 10d | ASPSP | Does your access dashboard give PSUs sufficient information to enable them to make informed decisions, including clear status flags (as per Section AIS Access Dashboard & Revocation, PIS Variable Recurring Payments (VRP) Access Dashboard and Revocation and / or CBPII Access Dashboard and Revocation)? | Must be **Yes** | Required |
| 10e | ASPSP | Do you provide a list of old connections for the PSU, including consents that have been cancelled or have expired or accesses that have been revoked (as per Section AIS Access Dashboard & Revocation, PIS Variable Recurring Payments (VRP) Access Dashboard and Revocation and / or CBPII Access Dashboard and Revocation)? | Must be **Yes** | Required |
| 10f | ASPSP | Do you confirm to the PSU that the access has been cancelled and advise the PSU to contact their associated AISP or PISP or CBPII to inform them of the cancellation of access and/or understand the consequences of doing so? | Must be **Yes** | Required |
| 10g | ASPSP | Do you mark the status of the consent resource as Cancelled when PSU has revoked access on the ASPSP access dashboard? | Must be **Yes** | Required |
| 10h | ASPSP | Do you mark the status of the consent resource as Expired when the consent has passed consent validity date? | Must be **Yes** | Required |

**Regulatory references**

- **10a:** CMA Order: Trustee action 1 from A2021/4. Original accompanying note: For "connections" it is CR by CMA9 which got approved by Trustee.
- **10b:** OBL: P2 and P15 of Agreed Arrangements; OBL: Roadmap item A10.
- **10c:** OBL: P2 and P15 of Agreed Arrangements.
- **10d:** CMA Order: Trustee action A1 from A2021/4.
- **10e:** CMA Order: Trustee action A1 from A2021/4.
- **10f:** CMA Order: Trustee action A1 from A2021/4.
- **10g:** PSRs: Regulation 71(7) and (8); EBA: Q and A 2018-4309; RTS: Article 30(1)(c) and 36(2).
- **10h:** PSRs: Article 67; RTS: Article 30(1)(c) and 36(2).

### Complaints

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 11 | ASPSP | Do you provide an easy way for the PSU to understand the complaints and dispute resolution process? | Must be **Yes** | Required |
| 11a | TPP | Do you provide an easy way for the PSU to understand the complaints and dispute resolution process? | Must be **Yes** | Required |

**Regulatory references**

- **11:** PSRs: Reg. 101.
- **11a:** PSRs: Reg. 101.

### Consent

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 12 | AISP | Do you make it clear when the consent to access account information will expire (including if it is one-off access or ongoing access)? | Must be **Yes** | Required |

**Regulatory references**

- **12:** FCA Approach Document: 17.52, 17.66.

### Data clusters

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 13a | ASPSP | Do you use the OBL language shown under the Customer Experience Guidelines Section Permissions & Data Cluster to describe the data clusters when communicating with the PSU? | Must be **Yes** | Required |
| 13b | AISP | Do you use the OBL language shown under the Customer Experience Guidelines Section Permissions & Data Cluster to describe the data clusters when communicating with the PSU and ensure to only request the data necessary for the provision of your account information service to the PSU? | Must be **Yes** | Required |

**Regulatory references**

- **13a:** CMA Order: 10.2.
- **13b:** PSRs: Reg. 70(3)(f).

### Functionality

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 14 | ASPSP | Do you provide access to all account information made available to the PSU through your existing online channel(s), irrespective of the channel through which the TPP is presenting their service to the PSU? | Must be **Yes** | Required |
| 15 | ASPSP | Do you apply the same access control rules to joint and multi-signatory accounts when accessed through a TPP as are applied when these accounts are accessed directly by the PSU? | Must be **Yes** | Required |

**Regulatory references**

- **14:** RTS: Art. 36(1)(a); EBA: Opinion paragraphs 18 and 20; FCA Approach Document: 17.32.
- **15:** RTS: Art. 36(1)(a); EBA: Opinion paragraphs 18 and 20; FCA Approach Document: 17.31.

### Authenticating to access

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 16 | TPP | Do you notify the PSU when reauthentication is required at the ASPSP? | Should be **Yes** | Recommended |
| 17 | ASPSP | When a PSU is authenticating to refresh AISP access without making any changes to the original consent request, does your journey include any steps or screens other than those required for authentication of the PSU, for example, re-selection of the account(s) to which access was originally granted? | Must be **No** | Required |
| 17c | ASPSP | Following the initial application of SCA, do you apply the UK-RTS, Article 10A exemption, unless there are permitted circumstances? | Must be **Yes** | Required |

**Regulatory references**

- **16:** FCA Approach Document: 17.82; FCA: PS 21/19 page 15.
- **17:** RTS: Art. 32(3); EBA: Final Guideline 5.1(b) and 5.2(c).
- **17c:** RTS: Art. 10A; FCA Approach Document: 20.47, 20.48.

### Reconfirm consent at AISP

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 16a | AISP | Do you notify the PSU when reconfirmation of consent is required for a single/multiple consent(s) across ASPSPs? | Must be **Yes** | Required |
| 16b | AISP | Do you provide the customer the details of the data permissions (cluster) to enable them to make an informed decision? | Must be **Yes** | Required |
| 16c | AISP | Do you stop accessing the data if the customer has not reconfirmed their consent within 90 days, following the previous reconfirmation? | Must be **Yes** | Required |
| 16d | AISP | Do you ensure that the PSU is given sufficient information to reconfirm consent including whether any other parties would have access to their information and which payment accounts will be accessed and give them clear choice to explicitly reconfirm their consent or stop the service? | Must be **Yes** | Required |

**Regulatory references**

- **16a:** FCA Approach Document: 17.77.
- **16b:** RTS: Art. 36(6); FCA Approach Document: 17.77.
- **16c:** RTS: Art. 36(6); FCA Approach Document: 17.78.
- **16d:** RTS: Art. 36(6); FCA Approach Document: 17.77.

### Authenticating to refresh access

**Source review needed:** The original checklist contains two entries with reference **17b** and identical questions, but different citation lists. Both entries and their original IDs are retained below. “First occurrence” and “second occurrence” distinguish their citations; they are not new checklist IDs.

| Ref. | Participant | Checklist question                                                                                                                                                                                                                            | Expected answer | OBL requirement |
| ---- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | --------------- |
| 17a  | AISP        | Do you allow the PSU to confirm their request to refresh access across multiple ASPSPs account(s)? When refreshing access across multiple ASPSPs, do you enable the PSU to select and confirm the relevant accounts(s) for refreshing access? | Must be **Yes** | Required        |
| 17b  | AISP        | Do you apply SCA when the PSU confirms their selection of account(s) across the relevant ASPSPs account(s)?                                                                                                                                   | Must be **Yes** | Required        |
| 17d  | ASPSP       | Do you mark the status of the consent resource as Authorised when PSU has reauthenticated to refresh access without making any changes to the original consent request?                                                                       | Must be **Yes** | Required        |

**Regulatory references**

- **17a:** RTS: Art. 10.
- **17b — second occurrence:** EBA: Opinion paper 13 June 2018 38–39. FCA Approach Document: 20.25..
- **17d:** PSRs: Regulation 71(7) and (8).

### Completion

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 18 | AISP | Do you provide confirmation of a successful account information data request following each PSU authentication? | Must be **Yes**; e.g. through a receipt or confirmation within TPP domain | Required |
| 18a | AISP | Upon successful completion of SCA, do you confirm to the PSU that access has been refreshed? | Must be **Yes** | Required |

## PIS

### Consent parameters

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 19a | ASPSP | Do you display all the VRP consent parameter(s) to the PSU which the PISP has provided? | Must be **Yes** | Required |
| 19c | PISP | Do you display all the VRP consent parameter(s) to the PSU which the PISP has provided? | Must be **Yes** | Required |
| 28e | ASPSP | Do you support all periodic limits and are you capable of handling multiple limits in a single consent (as shown under Sections VRP Payments with delegated SCA, VRP Payments with an SCA exemption, and VRP Payments under sweeping access of the Customer Experience Guidelines)? | Must be **Yes** | Required |

**Regulatory references**

- **19a:** OBL: Roadmap item A10 & A2 b(i).
- **19c:** OBL: Roadmap item A10 & A2 b(i).
- **28e:** OBL: Roadmap item A10.

### Delegated SCA

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 19b | PISP | Do you apply SCA when the PSU confirms the VRP payment? | Must be **Yes** | Required |

**Regulatory references**

- **19b:** OBL: Roadmap item A10 & A2 b(i).

### Functionality

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 19 | ASPSP | For payments that do not require the display of supplementary information (as defined in the Customer Experience Guidelines Single Domestic Payments – a/c Selection @ PISP (Supplementary Info)), does your journey involve any further steps (as defined in the Customer Experience Guidelines Single Domestic Payments – a/c selection @ PISP) or screens following authentication? | Must be **No** | Required |
| 20 | ASPSP | Do you provide supplementary information where it is required, in an equivalent way, to direct interactions with PSUs? | Must be **Yes** | Required |
| 21 | ASPSP | Can a PSU using a PISP utilise all PIS functionality offered by the ASPSP to the PSU in their online channel, irrespective of the channel or method used for authentication? | Must be **Yes** | Required |
| 22 | PISP | Do you capture the minimum set of parameters required for the payment instruction to be completed for each payment type? | Must be **Yes**; minimum set of parameters are defined in Section 4 of the Customer Experience Guidelines | Required |
| 22a | PISP | Do you capture any standardised set of consent parameters required for the variable recurring payments to be completed for each payment type? | Must be **Yes**; minimum set of parameters are defined in Section VRP Domestic Payments – a/c selection @PISP of the Customer Experience Guidelines | Required |
| 22b | PISP | Do you capture the set of consent parameters required for sweeping payments to be completed for each payment type? | Must be **Yes**; set of parameters are defined in Section Sweeping Domestic Payments – a/c selection @PISP of the Customer Experience Guidelines | Required |
| 23 | ASPSP | In cases where the payment instruction is incomplete because the account details have not been provided by the PSU to the PISP, do you allow the PSU to select the account from which they wish to make the payment? | Must be **Yes** | Required |
| 24 | PISP | Do you offer the PSU at least one of the available options for selecting the payment account during the payment initiation as defined in the Customer Experience Guidelines Section Payment Initiation Services (PIS)? | Must be **Yes**; see the account-selection options below | Required |
| 28f | ASPSP | Do you support the minimum and maximum payment limits made via PISP in line with direct online channels for each of the different payment types (e.g. Faster payments, CHAPS etc.)? | Must be **Yes** | Required |

**Account-selection options for check 24**

The available options for selecting an account are defined in Section 4 as:

- Enter their Account Identification details directly to the PISP.
- Select their Account Identification details at the PISP (this assumes they have been saved previously).
- Select their ASPSP in order to select their account from within the ASPSP’s domain later in the journey.

**Regulatory references**

- **19:** CMA Order: Trustee P3/P4 letter Action P3 A2; RTS: Art. 32(3); EBA: Final Guideline 5.1(b) and 5.2(c).
- **20:** EBA: Final Guideline 5.1(b) and 5.2(c).
- **21:** EBA: Final Guidelines 5.1; PSRs: Reg. 69(2)(c); FCA Approach Document: 17.35–17.38, 17.136.
- **22:** RTS: Art. 36(4).
- **22a:** OBL: Roadmap item A10 & A2 b(i); RTS: Art. 36(4).
- **22b:** OBL: Roadmap item A10 & A2 b(i); RTS: Art. 36(4).
- **23:** FCA Approach Document: 17.143.
- **28f:** PSRs: Reg. 69(2)(c); FCA Approach Document: 17.38.

### Status of payment

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 25 | ASPSP | Do you provide or make available all information regarding initiation and execution of the payment to the PISP immediately after receipt of the payment order? | Must be **Yes** | Required |
| 26 | PISP | Do you display all the required information to the PSU immediately after the initiation of the payment order? | Must be **Yes**; types of information are defined in Section 4.1 | Required |
| 27 | PISP | After receiving the initial payment status information, do you follow up with the ASPSP in order to get the latest status of the payment and inform the PSU accordingly? | Should be **Yes** | Recommended |

**Regulatory references**

- **25:** PSRs: Reg. 69(2)(b); RTS: Art. 36(1)(b); FCA Approach Document: 17.27–17.29.
- **26:** PSRs: Reg. 44(1).

### Status of VRP consent setup

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 26a | PISP | Do you display all the required information to the PSU immediately after the VRP Consent setup with the ASPSP? | Must be **Yes** | Required |

**Regulatory references**

- **26a:** OBL: Roadmap item A10 & A2 b(i).

### Display of payment details

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 28 | ASPSP | Do you make the PSU aware of the amount/currency/payee as part of the authentication journey? | Must be **Yes**, unless an SCA exemption is being applied | Required |
| 28a | ASPSP | Do you make the PSU aware of all the consent parameters associated with the variable recurring payment access, as part of the authentication journey? | Must be **Yes** | Required |

**Regulatory references**

- **28:** RTS: Art. 5(1)(a).
- **28a:** OBL: Roadmap item A10 & A2 b(i).

### Trusted Beneficiary setup

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 28b | ASPSP | During the authentication journey, do you inform the PSU that the payee will be added to their list of payees and also add to the PSU's List of Payees? | Must be **Yes** | Required |

**Regulatory references**

- **28b:** OBL: Roadmap item A10 & A2 b(i).

### Trusted Beneficiary application

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 28c | ASPSP | When the PISP initiates a Sweeping payment within the Sweeping consent parameters, do you apply the Trusted Beneficiary SCA exemption? | Must be **Yes** | Required |

**Regulatory references**

- **28c:** OBL: Roadmap item A10.

### Reject payment & response

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 28d | ASPSP | Do you reject Sweeping/VRP payment and provide an appropriate response to the PISP if the Sweeping/VRP payment is outside consent parameters, or the Sweeping/VRP Consent setup is revoked by the PSU at the ASPSP? | Must be **Yes** | Required |

**Regulatory references**

- **28d:** OBL: Roadmap item A10.

### Confirmation of funds ("yes/no" response)

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 29a | ASPSP | Do you provide immediate confirmation of whether or not there are funds available at the PISP’s request, in a ‘yes or no’ format? | Must be **Yes** | Required |
| 29b | ASPSP | If you cannot perform a funds check then do you provide PISPs the necessary data to allow them to make their own judgements on the sufficient availability of funds? | Must be **Yes** | Required |

**Regulatory references**

- **29a:** RTS: Art. 36(1)(c); EBA: Opinion paragraph 22; FCA Approach Document: 17.23, 17.24.
- **29b:** RTS: Art. 36(1)(c); EBA: Opinion paragraph 22; FCA Approach Document: 17.25.

### Future dated payments & standing orders

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 30 | PISP | Do you inform the PSU that amendment or cancellation of standing orders and future dated payments must be performed directly with their ASPSP? | Must be **Yes** | Required |

## CBPII

### Consent

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 31 | ASPSP | Do you, prior to receiving the first request from each CBPII, obtain explicit consent from the PSU to provide confirmation of funds in response to CBPII requests (as shown under the Customer Experience Guidelines Section Card Based Payment Instrument Issuers (CBPIIs))? | Must be **Yes** | Required |
| 32 | CBPII | Do you obtain explicit consent from the customer to request the confirmation of funds? | Must be **Yes**; minimum set of parameters are defined in Section 5 of the Customer Experience Guidelines | Required |

**Regulatory references**

- **31:** PSRs: Reg. 68(5)(b); FCA Approach Document: 17.18.
- **32:** PSRs: Reg. 68(3)(a); FCA Approach Document: 17.52, 17.54.

### Functionality

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 33 | CBPII | Do you only request confirmation of funds when the PSU has initiated a payment transaction for the amount in question using the card based instrument? | Must be **Yes** | Required |

**Regulatory references**

- **33:** PSRs: Reg. 68(3)(b).

### Confirmation of funds ("yes/no" response)

| Ref. | Participant | Checklist question | Expected answer | OBL requirement |
| --- | --- | --- | --- | --- |
| 34 | ASPSP | Do you provide immediate confirmation of whether or not there are funds available at the CBPII's request, in a ‘yes’ or ‘no’ format? | Must be **Yes** | Required |

**Regulatory references**

- **34:** PSRs: Reg. 68(4); RTS: Art. 36(1)(c); EBA: Opinion paragraph 22; FCA Approach Document: 17.21, 17.22.
