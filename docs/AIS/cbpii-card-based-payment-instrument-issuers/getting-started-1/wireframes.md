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
<Image align="center" border={false} src="https://files.readme.io/3af7c73bd1f01496cd5f11bacfa9f7ac9653ad60487e993149a4f84905bcc91f-Z-5.1.1.-Consent-For-Confirmation-Of-Funds.png" />

<br />

<Accordion title="1 - Minimum Set of Parameters">
  CBPIIs must allow PSUs to enter their payment Account Identification details in at least one of the ways specified in the OBL V3 Read/Write API Specifications (e.g. account number and sort code – with additional roll number if required, IBAN, PAN, Paym and other formats).

  **Note 1:** In some of the above cases, CBPIIs may also need PSUs to provide their ASPSP name so that CBPIIs can check whether ASPSPs will be able to match the account identifier to the underlying PSU payment account.

  CBPIIs could also choose to allow PSUs to enter their payment account name.

  **Note 2:** The use of IBAN as an identification of the payer account for UK ASPSPs is not expected to be heavily used as account and sortcode are the main account identifiers used in the UK. IBAN however will be used by non UK ASPSPs implementing OBL standards and offering their services in the UK.

  <br />
</Accordion>

<Accordion title="2 - PSU Consent to CBPII">
  CBPIIs must provide PSUs sufficient information to enable them to make an informed decision about whether to consent to the CBPII making CoF requests to their ASPSP accounts. For example, the CBPII should provide details on the purpose for which the funds checks will be used (including whether any other parties will have access to the information) and clear and reassuring messages about what information will be made available from the ASPSPs. This should include information such as the following:

  Prior to making Confirmation of funds requests to their ASPSPs, CBPIIs must have been given explicit consent by PSUs.

  CBPIIs will only received a ‘yes/no’ answer about the availability of funds at PSUs’ account, sufficient to cover a specific amount of a CBPII transaction.

  The Confirmation of Funds Response will not be stored by CBPIIs.

  Confirmation received by CBPIIs cannot be used for any other purpose than the execution of the transaction for which the request is made.

  The period over which CoF consent is requested and the reasons why.

  How PSUs will be able to revoke their consent through the CBPII environment.
</Accordion>

<Accordion title="3 - PSU Consent to CBPII">
  CBPIIs must request for the PSUs’ consent to in a clear and specific manner. CBPIIs must display the following information in the consent screen:

  **Note 1:** if PSU payment Account identification is selected in item 1, CBPIIs should mask the PSU payment Account details on the consent screen. Otherwise, if the PSU payment Account identification has been input by PSUs in item #1, CBPIIs should not mask these details to allow PSUs to check and verify correctness.PSU payment Account Identification and/or the selected ASPSP (based on item 1 options).

  **Note 2:** if PSU payment Account identification is provided by PSUs in item #1, CBPIIs could use this to identify and display the ASPSP without having to ask PSUs.

  Expiration Date & Time: Consent could be on-going or for set period of time. If this parameter is provided by CBPIIs, the consent will have limited life span and will expire on the specified date. CBPIIs could choose to align this expiry date with the expiration date of the card based instrument issued to PSUs. Alternatively, they could choose a different period for security or business reasons, or they could also allow PSUs to select their desired expiry date explaining however the implications this may have on the usage of their issued card.
  PSU payment Account name, if provided by PSUs in item 1.
</Accordion>

<Accordion title="4 - Generic CBPII to ASPSP redirection Screen and message">
  Please refer to Section Effective use of redirection screens.**We will need to link this when we add the other pages**
</Accordion>

<Accordion title="5 - Authentication">
  ASPSPs must apply SCA. The ASPSP authentication must have no more than the number of steps that the PSU would experience when directly authenticating via the ASPSP channel.
</Accordion>

<Accordion title="6 - Authentication">
  ASPSPs could display a message to prompt PSUs to authenticate to continue with setting up Funds Check.
</Accordion>

