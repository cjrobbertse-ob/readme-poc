---
title: Domestic Payments
hidden: false
---
## Overview

The Domestic Payments Consent resource is used by a <Glossary>PISP</Glossary> to register an intent to initiate a Domestic Payment.

<PISProfile />

## Endpoints

<Endpoints />

| Resource                    | HTTP Operation | Endpoint                                                        | Mandatory ? | Scope    | Grant Type         | Message Signing                | Idempotency Key | Request Object          | Response Object                   |
| --------------------------- | -------------- | --------------------------------------------------------------- | ----------- | -------- | ------------------ | ------------------------------ | --------------- | ----------------------- | --------------------------------- |
| `domestic-payment-consents` | `POST`         | `POST /domestic-payment-consents`                               | Mandatory   | payments | Client Credentials | Signed Request Signed Response | Yes             | OBWriteDomesticConsent4 | OBWriteDomesticConsentResponse5   |
| `domestic-payment-consents` | `GET`          | `GET /domestic-payment-consents/{ConsentId}`                    | Mandatory   | payments | Client Credentials | Signed Response                | No              | NA                      | OBWriteDomesticConsentResponse5   |
| `domestic-payment-consents` | `GET`          | `GET /domestic-payment-consents/{ConsentId}/funds-confirmation` | Mandatory   | payments | Authorization Code | Signed Response                | No              | NA                      | OBWriteFundsConfirmationResponse1 |

### `POST /domestic-payment-consents`

The API endpoint allows the <Glossary>PISP</Glossary> to ask an <Glossary>ASPSP</Glossary> to create a new `domestic-payment-consent` resource.

- The `POST` action indicates to the <Glossary>ASPSP</Glossary> that a domestic payment consent has been staged. At this point, the <Glossary>PSU</Glossary> **may not** have been identified by the <Glossary>ASPSP</Glossary>, and the request payload **may not** contain any information of the account that should be debited.

<PISEndpointCopy />

- The <Glossary>ASPSP</Glossary> creates the `domestic-payment-consent` resource and responds with a unique ConsentId to refer to the resource.

#### Status

The default Status is `AWAU` immediately after the `domestic-payment-consent` has been created.

<ConsentStatusAWAU />

### `GET /domestic-payment-consents/{ConsentId}`

<PISGetOption />

#### Status

Once the <Glossary>PSU</Glossary> authorises the domestic-payment-consent resource, the Status of the `domestic-payment-consent` resource **must** be updated with `AUTH`.

If the <Glossary>PSU</Glossary> rejects the consent or the `domestic-payment-consent` has failed some other <Glossary>ASPSP</Glossary> validation, the Status **must** be set to `RJCT`.

Once a `domestic-payment` has been successfully created using the `domestic-payment-consent`, the Status of the domestic-payment-consent **must** be set to `COND`.

The available status codes for the `domestic-payment-consent` resource are:

<ConsentStatusPIS />

### `GET/domestic-payment-consents/{ConsentId}/funds-confirmation`

The API endpoint allows the <Glossary>PISP</Glossary> to ask an <Glossary>ASPSP</Glossary> to confirm funds on a `domestic-payment-consent` resource.

- An <Glossary>ASPSP</Glossary> can only respond to a funds confirmation request if the `domestic-payment-consent` resource has an `AUTH` status. If the status is not `AUTH`, an <Glossary>ASPSP</Glossary> **must** respond with a 400 (Bad Request) and a `U009` error code.
- Confirmation of funds requests do not affect the status of the `domestic-payment-consent` resource.

### State Model

#### Payment Order Consent

The state model for the `domestic-payment-consent` resource follows the generic consent state model.