<Accordion title="7 - ASPSP Consent">
  Prior to receiving the first request from each CBPII, ASPSPs must obtain explicit consent from the PSU to provide confirmation of funds to CBPII requests.

  ASPSPs must be able to introduce an additional screen to display Information associated with the Confirmation of Funds consent. ASPSPs must display to PSUs all the information related to the CoF consent. This information includes the following:

  * CBPII requesting CoF to the PSU account.
  * PSU payment Account Name.
  * PSU payment Account Identification.
    * Consent Expiration Date & Time: (this could also be on-going).

  **Note:** PSU’s payment account details may be shown in account number and sort-code format in cases when PSU in item 1 provided account identification details in other formats such as a PAN, IBAN, Paym mobile number, etc., subject to CBPII and ASPSPs offering these options.
</Accordion>

<Accordion title="8 - ASPSP Supplementary Information">
  ASPSPs should provide some supplementary information in relation to their obligations for CoF requests and how these will be handled. This may include but not limited to the following:

  * ASPSPs will only respond with a ‘yes/no’ answer about the availability of funds at the PSUs’ account, sufficient to cover a specific amount of a CBPII transaction.
  * ASPSPs are not permitted to provide additional account information (such as the account balance) or block funds on the PSU’s account for the CBPII transaction.
  * PSUs may be able to view their history of Confirmation of Funds requests including the identity of CBPIIs which made CoF requests and the provided response, using their Access Dashboard at their ASPSPs.
  * How PSUs will be able to revoke their consent from the ASPSP Access Dashboard.
</Accordion>

<Accordion title="9 - PSU Review">
  ASPSPs should allow PSUs to review, as a part of the authentication process, all the information related to the CoF. PSUs can either proceed with the CoF consent or cancel it, on the same screen with items 7 & 8, using ‘equal weight’ options.
</Accordion>

<Accordion title="10 - Generic ASPSP to CBPII redirection screen and message">
  Please refer to Section Effective use of redirection screens.**We will need to link this when we add the other pages**
</Accordion>

<Accordion title="11 - CBPII Confirmation">
  CBPIIs should confirm to PSUs the successful completion of the Confirmation of Funds account access request. CBPIIs could also choose to display again:

  The PSU payment account identification details (this can now be in masked form).
  The expiration date of the Confirmation of Funds consent.
</Accordion>

<br />

<br />

<br />

Reference	Topic	Participant (TPP, ASPSP, PISP, AISP, CBPII)	Checklist question	Notes	Open Banking Implementation Requirements	CMA Order 	PSD2 / RTS / FCA AD	New Regulatory reference(s) as of [DATE]
General
1	Authentication	ASPSP	Is your Open Banking authentication journey  authentication journey equivalent to the journey experienced by a PSU when authenticating directly within your existing online channel (e.g. browser and app?)	Answer must be "Yes"	Required	Mandatory	Mandatory	"Trustee P3/P4 letter Actions P3 A2 and P3 A6
EBA Final Guideline 5.2 (a)  
FCA Approach Document 17.130,17.134, 17.136"
2	Authentication	ASPSP	At any point during the Open Banking customer journey, do you ask the PSU for consent for the TPP to access account information or initiate a payment?	Answer must be “No"	Required	Mandatory	Mandatory	"EBA Opinion paragraph 13
EBA Final Guideline 5.2(c) and 5.2(d)
RTS Art. 32(3)  
FCA Approach Document 17.57"
3	Authentication	ASPSP	Can a PSU identify your firm as genuine and legitimate within the authentication journey?	Answer should be "Yes"	Recommended	n/a	n/a	Consumer priorities
4	Authentication	ASPSP	Can a PSU authenticate using all channels (e.g. browser, app) offered by the ASPSP for authentication, irrespective of the channel via which the TPP is presenting their service?	Answer should be "Yes"	Required	n/a	Conditional 	"EBA Final  Guideline 5.1(b) and 5.2(a)
EBA Opinion paragraph 50  
FCA Approach Document 17.130,17.134, 17.136"
4b	Authentication	ASPSP	Do you ensure that your journey does not include any steps, langauge or features that could constitute as an obstacle?	Answer should be "Yes"	Required	Mandatory	Mandatory	"EBA Final  Guideline 5.1(b)
RTS Art.32(3)  
FCA Approach Document 17.120-17.122;17.128"
5a	Authentication	ASPSP	Do you support app-to-app redirection?	Answer must be "Yes“ for CMA9, and should be “Yes” for other ASPSPS	Required	Mandatory	Conditional	"EBA Final Guideline 5.1(b) and 5.2(a)
EBA Opinion paragraph 50
Trustee P3/P4 letter Action P3 A6FCA Approach Document 17.130,17.134, 17.136"
5b	Authentication	TPP	If your proposition includes a mobile app, do you support app-to-app redirection? 	Answer should be "Yes"	Recommended	n/a	n/a
5c	Product and Service Set Up	TPP	Do you adhere to the 5 Open Banking Customer Experience Principles (Trust, Control, Security, Speed, Transparency)	Answer should be "Yes"	Recommended	n/a	n/a
5d	Product and Service Set Up	TPP	Where you onward share data to firms outside the PSD2 perimeter do you expain this clearly and transparantly, including the purpose, the names of firms data will be shared with and what data is shared? 	Answer should be "Yes"	Recommended	n/a	n/a
5e	Product and Service Set Up	TPP	Are your materials and processes inclusive and designed to cater for all customers including those with vulnerabilites?	Answer should be "Yes"	Recommended	n/a	n/a	FCA FG21/1
6	Authentication	ASPSP	Do you support Decoupled authentication?	Answer could be "Yes"	Recommended	n/a	Conditional	"EBA Opinion paragraph 50
Trustee P3/P4 letter Action P4 A2
EBA Final Guideline 5.1"
7	Error codes	ASPSP	Do you provide error codes to the TPP as per the error codes specified in the Read/Write Data API Specification v3.1.2 for failed requests?	Answer must be "Yes"	Required	Mandatory	Mandatory	"RTS Art. 36(2)
EBA Opinion Table 1"
8	Consent 	TPP	"Do you gather consent in a clear, specific and straightforward manner as per the principles described in Sections
Account Information Consent (AIS),
Single Domestic Payments – a/c selection @ PISP (PIS) and
Consent for Confirmation of Funds (CoF) (CBPII)
of the Customer Experience Guidelines? "	Answer must be "Yes"	Required	n/a	Mandatory	PSRs Reg. 68(3)(a), 69(2) and 70(3)(a)                                                   FCA Approach Document 17.52, 17.54, 17.55  
8a	Consent	PISP	Do you gather consent in a clear, specific and straightforward manner as per the principles described in Section - Payment Refunds of the Customer Experience Guidelines?	Answer must be "Yes"	Required	n/a	Mandatory	"PSRs Reg. 69(3)(g), 69(3)(c)  
FCA Approach Document 17.67"
8b	Consent 	PISP	"Do you gather consent in a clear, specific and straightforward manner and ensure that all the standardised set of consent parameters (if applicable) are clearly displayed to the PSU as per the principles described in Sections

* VRP Payments with delegated SCA
* VRP Paymentss with an SCA exemption
* VRP Payments under sweeping access
  of the Customer Experience Guidelines? "	Answer must be "Yes"	Required	n/a	Mandatory	PSRs Reg. 68(3)(a), 69(2) and 70(3)(a)                                                             FCA Approach Document 17.52, 17.54, 17.55
  8c	Consent 	PISP	"Do you make Terms available in a clear, specific and straightforward manner to the PSU before taking consent as per the principles described in Sections