![](https://files.readme.io/ef1d32566dc6cd9eca5963113443ae7866ffc3cc8a7a214d8a80e809a0ab6c45-image.png)

<br />

The definitions for the Status:

<ConsentStatusPIS />

<PISStatusChange />

## Data Model

The data dictionary section gives the detail on the payload content for the Domestic Payment API flows.

### Reused Classes

#### `OBRemittanceInformation2`

The `OBRemittanceInformation2` class is defined in the [payment-initiation-api-profile](../../profiles/payment-initiation-api-profile.md#obremittanceinformation2) page.

#### `OBRegulatoryReporting1`

The `OBRegulatoryReporting1` class is defined in the [payment-initiation-api-profile](../../profiles/payment-initiation-api-profile.md#obregulatoryreporting1) page.

#### `OBUltimateCreditor1`

The `OBUltimateCreditor1` class is defined in the [payment-initiation-api-profile](../../profiles/payment-initiation-api-profile.md#obultimatecreditor1) page.

#### `OBUltimateDebtor1`

The `OBUltimateDebtor1` class is defined in the [payment-initiation-api-profile](../../profiles/payment-initiation-api-profile.md#obultimatedebtor1) page.

#### `OBPostalAddress7`

The `OBPostalAddress7` class is defined in the [payment-initiation-api-profile](../../profiles/payment-initiation-api-profile.md#obpostaladdress7) page

#### `OBDomestic2`

This section describes the `OBDomestic2` class which is reused as the Initiation object in the `domestic-payment-consent` resource.

##### UML Diagram

<UmlGenerator
  api="PIS"
  schema="OBWriteDomesticConsent4.properties.Data.properties.Initiation:OBDomestic2"
/>

<br />

<br />

![](https://files.readme.io/b2e652d77b7c1dd60b77df0d7e22e6dc33435b496fc7781cf8d2f207fbd3c803-image.png)

#### Notes

For the `OBDomestic2` Initiation object:

- All elements in the Initiation payload that are specified by the <Glossary>PISP</Glossary> **must not**be changed via the <Glossary>ASPSP</Glossary> as this is part of formal consent from the <Glossary>PSU</Glossary>.
- If the <Glossary>ASPSP</Glossary> is able to establish a problem with payload or any contextual error during the API call, the <Glossary>ASPSP</Glossary> **must** reject the `domestic-payment-consent` request immediately.
- If the <Glossary>ASPSP</Glossary> establishes a problem with the `domestic-payment-consent` after the API call, the <Glossary>ASPSP</Glossary> **must** set the Status of the `domestic-payment-consent` resource to `RJCT` (Rejected).
- DebtorAccount is **optional** as the <Glossary>PISP</Glossary> may not know the account identification details for the <Glossary>PSU</Glossary>.
- If the `DebtorAccount` is specified by the <Glossary>PISP</Glossary> and is invalid for the <Glossary>PSU</Glossary>, then the `domestic-payment-consent` will be set to `RJCT` (Rejected) after <Glossary>PSU</Glossary> authentication.
- Account Identification field usage:
  - Where `UK.OBIE.SortCodeAccountNumber` is specified as the `SchemeName` in the Account identification section (either `DebtorAccount` or `CreditorAccount`), the `Identification` field **must** be populated with the 6 digit Sort Code and 8 digit Account Number (a 14 digit field).
  - Where the `UK.OBIE.IBAN` is specified as the `SchemeName` in the Account identification section (either `DebtorAccount` or `CreditorAccount`), the `Identification` field **must** be populated with the full IBAN.
- The element `Reference` has been renamed from `CreditorReferenceInformation` as this is the unique ISO 20022 element used in pain.001, rather than an ISO 20022 message component.
- As a merchant **may** be initiating a payment via a <Glossary>PISP</Glossary>, two identifiers are included in the payload:
  - `InstructionIdentification` is uniquely generated by the <Glossary>PISP</Glossary>. The expectation is that this is unique indefinitely across all time periods. The <Glossary>PISP</Glossary> can ensure that this is indefinitely unique by including a date or date-time element to the field, or by inserting a unique Id.
  - `EndToEndIdentification` is uniquely generated by the merchant.
- Neither the `InstructionIdentification` nor `EndToEndIdentification` are used as the `domestic-payment-consent` resource identifier (ConsentId) as the ConsentId **must** be uniquely generated by the <Glossary>ASPSP</Glossary>.
- `LocalInstrument` is the requested payment scheme for execution. This is an enum.
- Design decisions for the Initiation section of the payload and how this maps to the ISO 20022 messaging standard are articulated in the Mapping to Schemes and Standards section.

##### Data Dictionary

| Name                      | Occurrence | XPath                                               | EnhancedDefinition                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Class                                                                                                                                     | Codes                                             | Pattern                       |                      |
| :------------------------ | :--------- | :-------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------ | :---------------------------- | :------------------- |
| OBDomestic2               |            | OBDomestic2                                         | The Initiation payload is sent by the initiating party to the ASPSP. It is used to request movement of funds from the debtor account to a creditor for a single domestic payment.                                                                                                                                                                                                                                                                                              | OBDomestic2                                                                                                                               |                                                   |                               |                      |
| InstructionIdentification | 1..1       | OBDomestic2/InstructionIdentification               | Unique identification as assigned by an instructing party for an instructed party to unambiguously identify the instruction. Usage: the instruction identification is a point to point reference that can be used between the instructing party and the instructed party to refer to the individual instruction. It can be included in several messages related to the instruction.                                                                                            | Max35Text                                                                                                                                 |                                                   |                               |                      |
| EndToEndIdentification    | 1..1       | OBDomestic2/EndToEndIdentification                  | Unique identification assigned by the initiating party to unambiguously identify the transaction. This identification is passed on, unchanged, throughout the entire end-to-end chain. Usage: The end-to-end identification can be used for reconciliation or to link tasks relating to the transaction. It can be included in several messages related to the transaction. OB: The Faster Payments Scheme can only access 31 characters for the EndToEndIdentification field. | Max35Text                                                                                                                                 |                                                   |                               |                      |
| LocalInstrument           | 0..1       | OBDomestic2/LocalInstrument                         | User community specific instrument. Usage: This element is used to specify a local instrument, local clearing option and/or further qualify the service or service level.                                                                                                                                                                                                                                                                                                      | For a full list of enumeration values refer to `OB_Internal_CodeSet` [here](https://github.com/OpenBankingUK/External_Internal_CodeSets)  | OBInternalLocalInstrument1Code                    |                               |                      |
| InstructedAmount          | 1..1       | OBDomestic2/InstructedAmount                        | Amount of money to be moved between the debtor and creditor, before deduction of charges, expressed in the currency as ordered by the initiating party. Usage: This amount has to be transported unchanged through the transaction chain.                                                                                                                                                                                                                                      | OBActiveOrHistoricCurrencyAndAmount                                                                                                       |                                                   |                               |                      |
| Amount                    | 1..1       | OBDomestic2/InstructedAmount/Amount                 | A number of monetary units specified in an active currency where the unit of currency is explicit and compliant with ISO 4217.                                                                                                                                                                                                                                                                                                                                                 | OBActiveCurrencyAndAmount\_SimpleType                                                                                                     |                                                   | \`^\d{1,13}$                  | ^\d{1,13}.\d{1,5}$\` |
| Currency                  | 1..1       | OBDomestic2/InstructedAmount/Currency               | A code allocated to a currency by a Maintenance Agency under an international identification scheme, as described in the latest edition of the international standard ISO 4217 "Codes for the representation of currencies and funds".                                                                                                                                                                                                                                         | ActiveOrHistoricCurrencyCode                                                                                                              |                                                   | ^\[A-Z]{3,3}$                 |                      |
| DebtorAccount             | 0..1       | OBDomestic2/DebtorAccount                           | Unambiguous identification of the account of the debtor to which a debit entry will be made as a result of the transaction.                                                                                                                                                                                                                                                                                                                                                    | OBCashAccountDebtorWithName                                                                                                               |                                                   |                               |                      |
| UltimateDebtor            | 0..1       | OBDomestic2/UltimateDebtor                          | Ultimate party that owes an amount of money to the (ultimate) creditor.                                                                                                                                                                                                                                                                                                                                                                                                        | OBUltimateDebtor1                                                                                                                         |                                                   |                               |                      |
| CreditorAccount           | 1..1       | OBDomestic2/CreditorAccount                         | Unambiguous identification of the account of the creditor to which a credit entry will be posted as a result of the payment transaction.                                                                                                                                                                                                                                                                                                                                       | OBCashAccountCreditor3                                                                                                                    |                                                   |                               |                      |
| SchemeName                | 1..1       | OBDomestic2/CreditorAccount/SchemeName              | Name of the identification scheme, in a coded form as published in an external list.                                                                                                                                                                                                                                                                                                                                                                                           | For a full list of enumeration values refer to `OB_Internal_CodeSet` [here](https://github.com/OpenBankingUK/External_Internal_CodeSets). | OBInternalAccountIdentification4Code              |                               |                      |
| Identification            | 1..1       | OBDomestic2/CreditorAccount/Identification          | Identification assigned by an institution to identify an account. This identification is known by the account owner.                                                                                                                                                                                                                                                                                                                                                           | Max256Text                                                                                                                                |                                                   |                               |                      |
| Name                      | 1..1       | OBDomestic2/CreditorAccount/Name                    | The account name is the name or names of the account owner(s) represented at an account level. Note, the account name is not the product name or the nickname of the account. OB: ASPSPs may carry out name validation for Confirmation of Payee, but it is not mandatory.                                                                                                                                                                                                     | Max350Text                                                                                                                                |                                                   |                               |                      |
| SecondaryIdentification   | 0..1       | OBDomestic2/CreditorAccount/SecondaryIdentification | This is secondary identification of the account, as assigned by the account servicing institution. This can be used by building societies to additionally identify accounts with a roll number (in addition to a sort code and account number combination).                                                                                                                                                                                                                    | Max34Text                                                                                                                                 |                                                   |                               |                      |
| Proxy                     | 0..1       | OBDomestic2/CreditorAccount/Proxy                   | Specifies an alternate assumed name for the identification of the account.                                                                                                                                                                                                                                                                                                                                                                                                     | OBProxy1                                                                                                                                  |                                                   |                               |                      |
| UltimateCreditor          | 0..1       | OBDomestic2/UltimateCreditor                        | Ultimate party to which an amount of money is due.                                                                                                                                                                                                                                                                                                                                                                                                                             | OBUltimateCreditor1                                                                                                                       |                                                   |                               |                      |
| CreditorPostalAddress     | 0..1       | OBDomestic2/CreditorPostalAddress                   | Information that locates and identifies a specific address, as defined by postal services.                                                                                                                                                                                                                                                                                                                                                                                     | OBPostalAddress7                                                                                                                          |                                                   |                               |                      |
| RemittanceInformation     | 0..1       | OBDomestic2/RemittanceInformation                   | Information supplied to enable the matching of an entry with the items that the transfer is intended to settle, such as commercial invoices in an accounts' receivable system.                                                                                                                                                                                                                                                                                                 | OBRemittanceInformation2                                                                                                                  |                                                   |                               |                      |
| RegulatoryReporting       | 0..10      | OBDomestic2/RegulatoryReporting                     | Information needed due to regulatory and statutory requirements.                                                                                                                                                                                                                                                                                                                                                                                                               | OBRegulatoryReporting1                                                                                                                    |                                                   |                               |                      |
| SupplementaryData         | 0..1       | OBDomestic2/SupplementaryData                       | Additional information that can not be captured in the structured fields and/or any other specific block.                                                                                                                                                                                                                                                                                                                                                                      | OBSupplementaryData1                                                                                                                      |                                                   |                               |                      |
| CreditorAgent             | 0..1       | OBDomestic2/CreditorAgent                           | Financial institution servicing an account for the creditor.                                                                                                                                                                                                                                                                                                                                                                                                                   | OBBranchAndFinancialInstitutionIdentification6                                                                                            |                                                   |                               |                      |
| SchemeName                | 0..1       | OBDomestic2/CreditorAgent/SchemeName                | Name of the identification scheme, in a coded form as published in an external list.                                                                                                                                                                                                                                                                                                                                                                                           | For a full list of enumeration values refer to `OB_Internal_CodeSet` [here](https://github.com/OpenBankingUK/External_Internal_CodeSets). | OBExternalFinancialInstitutionIdentification4Code |                               |                      |
| Identification            | 0..1       | OBDomestic2/CreditorAgent/Identification            | Unique and unambiguous identification of a financial institution or a branch of a financial institution.                                                                                                                                                                                                                                                                                                                                                                       | Max35Text                                                                                                                                 |                                                   |                               |                      |
| Name                      | 0..1       | OBDomestic2/CreditorAgent/Name                      | Name by which an agent is known and which is usually used to identify that agent.                                                                                                                                                                                                                                                                                                                                                                                              | Max140Text                                                                                                                                |                                                   |                               |                      |
| LEI                       | 0..1       | OBDomestic2/CreditorAgent/LEI                       | Legal Entity Identifier is a code allocated to a party as described in ISO 17442 "Financial Services - Legal Entity Identifier (LEI)".                                                                                                                                                                                                                                                                                                                                         | Max20Text                                                                                                                                 |                                                   | ^\[A-Z0-9]{18,18}\[0-9]{2,2}$ |                      |
| PostalAddress             | 0..1       | OBDomestic2/CreditorAgent/PostalAddress             | Information that locates and identifies a specific address, as defined by postal services.                                                                                                                                                                                                                                                                                                                                                                                     | OBPostalAddress7                                                                                                                          |                                                   |                               |                      |

### Domestic Payment Consent - Request

The `OBWriteDomesticConsent4` object is used for the call to:

- `POST /domestic-payment-consents`

#### UML Diagram

![](https://files.readme.io/e6392a73bf996cc8a40a1672245091e64625c772bbe7574c3555c3d7c575a71c-image.png)

<br />

#### Notes

The `domestic-payment-consent` **request** contains these objects:

- `Initiation`
- `Authorisation`
- `SCASupportData`

#### Data Dictionary

| Name                    | Occurrence              | XPath                                          | EnhancedDefinition                                                                                                                                                                | Class                                                                                                                                     | Codes                            | Pattern |
| ----------------------- | ----------------------- | ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- | ------- |
| OBWriteDomesticConsent4 | OBWriteDomesticConsent4 |                                                |                                                                                                                                                                                   | OBWriteDomesticConsent4                                                                                                                   |                                  |         |
| Data                    | 1..1                    | OBWriteDomesticConsent4/Data                   |                                                                                                                                                                                   | OBWriteDataDomesticConsent4                                                                                                               |                                  |         |
| ReadRefundAccount       | 0..1                    | OBWriteDomesticConsent4/Data/ReadRefundAccount | Specifies to share the refund account details with PISP                                                                                                                           | For a full list of enumeration values refer to `OB_Internal_CodeSet` [here](https://github.com/OpenBankingUK/External_Internal_CodeSets). | OBInternalReadRefundAccount1Code |         |
| Initiation              | 1..1                    | OBWriteDomesticConsent4/Data/Initiation        | The Initiation payload is sent by the initiating party to the ASPSP. It is used to request movement of funds from the debtor account to a creditor for a single domestic payment. | OBDomestic2                                                                                                                               |                                  |         |
| Authorisation           | 0..1                    | OBWriteDomesticConsent4/Data/Authorisation     | The authorisation type request from the TPP.                                                                                                                                      | OBAuthorisation1                                                                                                                          |                                  |         |
| SCASupportData          | 0..1                    | OBWriteDomesticConsent4/Data/SCASupportData    | Supporting Data provided by TPP, when requesting SCA Exemption.                                                                                                                   | OBSCASupportData1                                                                                                                         |                                  |         |

### Domestic Payment Consent - Response

The `OBWriteDomesticConsentResponse5` object will be used for a response to a call to:

- `POST /domestic-payment-consents`
- `GET /domestic-payment-consents/{ConsentId}`

#### UML Diagram

![](https://files.readme.io/b25301ce60a83fc37d54dc3f51a05f8bad7b6f459044da32e03d47467d82aab8-image.png)

<br />

#### Notes

The `domestic-payment-consent` **response** contains the full **original** payload from the `domestic-payment-consent` **request**, with the additional elements below:

- `ConsentId`
- `CreationDateTime` the`domestic-payment-consent`resource was created.
- `Status` and `StatusUpdateDateTime` of the `domestic-payment-consent` resource.
- CutOffDateTime Behaviour is explained in Payment Initiation API Profile, Section - [Payment Restrictions -> CutOffDateTime Behaviour](../../profiles/payment-initiation-api-profile.md#cutoffdatetime-behaviour).
- `ExpectedExecutionDateTime` for the `domestic-payment` resource if created before `CutOffDateTIme` - the expected DateTime the payment is executed against the `Debtor Account`. If populated, the <Glossary>ASPSP</Glossary> **must** update the value with any changes (e.g., after <Glossary>PSU</Glossary>PSU authorisation).
- Charges array for the breakdown of applicable <Glossary>ASPSP</Glossary> charges.
- Post successful <Glossary>PSU</Glossary> Authentication, an <Glossary>ASPSP</Glossary> **may** provide `DebtorName` in the Payment Order Consent Response, even when the Payer didn't provide the Debtor Account via <Glossary>PISP</Glossary>.

#### Data Dictionary

| Name                            | Occurrence | XPath                                                                     | EnhancedDefinition                                                                                                                                                                | Class                                                                                                                                     | Codes                            | Pattern |
| ------------------------------- | ---------- | ------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- | ------- |
| OBWriteDomesticConsentResponse5 |            | OBWriteDomesticConsentResponse5                                           |                                                                                                                                                                                   | OBWriteDomesticConsentResponse5                                                                                                           |                                  |         |
| Data                            | 1..1       | OBWriteDomesticConsentResponse5/Data                                      |                                                                                                                                                                                   | OBWriteDataDomesticConsentResponse5                                                                                                       |                                  |         |
| ConsentId                       | 1..1       | OBWriteDomesticConsentResponse5/Data/ConsentId                            | OB: Unique identification as assigned by the ASPSP to uniquely identify the consent resource.                                                                                     | Max128Text                                                                                                                                |                                  |         |
| CreationDateTime                | 1..1       | OBWriteDomesticConsentResponse5/Data/CreationDateTime                     | Date and time at which the resource was created.                                                                                                                                  | ISODateTime                                                                                                                               |                                  |         |
| Status                          | 1..1       | OBWriteDomesticConsentResponse5/Data/Status                               | Specifies the status of consent resource in code form.                                                                                                                            | For a full list of enumeration values refer to `OB_Internal_CodeSet` [here](https://github.com/OpenBankingUK/External_internal_CodeSets)  | OBInternalConsentStatus2Code     |         |
| StatusReason                    | 0..\*      | OBWriteDomesticConsentResponse5/Data/StatusReason                         | An array of StatusReasonCode                                                                                                                                                      | OBStatusReason                                                                                                                            |                                  |         |
| StatusReasonCode                | 0..1       | OBWriteDomesticConsentResponse5/Data/StatusReason/StatusReasonCode        | Specifies the status reason in a code form.                                                                                                                                       | For a full list of enumeration values refer to `OB_Internal_CodeSet` [here](https://github.com/OpenBankingUK/External_internal_CodeSets)  | OBExternalStatusReason1Code      |         |
| StatusReasonDescription         | 0..1       | OBWriteDomesticConsentResponse5/Data/StatusReason/StatusReasonDescription | Description supporting the StatusReasonCode.                                                                                                                                      | Max500Text                                                                                                                                |                                  |         |
| Path                            | 0..1       | OBWriteDomesticConsentResponse5/Data/StatusReason/Path                    | Path is optional but relevant when the status reason refers to an object/field and hence conditional to provide JSON path.                                                        | Max500Text                                                                                                                                |                                  |         |
| StatusUpdateDateTime            | 1..1       | OBWriteDomesticConsentResponse5/Data/StatusUpdateDateTime                 | Date and time at which the resource status was updated.                                                                                                                           | ISODateTime                                                                                                                               |                                  |         |
| ReadRefundAccount               | 0..1       | OBWriteDomesticConsentResponse5/Data/ReadRefundAccount                    | Specifies to share the refund account details with PISP                                                                                                                           | For a full list of enumeration values refer to `OB_Internal_CodeSet` [here](https://github.com/OpenBankingUK/External_Internal_CodeSets). | OBInternalReadRefundAccount1Code |         |
| CutOffDateTime                  | 0..1       | OBWriteDomesticConsentResponse5/Data/CutOffDateTime                       | Specified cut-off date and time for the payment consent.                                                                                                                          | ISODateTime                                                                                                                               |                                  |         |
| ExpectedExecutionDateTime       | 0..1       | OBWriteDomesticConsentResponse5/Data/ExpectedExecutionDateTime            | Expected execution date and time for the payment resource.                                                                                                                        | ISODateTime                                                                                                                               |                                  |         |
| ExpectedSettlementDateTime      | 0..1       | OBWriteDomesticConsentResponse5/Data/ExpectedSettlementDateTime           | Expected settlement date and time for the payment resource.                                                                                                                       | ISODateTime                                                                                                                               |                                  |         |
| Charges                         | 0..\*      | OBWriteDomesticConsentResponse5/Data/Charges                              | Set of elements used to provide details of a charge for the payment initiation.                                                                                                   | OBCharge2                                                                                                                                 |                                  |         |
| Initiation                      | 1..1       | OBWriteDomesticConsentResponse5/Data/Initiation                           | The Initiation payload is sent by the initiating party to the ASPSP. It is used to request movement of funds from the debtor account to a creditor for a single domestic payment. | OBDomestic2                                                                                                                               |                                  |         |
| Authorisation                   | 0..1       | OBWriteDomesticConsentResponse5/Data/Authorisation                        | The authorisation type request from the TPP.                                                                                                                                      | OBAuthorisation1                                                                                                                          |                                  |         |
| SCASupportData                  | 0..1       | OBWriteDomesticConsentResponse5/Data/SCASupportData                       | Supporting Data provided by TPP, when requesting SCA Exemption.                                                                                                                   | OBSCASupportData1                                                                                                                         |                                  |         |
| Debtor                          | 0..1       | OBWriteDomesticConsentResponse5/Data/Debtor                               | Set of elements used to identify a person or an organisation.                                                                                                                     | OBCashAccountDebtor4                                                                                                                      |                                  |         |
| Risk                            | 1..1       | OBWriteDomesticConsentResponse5/Risk                                      | The Risk section is sent by the initiating party to the ASPSP. It is used to specify additional details for risk scoring for Payments.                                            | OBRisk1                                                                                                                                   |                                  |         |

### Domestic Payment Consent Confirmation of Funds - Response

The `OBWriteFundsConfirmationResponse1` object is used for a response to a call to:

- `GET /domestic-payment-consents/{ConsentId}/funds-confirmation`

#### UML Diagram

![](https://files.readme.io/daa19ebb632da675b76fa1e89d036ea93e9eab8b740d043f3c19a17dc93c8f31-image.png)

<br />

#### Notes

The confirmation of funds response contains the result of a funds availability check, or SupplementaryData.

#### Data Dictionary

| Name                              | Occurrence | XPath                                                                              | EnhancedDefinition                                                                                        | Class                                 | Codes | Pattern |
| --------------------------------- | ---------- | ---------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------- | ----- | ------- |
| OBWriteFundsConfirmationResponse1 |            | OBWriteFundsConfirmationResponse1                                                  |                                                                                                           | OBWriteFundsConfirmationResponse1     |       |         |
| Data                              | 1..1       | OBWriteFundsConfirmationResponse1/Data                                             |                                                                                                           | OBWriteDataFundsConfirmationResponse1 |       |         |
| FundsAvailableResult              | 0..1       | OBWriteFundsConfirmationResponse1/Data/FundsAvailableResult                        | Result of a funds availability check.                                                                     | OBFundsAvailableResult1               |       |         |
| FundsAvailableDateTime            | 1..1       | OBWriteFundsConfirmationResponse1/Data/FundsAvailableResult/FundsAvailableDateTime | Date and time at which the funds availability check was generated.                                        | ISODateTime                           |       |         |
| FundsAvailable                    | 1..1       | OBWriteFundsConfirmationResponse1/Data/FundsAvailableResult/FundsAvailable         | Flag to indicate the availability of funds given the Amount in the consent request.                       | xs:boolean                            |       |         |
| SupplementaryData                 | 0..1       | OBWriteFundsConfirmationResponse1/Data/SupplementaryData                           | Additional information that can not be captured in the structured fields and/or any other specific block. | OBSupplementaryData1                  |       |         |

## Usage Examples

Note, further usage examples are available [here](../../references/usage-examples/README.md).

### `POST` /domestic-payment-consents

#### Request

<br />

```
POST /domestic-payment-consents HTTP/1.1
Authorization: Bearer 2YotnFZFEjr1zCsicMWpAA
x-idempotency-key: FRESCO.21302.GFX.20
x-jws-signature: TGlmZSdzIGEgam91cm5leSBub3QgYSBkZXN0aW5hdGlvbiA=..T2ggZ29vZCBldmVuaW5nIG1yIHR5bGVyIGdvaW5nIGRvd24gPw==
x-fapi-auth-date: Sun, 10 Sep 2017 19:43:31 GMT
x-fapi-customer-ip-address: 104.25.212.99
x-fapi-interaction-id: 93bac548-d2de-4546-b106-880a5018460d
Content-Type: application/json
Accept: application/json
```

<br />

```json
{
  "Data": {
    "ReadRefundAccount": "Yes",
    "Initiation": {
      "InstructionIdentification": "ACME412",
      "EndToEndIdentification": "FRESCO.21302.GFX.20",
      "LocalInstrument": "UK.OBIE.CHAPS",
      "InstructedAmount": {
        "Amount": "165.88",
        "Currency": "GBP"
      },
      "DebtorAccount": {
        "SchemeName": "UK.OBIE.SortCodeAccountNumber",
        "Identification": "08080025612489",
        "SecondaryIdentification": "080801562314789",
        "Name": "Jane Smith",
        "Proxy": {
          "Identification": "441234012345",
          "Code": "TELE",
          "Type": "Telephone"
        }
      },
      "CreditorAccount": {
        "SchemeName": "UK.OBIE.SortCodeAccountNumber",
        "Identification": "08080021325698",
        "Name": "ACME Inc",
        "SecondaryIdentification": "0002",
        "Proxy": {
          "Identification": "2360549017905188",
          "Code": "TELE",
          "Type": "Telephone"
        }
      },
      "CreditorPostalAddress": {
        "AddressType": "BIZZ",
        "Department": "Finance",
        "SubDepartment": "Payroll",
        "StreetName": "Bank Street",
        "BuildingNumber": "11",
        "BuildingName": "Tower Bridges",
        "Floor": "6",
        "UnitNumber": "UNIT591",
        "Room": "844",
        "PostBox": "PO Box 123456",
        "PostCode": "Z78 4TY",
        "TownLocationName": "Bank",
        "TownName": "London",
        "DistrictName": "Greater London",
        "CareOf": "Ms Jane Smith",
        "CountrySubDivision": "England",
        "Country": "GB"
      },
      "UltimateDebtor": {
        "SchemeName": "UK.OBIE.BICFI",
        "Identification": "2360549017905161589",
        "Name": "Ultimate Debtor",
        "LEI": "8200007YHFDMEODY1965",
        "PostalAddress": {
          "AddressType": "BIZZ",
          "StreetName": "Bank Street",
          "BuildingNumber": "11",
          "Floor": "6",
          "PostCode": "Z78 4TY",
          "TownName": "London",
          "Country": "GB"
        }
      },
      "CreditorAgent": {
        "LEI": "IZ9Q00LZEVUKWCQY6X15",
        "SchemeName": "UK.OBIE.BICFI",
        "Identification": "80200112344562",
        "Name": "The Credit Agent",
        "PostalAddress": {
          "AddressType": "BIZZ",
          "StreetName": "Bank Street",
          "BuildingNumber": "11",
          "Floor": "6",
          "PostCode": "Z78 4TY",
          "TownName": "London",
          "Country": "GB"
        }
      },
      "UltimateCreditor": {
        "SchemeName": "UK.OBIE.BICFI",
        "Identification": "2360549017905161589",
        "Name": "Ultimate Creditor",
        "LEI": "60450004FECVJV7YN339",
        "PostalAddress": {
          "AddressType": "BIZZ",
          "StreetName": "Bank Street",
          "BuildingNumber": "11",
          "Floor": "6",
          "PostCode": "Z78 4TY",
          "TownName": "London",
          "Country": "GB"
        }
      },
      "RegulatoryReporting": [
        {
          "DebitCreditReportingIndicator": "CRED",
          "Authority": {
            "Name": "FCA",
            "CountryCode": "UK"
          },
          "Details": [
            {
              "Type": "CRED",
              "Date": "2024-04-25T13:26:41.911Z",
              "Information": [
                "Reg info1",
                "Reg info2"
              ],
              "Country": "UK",
              "Amount": {
                "Amount": "4.68702",
                "Currency": "GBP"
              }
            }
          ]
        }
      ],
      "RemittanceInformation": {
        "Structured": [
          {
            "ReferredDocumentInformation": [
              {
                "Code": "CINV",
                "Issuer": "Issuer01",
                "Number": "Number_01",
                "RelatedDate": "2024-04-25T13:26:41.911Z",
                "LineDetails": [
                  "LineDetail"
                ]
              }
            ],
            "ReferredDocumentAmount": "1.00",
            "CreditorReferenceInformation": {
              "Code": "DISP",
              "Issuer": "Issuer01",
              "Reference": "REF_26518"
            },
            "Invoicer": "INVR51856",
            "Invoicee": "INVE5161856",
            "TaxRemittance": "Tax Remittance related information",
            "AdditionalRemittanceInformation": [
              "Free text for additional information"
            ]
          }
        ],
        "Unstructured": [
          "Internal ops code 5120101"
        ]
      }
    },
    "Authorisation": {
      "AuthorisationType": "Any",
      "CompletionDateTime": "2024-04-25T14:20:41.911Z"
    },
    "SCASupportData": {
      "RequestedSCAExemptionType": "EcommerceGoods",
      "AppliedAuthenticationApproach": "SCA",
      "ReferencePaymentOrderId": "O-611265"
    }
  },
  "Risk": {
    "PaymentContextCode": "EcommerceMerchantInitiatedPayment",
    "ContractPresentIndicator": false,
    "PaymentPurposeCode": "EPAY",
    "CategoryPurposeCode": "CASH",
    "BeneficiaryPrepopulatedIndicator": false,
    "BeneficiaryAccountType": "Business",
    "MerchantCategoryCode": "7300",
    "MerchantCustomerIdentification": "053598653254",
    "DeliveryAddress": {
      "AddressLine": [
        "Flat 7",
        "Acacia Lodge"
      ],
      "StreetName": "Acacia Avenue",
      "BuildingNumber": "27",
      "PostCode": "GU31 2ZZ",
      "TownName": "Sparsholt",
      "CountrySubDivision": "Wessex",
      "Country": "GB"
    }
  }
}
```

#### Response

<br />

```
HTTP/1.1 201 Created
x-jws-signature: V2hhdCB3ZSBnb3QgaGVyZQ0K..aXMgZmFpbHVyZSB0byBjb21tdW5pY2F0ZQ0K
x-fapi-interaction-id: 93bac548-d2de-4546-b106-880a5018460d
Content-Type: application/json
```

<br />

```json
{
  "Data": {
    "ConsentId": "58923",
    "Status": "AWAU",
    "StatusReason": [
      {
        "StatusReasonCode": "U036",
        "StatusReasonDescription": "Waiting for completion of consent authorisation to be completed by user"
      }
    ],
    "CutOffDateTime": "2024-04-27T15:15:22+00:00",
    "ExpectedExecutionDateTime": "2024-04-25T15:15:22+00:00",
    "ExpectedSettlementDateTime": "2024-04-25T15:15:22+00:00",
    "CreationDateTime": "2024-04-25T15:15:13+00:00",
    "StatusUpdateDateTime": "2024-05-25T15:17:13+00:00",
    "ReadRefundAccount": "Yes",
    "Authorisation": {
      "AuthorisationType": "Any",
      "CompletionDateTime": "2024-04-25T14:20:41.911Z"
    },
    "Charges": [
      {
        "ChargeBearer": "Shared",
        "Type": "UK.OBIE.CHAPSOut",
        "Amount": {
          "Amount": "0.88",
          "Currency": "GBP"
        }
      }
    ],
    "Initiation": {
      "InstructionIdentification": "ACME412",
      "EndToEndIdentification": "FRESCO.21302.GFX.20",
      "LocalInstrument": "UK.OBIE.CHAPS",
      "InstructedAmount": {
        "Amount": "165.88",
        "Currency": "GBP"
      },
      "DebtorAccount": {
        "SchemeName": "UK.OBIE.SortCodeAccountNumber",
        "Identification": "08080025612489",
        "SecondaryIdentification": "080801562314789",
        "Name": "Jane Smith",
        "Proxy": {
          "Identification": "441234012345",
          "Code": "TELE",
          "Type": "Telephone"
        }
      },
      "CreditorAccount": {
        "SchemeName": "UK.OBIE.SortCodeAccountNumber",
        "Identification": "08080021325698",
        "Name": "ACME Inc",
        "SecondaryIdentification": "0002",
        "Proxy": {
          "Identification": "441234012885",
          "Code": "TELE",
          "Type": "Telephone"
        }
      },
      "CreditorAgent": {
        "LEI": "IZ9Q00LZEVUKWCQY6X15",
        "SchemeName": "UK.OBIE.BICFI",
        "Identification": "80200112344562",
        "Name": "The Credit Agent",
        "PostalAddress": {
          "AddressType": "BIZZ",
          "StreetName": "Bank Street",
          "BuildingNumber": "11",
          "Floor": "6",
          "PostCode": "Z78 4TY",
          "TownName": "London",
          "Country": "GB"
        }
      },
      "CreditorPostalAddress": {
        "AddressType": "BIZZ",
        "StreetName": "Bank Street",
        "BuildingNumber": "11",
        "Floor": "6",
        "PostCode": "Z78 4TY",
        "TownName": "London",
        "Country": "GB"
      },
      "UltimateDebtor": {
        "SchemeName": "UK.OBIE.BICFI",
        "Identification": "2360549017905161589",
        "Name": "Ultimate Debtor",
        "LEI": "8200007YHFDMEODY1965",
        "PostalAddress": {
          "AddressType": "BIZZ",
          "StreetName": "Bank Street",
          "BuildingNumber": "11",
          "Floor": "6",
          "PostCode": "Z78 4TY",
          "TownName": "London",
          "Country": "GB"
        }
      },
      "UltimateCreditor": {
        "SchemeName": "UK.OBIE.BICFI",
        "Identification": "2360549017905161589",
        "Name": "Ultimate Creditor",
        "LEI": "60450004FECVJV7YN339",
        "PostalAddress": {
          "AddressType": "BIZZ",
          "StreetName": "Bank Street",
          "BuildingNumber": "11",
          "Floor": "6",
          "PostCode": "Z78 4TY",
          "TownName": "London",
          "Country": "GB"
        }
      },
      "RegulatoryReporting": [
        {
          "DebitCreditReportingIndicator": "CRED",
          "Authority": {
            "Name": "FCA",
            "CountryCode": "UK"
          },
          "Details": [
            {
              "Type": "CRED",
              "Date": "2024-04-25T13:26:41.911Z",
              "Information": [
                "Reg info1",
                "Reg info2"
              ],
              "Country": "UK",
              "Amount": {
                "Amount": "4.68702",
                "Currency": "GBP"
              }
            }
          ]
        }
      ],
      "RemittanceInformation": {
        "Structured": [
          {
            "ReferredDocumentInformation": [
              {
                "Code": "CINV",
                "Issuer": "Issuer01",
                "Number": "Number_01",
                "RelatedDate": "2024-04-25T13:26:41.911Z",
                "LineDetails": [
                  "Line details entry 1"
                ]
              }
            ],
            "ReferredDocumentAmount": "1.00",
            "CreditorReferenceInformation": {
              "Code": "DISP",
              "Issuer": "Issuer01",
              "Reference": "REF_26518"
            },
            "Invoicer": "INVR51856",
            "Invoicee": "INVE5161856",
            "TaxRemittance": "Tax Remittance related information",
            "AdditionalRemittanceInformation": [
              "Free text for additional information"
            ]
          }
        ],
        "Unstructured": [
          "Internal ops code 5120101"
        ]
      }
    },
    "Debtor": {
      "Name": "D Jones",
      "SchemeName": "UK.OBIE.SortCodeAccountNumber",
      "Identification": "08080021325698",
      "SecondaryIdentification": "0002",
      "LEI": "8200007YHFDMEODY1965"
    },
    "SCASupportData": {
      "RequestedSCAExemptionType": "EcommerceGoods",
      "AppliedAuthenticationApproach": "SCA",
      "ReferencePaymentOrderId": "O-611265"
    }
  },
  "Risk": {
    "PaymentContextCode": "EcommerceMerchantInitiatedPayment",
    "ContractPresentIndicator": false,
    "PaymentPurposeCode": "EPAY",
    "CategoryPurposeCode": "CASH",
    "BeneficiaryPrepopulatedIndicator": false,
    "BeneficiaryAccountType": "Business",
    "MerchantCategoryCode": "7300",
    "MerchantCustomerIdentification": "053598653254",
    "DeliveryAddress": {
      "AddressLine": [
        "Flat 7",
        "Acacia Lodge"
      ],
      "StreetName": "Acacia Avenue",
      "BuildingNumber": "27",
      "PostCode": "GU31 2ZZ",
      "TownName": "Sparsholt",
      "CountrySubDivision": "Wessex",
      "Country": "GB"
    }
  },
  "Links": {
    "Self": "https://api.alphabank.com/open-banking/v4.0/pisp/domestic-payment-consents/58923"
  },
  "Meta": {}
}
```

<br />

### `GET` /domestic-payment-consents/{`{ConsentId}`}

#### Request

```
GET /domestic-payment-consents/58923 HTTP/1.1
Authorization: Bearer Jhingapulaav
x-fapi-auth-date: Sun, 10 Sep 2017 19:43:31 GMT
x-fapi-customer-ip-address: 104.25.212.99
x-fapi-interaction-id: 93bac548-d2de-4546-b106-880a5018460d
Accept: application/json
```

#### Response

```
HTTP/1.1 200 OK
x-jws-signature: V2hhdCB3ZSBnb3QgaGVyZQ0K..aXMgZmFpbHVyZSB0byBjb21tdW5pY2F0ZQ0K
x-fapi-interaction-id: 93bac548-d2de-4546-b106-880a5018460d
Content-Type: application/json
```

<br />

```json
``{
  "Data": {
    "ConsentId": "58923",
    "Status": "AUTH",
    "CreationDateTime": "2024-04-25T15:15:13+00:00",
    "StatusUpdateDateTime": "2024-05-25T15:17:13+00:00",
    "ReadRefundAccount": "Yes",
    "Initiation": {
      "InstructionIdentification": "ACME412",
      "EndToEndIdentification": "FRESCO.21302.GFX.20",
      "InstructedAmount": {
        "Amount": "165.88",
        "Currency": "GBP"
      },
      "CreditorAccount": {
        "SchemeName": "UK.OBIE.SortCodeAccountNumber",
        "Identification": "08080021325698",
        "Name": "ACME Inc",
        "SecondaryIdentification": "0002",
        "Proxy": {
          "Identification": "441234012885",
          "Code": "TELE",
          "Type": "Telephone"
        }
      },
      "CreditorPostalAddress": {
        "AddressType": "BIZZ",
        "StreetName": "Bank Street",
        "BuildingNumber": "11",
        "Floor": "6",
        "PostCode": "Z78 4TY",
        "TownName": "London",
        "Country": "GB"
      },
      "CreditorAgent": {
        "LEI": "IZ9Q00LZEVUKWCQY6X15",
        "SchemeName": "UK.OBIE.BICFI",
        "Identification": "80200112344562",
        "Name": "The Credit Agent",
        "PostalAddress": {
          "AddressType": "BIZZ",
          "StreetName": "Bank Street",
          "BuildingNumber": "11",
          "Floor": "6",
          "PostCode": "Z78 4TY",
          "TownName": "London",
          "Country": "GB"
        }
      },
      "UltimateDebtor": {
        "SchemeName": "UK.OBIE.BICFI",
        "Identification": "2360549017905161589",
        "Name": "Ultimate Debtor",
        "LEI": "8200007YHFDMEODY1965",
        "PostalAddress": {
          "AddressType": "BIZZ",
          "StreetName": "Bank Street",
          "BuildingNumber": "11",
          "Floor": "6",
          "PostCode": "Z78 4TY",
          "TownName": "London",
          "Country": "GB"
        }
      },
      "UltimateCreditor": {
        "SchemeName": "UK.OBIE.BICFI",
        "Identification": "2360549017905161589",
        "Name": "Ultimate Creditor",
        "LEI": "60450004FECVJV7YN339",
        "PostalAddress": {
          "AddressType": "BIZZ",
          "StreetName": "Bank Street",
          "BuildingNumber": "11",
          "Floor": "6",
          "PostCode": "Z78 4TY",
          "TownName": "London",
          "Country": "GB"
        }
      },
      "RegulatoryReporting": [
        {
          "DebitCreditReportingIndicator": "CRED",
          "Authority": {
            "Name": "FCA",
            "CountryCode": "UK"
          },
          "Details": [
            {
              "Date": "2024-04-25T13:26:41.911Z",
              "Country": "UK",
              "Amount": {
                "Amount": "4.68702",
                "Currency": "GBP"
              }
            }
          ]
        }
      ],
      "RemittanceInformation": {
        "Structured": [
          {
            "ReferredDocumentInformation": [
              {
                "Code": "CINV",
                "Issuer": "Issuer01",
                "Number": "Number_01",
                "RelatedDate": "2024-04-25T13:26:41.911Z",
                "LineDetails": [
                  "Line details entry 1"
                ]
              }
            ],
            "ReferredDocumentAmount": "1.00",
            "CreditorReferenceInformation": {
              "Code": "DISP",
              "Issuer": "Issuer01",
              "Reference": "REF_26518"
            },
            "Invoicer": "INVR51856",
            "Invoicee": "INVE5161856",
            "TaxRemittance": "Tax Remittance related information",
            "AdditionalRemittanceInformation": [
              "Free text for additional information"
            ]
          }
        ],
        "Unstructured": [
          "Internal ops code 5120101"
        ]
      }
    },
    "Debtor": {
      "Name": "D Jones",
      "SchemeName": "UK.OBIE.SortCodeAccountNumber",
      "Identification": "08080021325698",
      "SecondaryIdentification": "0002",
      "LEI": "8200007YHFDMEODY1965"
    },
    "SCASupportData": {
      "RequestedSCAExemptionType": "EcommerceGoods",
      "AppliedAuthenticationApproach": "SCA",
      "ReferencePaymentOrderId": "O-611265"
    }
  },
  "Risk": {
    "PaymentContextCode": "EcommerceMerchantInitiatedPayment",
    "ContractPresentIndicator": false,
    "PaymentPurposeCode": "EPAY",
    "BeneficiaryPrepopulatedIndicator": false,
    "BeneficiaryAccountType": "Business",
    "MerchantCustomerIdentification": "053598653254",
    "DeliveryAddress": {
      "AddressLine": [
        "Flat 7",
        "Acacia Lodge"
      ],
      "StreetName": "Acacia Avenue",
      "BuildingNumber": "27",
      "PostCode": "GU31 2ZZ",
      "TownName": "Sparsholt",
      "CountrySubDivision": "Wessex",
      "Country": "GB"
    }
  },
  "Links": {
    "Self": "https://api.alphabank.com/open-banking/v4.0/pisp/domestic-payment-consents/58923"
  },
  "Meta": {}
}
```

<br />