* VRP Payments with delegated SCA
* VRP Paymentss with an SCA exemption
* VRP Payments under sweeping access
  of the Customer Experience Guidelines? "	Answer must be "Yes"	Customer-Required	n/a	n/a	Roadmap item A10 & A2 b(i)
  8d	Consent & Consent Dashboard	TPP	Do you display TPP Trading name/brand name (i.e. Client Name) clearly to the PSU while taking consent and on the consent dashboard?	Answer must be "Yes"	Required	n/a	Mandatory
  8e	Consent & Consent Dashboard	AISP, CBPII	"Do you display the Agent company name if the customer facing entity is a Agent acting on behalf of the AISP and do you ensure that the Consent Dashboard is easy and intuitive to find and use when a PSU is using one of your agents (as per Section Consent Dashboards When Using an Agent of an AISP)?
  "	Answer must be "Yes"	Required	n/a	Mandatory	FCA PERG Q25A
  8f	Consent & Consent Dashboard	PISP	"Do you also display the customer facing service provider name and the PISP Trading name if they are different entities?
  Do you add the customer facing service provider name in the 'on behalf of' field of software statement only if it is different than the PISP Trading name?"	Answer must be "Yes"	Required	n/a	Mandatory	Roadmap item A10 & A2 b(i)
  8g	"Consent Dashboard
  Leaving a Product or Service"	TPP	When PSU's revoke their consent for the payment service, do you provide  them with information which  clearly outlines the consequences of revocation, including what happens to any data you may hold?	Answer should be "Yes"	Recommended	n/a	n/a
  9a	Consent dashboard	TPP	Do you refer to your dashboard as "open banking connections" or "open banking connected accounts" and do you provide clear instructions on the location and purpose of the consent dashboard?	Answer must be "Yes"	Recommended	n/a	n/a
  9b	Consent dashboard	TPP	"Can a PSU view their on-going consent in a Consent Dashboard on all channels which is easy and intuitive for PSUs to find and use (as per Sections AIS Consent Dashboards and Revocation, CBPII Consent Dashboard and Revocation, Variable Recurring Payments (VRP) Consent Dashboard and Revocation)?
  "	Answer must be "Yes"	Required	n/a	n/a	•P2 and P15 of Agreed Arrangements
  9c	Consent dashboard	TPP	"Do you make available a consent dashboard which allows PSUs to revoke access which has been previously granted without obstruction (as per Sections AIS Consent Dashboards and Revocation, CBPII Consent Dashboard and Revocation, Variable Recurring Payments (VRP) Consent Dashboard and Revocation)?
  After revocation, do you make a call to DELETE the consent resource as soon as practically possible (as described in Version 3 of the API specifications) to ensure that no new data can be retrieved?"	Answer must be "Yes"	Required	Mandatory	n/a	•P2 and P15 of Agreed Arrangements
  9d	Consent dashboard	TPP	Does your consent dashboard give PSUs sufficient information to enable them to make informed decisions, including clear status flags as per Sections AIS Consent Dashboards and Revocation, CBPII Consent Dashboard and Revocation, Variable Recurring Payments (VRP) Consent Dashboard and Revocation)?	Answer must be "Yes"	Recommended	n/a	n/a
  9e	Consent dashboard	TPP	Do you provide a list of old connections for the PSU, including consents that have been revoked or have expired or accesses that have been revoked (as per Sections AIS Consent Dashboards and Revocation, CBPII Consent Dashboard and Revocation, Variable Recurring Payments (VRP) Consent Dashboard and Revocation)?	Answer must be "Yes"	Recommended	n/a	n/a
  9f	Consent dashboard	TPP	Does your consent management tool make it clear to your customers if any data is being onward shared, the purpose for that sharing and how to manage or cancel that onward sharing?  	Answer should be "Yes"	Recommended	n/a	n/a	•Trustee action A14 from A2021/4
  Account Information Services
  10a	Access dashboard	ASPSP	Do you refer to your dashboard as "open banking connections" or "open banking connected services" or "connections"?	Answer must be "Yes"	Required	Mandatory	n/a	"Trustee action 1 from A2021/4
  For ""connections"" it is CR by CMA9 which got approved by Trustee"
  10b	Access dashboard	ASPSP	Do you make available on all channels an access dashboard which allows PSUs to view long-lived access which has been granted and is it easy and intuitive for PSUs to find and use (as per Section AIS Access Dashboard & Revocation, PIS Variable Recurring Payments (VRP) Access Dashboard and Revocation and / or CBPII Access Dashboard and Revocation)? 	Answer must be "Yes"	Required	Mandatory	n/a	"P2 and P15 of Agreed Arrangements
  Roadmap item A10   "
  10c	Access dashboard	ASPSP	Do you make available an access dashboard which allows PSUs to revoke access which has been previously granted (as per Section AIS Access Dashboard & Revocation, PIS Variable Recurring Payments (VRP) Access Dashboard and Revocation and / or CBPII Access Dashboard and Revocation)?	Answer must be "Yes"	Required	Mandatory	n/a	"P2 and P15 of Agreed Arrangements
  "
  10d	Access dashboard	ASPSP	Does your access dashboard give PSU's sufficient information to enable them to make informed decisions, including clear status flags (as per Section AIS Access Dashboard & Revocation, PIS Variable Recurring Payments (VRP) Access Dashboard and Revocation and / or CBPII Access Dashboard and Revocation)?	Answer must be "Yes"	Required	Mandatory	n/a	Trustee action A1 from A2021/4
  10e	Access dashboard	ASPSP	Do you provide a list of old connections for the PSU, including consents that have been cancelled or have expired or accesses that have been revoked (as per Section AIS Access Dashboard & Revocation, PIS Variable Recurring Payments (VRP) Access Dashboard and Revocation and / or CBPII Access Dashboard and Revocation)? 	Answer must be "Yes"	Required	Mandatory	n/a	Trustee action A1 from A2021/4
  10f	Access dashboard	ASPSP	"Do you confirm to the PSU that the access has been cancelled and advise the PSU to contact their associated AISP or PISP or CBPII to inform them of the cancellation of access and/or understand the consequences of doing so?
  "	Answer must be "Yes"	Required	Mandatory	n/a	Trustee action A1 from A2021/4
  10g	Access dashboard	ASPSP	Do you mark the status of the consent resource as Cancelled when PSU has revoked access on the ASPSP access dashboard?	Answer must be "Yes"	Recommended	Conditional	Conditional	"Regulation 71(7) and (8) PSRs,
  EBA Q and A  2018-4309,
  Article 30(1)( c) and 36(2) FCA's SCA-RTS"
  10h	Access dashboard	ASPSP	Do you mark the status of the consent resource as Expired when the consent has passed consent validity date?	Answer must be "Yes"	Recommended	Conditional	Conditional	"Regulation 67 Payment Services Regulations 2017,
  Article 30(1)(c) and 36(2) FCA's SCA-RTS."
  11	Complaints	TPP, ASPSP	Do you provide an easy way for the PSU to understand the complaints and dispute resolution process? 	Answer must be "Yes"	Required	n/a	Mandatory	•PSRs Reg. 101
  12	Consent	AISP	Do you make it clear when the consent to access account information will expire (including if it is one-off access or ongoing access)?	Answer must be "Yes"	Required	n/a	Mandatory	•FCA Approach Document 17.52,17.66
  13a	Data clusters	ASPSP	Do you use the OBL language shown under the Customer Experience Guidelines Section Permissions & Data Cluster to describe the data clusters when communicating with the PSU?	Answer must be "Yes"	Required	Mandatory	n/a	CMA Order 10.2
  13b	Data clusters	AISP	Do you use the OBL language shown under the Customer Experience Guidelines Section Permissions & Data Cluster to describe the data clusters when communicating with the PSU and ensure to only request the data necessary for the provision of your account information service to the PSU?	Answer must be "Yes"	Required	n/a	Mandatory	•PSRs, Reg. 70(3)(f)
  14	Functionality	 ASPSP	Do you provide access to all account information made available to the PSU through your existing online channel(s), irrespective of the channel through which the TPP is presenting their service to the PSU?	Answer must be "Yes"	Required	Mandatory	Mandatory	"RTS Art. 36(1)(a)
  EBA Opinion paragraphs 18 and 20  
  FCA Approach Document 17.32"
  15	Functionality	ASPSP	Do you apply the same access control rules to joint and multi-signatory accounts when accessed through a TPP as are applied when these accounts are accessed directly by the PSU?	Answer must be "Yes"	Required	n/a	Mandatory	"RTS Art. 36(1)(a)
  EBA Opinion paragraphs 18 and 20  
  FCA Approach Document 17.31"
  16	Authenticating to access	TPP	Do you notify the PSU when reauthentication is required at the ASPSP?	"Answer should be ""Yes""
  "	Recommended	n/a	n/a	FCA Approach Document 17.82; FCA PS 21/19 page 15
  16a	Reconfirm consent at AISP	AISP	Do you notify the PSU when reconfirmation of consent is required for a single/multiple consent(s) across ASPSPs?	Answer must be "Yes"	Required	n/a	Mandatory	FCA Approach Document 17.77
  16b	Reconfirm consent at AISP	AISP	Do you provide the customer the details of the data permissions (cluster) to enable them to make an informed decision?	Answer must be "Yes"	Required	n/a	Mandatory	RTS. Art 36(6)                                                                                                FCA Approach Document 17.77
  16c	Reconfirm consent at AISP	AISP	Do you stop accessing the data if the customer has not reconfirmed their consent within 90 days, following the previous reconfirmation? 	Answer must be "Yes"	Required	n/a	Mandatory	RTS Art. 36(6)                                                                                              FCA Approach Document 17.78
  16d	Reconfirm consent at AISP	AISP	Do you ensure that the PSU is given sufficient information to reconfirm consent including whether any other parties would have access to their information and which payment accounts will be accessed and give them clear choice to explicitly reconfirm their consent or stop the service?	Answer must be "Yes"	Required	n/a	n/a	RTS, Art 36(6)                                                                                                FCA Approach Document 17.77
  17	Authenticating to access	ASPSP	When a PSU is authenticating to refresh AISP access without making any changes to the original consent request, does your journey include any steps or screens other than those required for authentication of the PSU, for example, re-selection of the account(s) to which access was originally granted?	Answer must be "No"	Required	n/a	Mandatory	"RTS Art 32(3)
  EBA Final Guideline 5.1(b) and 5.2(c)"
  17b	Authenticating to refresh access	AISP	Do you apply SCA when the PSU confirms their selection of account(s) across the relevant ASPSPs account(s)?	Answer must be "Yes"	Required	n/a	n/a	EBA opinion paper – 13th June 2018 38-39                                                 FCA Approach Document 20.25
  17a	Authenticating to refresh access	EU AISP	"Do you allow the PSU to confirm their request to refresh access across multiple ASPSPs account(s)?
  When refreshing access across multiple ASPSPs, do you enable the PSU to select and confirm the relevant accounts(s) for refreshing access?"	Answer must be "Yes"	Customer-Required	n/a	n/a	EU RTS Art.10
  17b	Authenticating to refresh access	EU AISP	Do you apply SCA when the PSU confirms their selection of account(s) across the relevant ASPSPs account(s)?	Answer must be "Yes"	Required	n/a	n/a	EBA opinion paper – 13th June 2018 38-39
  17c	Authenticate to access	ASPSP	Following the initial application of SCA, do you apply the UK- RTS, Article 10A exemption, unless there are permitted circumstances?	Answer must be "Yes"	Recommended	n/a	Conditional	UK-RTS, Article 10A; FCA Approach Document 20.47,20.48
  17d	Authenticating to refresh access	ASPSP	Do you mark the status of the consent resource as Authorised when PSU has reauthenticated to refresh access without making any changes to the original consent request?	Answer must be "Yes"	Recommended	Conditional	Conditional	Regulation 71(7) and (8) Payment Services Regulations 2017
  18	Completion	AISP	Do you provide confirmation of a successful account information data request following each PSU authentication?	"Answer must be ""Yes""
  e.g. through a receipt or confirmation within TPP domain"	Required	n/a	n/a
  18a	Completion	AISP	Upon successful completion of SCA, do you confirm to the PSU  that access has been refreshed?	Answer must be "Yes"	Required	n/a	n/a
  Payment Initiation Services
  19a	Consent parameters	PISP & ASPSP	Do you display all the VRP consent parameter(s)  to the PSU which the PISP has provided?	Answer must be "Yes"	Required	n/a	Conditional	Roadmap item A10 & A2 b(i)
  19b	Delegated SCA	PISP	Do you apply SCA when the PSU confirms the VRP payment?	Answer must be "Yes"	Required	n/a	n/a	Roadmap item A10 & A2 b(i)  
  19	Functionality	ASPSP	For payments that do not require the display of supplementary information (as defined in the Customer Experience Guidelines Single Domestic Payments – a/c Selection @ PISP (Supplementary Info) does your journey involve any further steps (as defined in the Customer Experience Guidelines Single Domestic Payments – a/c selection @ PISP ) or screens following authentication?	Answer must be "No"	Required	Mandatory	Mandatory	"Trustee P3/P4 letter Action P3 A2
  RTS Art. 32(3)
  EBA Final Guideline 5.1(b) and 5.2(c)"
  20	Functionality	ASPSP	Do you provide supplementary information where it is required, in an equivalent way, to direct interactions with PSUs?	Answer must be "Yes"	Required	n/a	Mandatory	EBA Final Guideline 5.1(b) and 5.2(c)
  21	Functionality	ASPSP	Can a PSU using a PISP utilise all PIS functionality offered by the ASPSP to the PSU in their online channel, irrespective of the channel or method used for authentication?	Answer must be "Yes"	Required	Mandatory	Mandatory	"EBA Final Guidelines 5.1
  PSRs Reg. 69(2)(c)  
  FCA Approach Document 17.35-17.38, 17.136"
  22	Functionality	PISP	Do you capture the minimum set of parameters required for the payment instruction to be completed for each payment type? 	"Answer must be ""Yes""
  Minimum set of parameters are defined in the Section 4 of the Customer Experience Guidelines"	Required	n/a	Mandatory	•RTS Art. 36(4)
  22a	Functionality	PISP	Do you capture any standardised set of consent parameters required for the variable recurring payments to be completed for each payment type? 	"Answer must be ""Yes""
  Minimum set of parameters are defined in the Section VRP Domestic Payments - a/c selection @PISP of the Customer Experience Guidelines"	Required	n/a	Conditional	"Roadmap item A10 & A2 b(i)
  RTS Art. 36(4)  "
  22b	Functionality	PISP	Do you capture set of consent parameters required for sweeping payments to be completed for each payment type? 	"Answer must be ""Yes""
  Set of parameters are defined in the Section Sweeping Domestic Payments - a/c selection @PISP of the Customer Experience Guidelines"	Required	n/a	Conditional	"Roadmap item A10 & A2 b(i)
  RTS Art. 36(4)  "
  23	Functionality	ASPSP	In cases where the payment instruction is incomplete because the account details have not been provided by the PSU to the PISP, do you allow the PSU to select the account from which they wish to make the payment? 	Answer must be "Yes"	Required	Mandatory	Mandatory	FCA Approach Document 17.143
  24	Functionality	PISP	Do you offer the PSU at least one of the available options for selecting the payment account during the payment initiation as defined in the Customer Experience Guidelines Section Payment Initiation Services (PIS) ?	"Answer must be ""Yes""

The available options for selecting an account are defined in Section 4 as:
•enter their Account Identification details directly to the PISP
•select their Account Identification details at the PISP (this assumes they have been saved previously) 
•select their ASPSP in order to select their account from within the ASPSP’s domain later in the journey"	Required	n/a	n/a
25	Status of payment	ASPSP	Do you provide or make available all information regarding initiation and execution of the payment to the PISP immediately after receipt of the payment order?	Answer must be "Yes"	Required	Mandatory	Mandatory	"PSRs Reg. 69(2)(b)                                                                                     RTS Art. 36(1)(b)  
FCA Approach Document 17.27-17.29"
26	Status of payment	PISP	Do you display all the required information to the PSU immediately after the initiation of the payment order? 	"Answer must be ""Yes""
Types of information are defined in Section 4.1 "	Required	n/a	Mandatory	PSRs Reg. 44(1)
26a	Status of VRP Consent Setup	PISP	Do you display all the required information to the PSU immediately after the VRP Consent setup with the ASPSP? 	Answer must be "Yes"	Customer-Required	n/a	n/a	Roadmap item A10 & A2 b(i)  
27	Status of payment	PISP	After receiving the initial payment status information, do you follow up with the ASPSP in order to get the latest status of the payment and inform the PSU accordingly?	Answer should be "Yes"	Recommended	n/a	n/a
28	Display of payment details	ASPSP	Do you make the PSU aware of the amount/currency/payee as part of the authentication journey?	Answer must be “Yes”, unless an SCA exemption is being applied	Required	n/a	Conditional	RTS Art. 5(1)(a)
28a	Display of payment details	ASPSP	Do you make the PSU aware of all the consent parameters associated with the variable recurring payment access, as part of the authentication journey?	Answer must be “Yes”	Customer-Required	n/a	n/a	Roadmap item A10 & A2 b(i)  
28b	Trusted Beneficiary setup	ASPSP	During the authentication journey, do you inform the PSU that the payee will be added to their list of payees and also add to the PSU's List of Payees?	Answer must be “Yes”	Required	Conditional	n/a	Roadmap item A10 & A2 b(i)  
28c	Trusted Beneficiary application	ASPSP	When the PISP initiates a Sweeping payment within the Sweeping consent parameters, do you apply the Trusted Beneficiary SCA exemption?	Answer must be “Yes”	Required	Conditional	n/a	Roadmap item A10  
28d	Reject payment & response	ASPSP	"Do you reject Sweeping/VRP payment and provide appropriate response to the PISP if?

* the Sweeping / VRP payment is outside consent parameters.
* the Sweeping / VRP Consent setup is revoked by PSU at the ASPSP."	Answer must be “Yes”	Required	Conditional	n/a	Roadmap item A10  
  28e	Consent parameters	ASPSP	"Do you support all periodic limits and capable of handling multiple limits in a single consent (as shown under the Section -
* VRP Payments with delegated SCA
* VRP Payments with an SCA exemption
* VRP Payments under sweeping access
  of the Customer Experience Guidelines)?"	Answer must be "Yes"	Required	n/a	n/a	Roadmap item A10  
  28f	Functionality	ASPSP	Do you support the minimum and maximum payment limits made via PISP in line with direct online channels for each of the different payment types (eg. Faster payments, CHAPS etc)? 	Answer must be "Yes"	Required	Mandatory	Mandatory	"PSRs Reg. 69(2)(c)
  FCA Approach Document 17.38"
  29a	Confirmation of funds ("yes/no" response)*	ASPSP	Do you provide immediate confirmation of whether or not there are funds available at the PISP’s request, in a ‘yes or no’ format?	Answer must be "Yes"	Required	n/a	Mandatory	"RTS Art. 36(1)(c)
  EBA Opinion paragraph 22  
  FCA Approach Document 17.23, 17.24"
  29b	Confirmation of funds ("yes/no" response)*	ASPSP	If you cannot perform a funds check then do you provide PISPs the necessary data to allow them to make their own judgements on the sufficient availability of funds 	Answer must be "Yes"	Required	n/a	Mandatory	"RTS Art. 36(1)(c)
  EBA Opinion paragraph 22                                                                            FCA Approach Document 17.25"
  30	Future Dated Payments & Standing Orders	PISP	Do you inform the PSU that amendment or cancellation of standing orders and future dated payments must be performed directly with their ASPSP?	Answer must be "Yes"	Required	n/a	n/a
  Confirmation of Funds - CBPII
  31	Explicit consent	ASPSP	Do you, prior to receiving the first request from each CBPII, obtain explicit consent from the PSU to provide confirmation of funds in response to CBPII requests (as shown under the Customer Experience Guidelines Section Card Based Payment Instrument Issuers (CBPIIs) )?	Answer must be "Yes"	Required	n/a	Mandatory	PSRs Reg. 68(5)(b)                                                                                   FCA Approach Document 17.18
  32	Explicit consent	CBPII	Do you obtain explicit consent from the customer to request the confirmation of funds?	"Answer must be ""Yes”
  Minimum set of parameters are defined in the Section 5 of the Customer Experience Guidelines"	Required	n/a	Mandatory	"PSRs Reg. 68(3)(a)  
  FCA Approach Document 17.52,17.54"
  33	Functionality 	CBPII	Do you only request confirmation of funds when the PSU has initiated a payment transaction for the amount in question using the card based instrument? 	Answer must be "Yes"	Required	n/a	Mandatory	PSRs Reg. 68(3)(b)
  34	Confirmation of funds ("yes/no" response)	ASPSP	Do you provide immediate confirmation of funds in the form of a ‘yes’ or ‘no’ answer to a CBPII request where the payment account is accessible online?	Answer must be "Yes"	Required	n/a	Mandatory	"PSRs Reg. 68(4)
  RTS Art. 36(1)(c)
  EBA Opinion paragraph 22  
  FCA Approach Document 17.21, 17.22"

Note: CMA Order includes the Trustee's P3/P4 Evaluation letter and PSD2 / RTS includes the EBA Opinion and (draft) Exemption Guidelines .

/

<HTMLBlock>{`
<iframe 
  src="https://onedrive.live.com/embed?cid=YOUR_CID&resid=YOUR_RESID&authkey=YOUR_AUTH_KEY&em=2&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True" 
  width="100%" 
  height="400" 
  frameborder="0">
</iframe>
`}</HTMLBlock>

<br />

<HTMLBlock>{`
<iframe 
  src=""C:\Users\MikeBanyard\OneDrive - Open Banking Ltd\CEG CBPII User Journey.xlsx"cid=YOUR_CID&resid=YOUR_RESID&authkey=YOUR_AUTH_KEY&em=2&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True" 
  width="100%" 
  height="400" 
  frameborder="0">
</iframe>
`}</HTMLBlock>
