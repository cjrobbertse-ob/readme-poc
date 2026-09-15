---
title: temp
deprecated: false
hidden: false
metadata:
  robots: index
---
#### Sequence diagram

![Sequence diagram for payment consent, authorisation, funds confirmation, and payment submission](https://files.readme.io/87b24b49d9c2ca0becd78890e9bcb916e24fe99fb747f7fcc2a7cf020258b326-image.png)

<br />

<MermaidDiagramButton 
title="Missing or Expired Access Token"
openLabel="View Token Issues Sequence Diagram"
code={`
sequenceDiagram
    participant PSU as PSU
    participant AISP as AISP
    participant ASPSP_Authorisation_Server as ASPSP Authorisation Server
    participant ASPSP_Resource_Server as ASPSP Resource Server

    alt Request data with a missing or expired access-token
    AISP->>ASPSP_Resource_Server: Establish TLS 1.2 MA (mutual)
    AISP->>ASPSP_Resource_Server: GET /accounts
    ASPSP_Resource_Server->>AISP: HTTP 401 (Unauthorized)

    AISP->>ASPSP_Resource_Server: GET /accounts/{AccountId}/transactions
    ASPSP_Resource_Server->>AISP: HTTP 401 (Unauthorized)

    end
`} />

<br />

<MermaidDiagramButton 
title="Missing or Expired Access Token"
openLabel="View Token Issues Sequence Diagram"
code={`
sequenceDiagram
    participant PSU as PSU
    participant PISP as PISP
    participant ASPSP_Authorisation_Server as ASPSP Authorisation Server
    participant ASPSP_Resource_Server as ASPSP Resource Server

    Note over PSU,ASPSP_Resource_Server: Step 1: Agree Payment-Order Initiation

    PSU->>PISP: Agree payment-order initiation request

    Note over PSU,ASPSP_Resource_Server: Setup Payment-Order Consent

    PISP->>ASPSP_Authorisation_Server: Establish TLS 1.2 MA (mutual)
    PISP->>ASPSP_Authorisation_Server: Initiate Client Credentials Grant
    ASPSP_Authorisation_Server->>PISP: access-token
    PISP->>ASPSP_Resource_Server: Establish TLS 1.2 MA (mutual)
    PISP->>ASPSP_Resource_Server: POST /payment-order-consents
    Note over ASPSP_Resource_Server: Consent Status: AWAU
    ASPSP_Resource_Server->>PISP: HTTP 201 (Created),  ConsentId

    Note over PSU,ASPSP_Resource_Server: Step 3: Authorize Consent

    alt Redirection (Using authorization code grant)
    PISP->>PSU: HTTP 302 (Found), Redirect (ConsentId)
    PSU->>ASPSP_Authorisation_Server: Follow redirect (ConsentId)
    PSU->>ASPSP_Authorisation_Server: authenticate (mutual)
    PSU->>ASPSP_Authorisation_Server: SCA if required (mutual)
    PSU->>ASPSP_Authorisation_Server: Select debtor account if required (mutual)
    Note over ASPSP_Resource_Server: Consent Status: AUTH
    ASPSP_Authorisation_Server->>PSU: HTTP 302 (Found), Redirect (authorization-code)
    PSU->>PISP: Follow redirect (authorization-code)
    PISP->>ASPSP_Authorisation_Server: Establish TLS 1.2 MA (mutual)
    PISP->>ASPSP_Authorisation_Server: Exchange authorization-code for access token
    ASPSP_Authorisation_Server->>PISP: access-token
    else Decoupled (Using CIBA)
    PISP->>ASPSP_Authorisation_Server: POST /bc-authorize (login_hint_token)
    ASPSP_Authorisation_Server->>PISP: OK

    PSU->>ASPSP_Authorisation_Server: Authorise (Consent Id)
    PSU->>ASPSP_Authorisation_Server: authenticate (mutual)
    PSU->>ASPSP_Authorisation_Server: SCA if required (mutual)
    PSU->>ASPSP_Authorisation_Server: select accounts (mutual)
    Note over ASPSP_Resource_Server: Consent Status: AUTH

    alt Using callback
    ASPSP_Authorisation_Server->>PISP: Callback (authorization-code)
    PISP->>ASPSP_Authorisation_Server: Establish TLS 1.2 MA (mutual)
    PISP->>ASPSP_Authorisation_Server: Exchange authorization-code for access token
    ASPSP_Authorisation_Server->>PISP: access-token
    else Using polling
    PISP->>ASPSP_Authorisation_Server: Establish TLS 1.2 MA (mutual)
    PISP->>ASPSP_Authorisation_Server: Poll at /token using auth-req-id
    ASPSP_Authorisation_Server->>PISP: access-token
    end
    end


    Note over PSU,ASPSP_Resource_Server: Step 4: Confirm Funds (Domestic and International Single Immediate Payments Only)

    opt Optional
    PISP->>ASPSP_Resource_Server: Establish TLS 1.2 MA (mutual)
    PISP->>ASPSP_Resource_Server: GET /payment-order-consents/{ConsentId}/funds-confirmation
    ASPSP_Resource_Server->>PISP: HTTP 200 (OK) funds-confirmation resource

    end

    Note over PSU,ASPSP_Resource_Server: Step 5: Create Payment-Order

    PISP->>ASPSP_Resource_Server: Establish TLS 1.2 MA (mutual)
    PISP->>ASPSP_Resource_Server: POST /payment-orders
    alt Multiauthorise Payment Order
    Note over ASPSP_Resource_Server: Multiauthoriation Status: AWAF
    Note over ASPSP_Resource_Server: Multiauthoriation Status: AUTH
    end
    Note over ASPSP_Resource_Server: Consent Status: COND
    alt Immediate Payment
    Note over ASPSP_Resource_Server: Payment Status: RCVD
    end
    ASPSP_Resource_Server->>PISP: HTTP 201 (Created), Payment-Order Id

    Note over PSU,ASPSP_Resource_Server: Step 6: Get Payment-Order-Consent/Payment-Order/Payment-details Status

    opt payment-order-consent
    PISP->>ASPSP_Resource_Server: Establish TLS 1.2 MA (mutual)
    PISP->>ASPSP_Resource_Server: GET /payment-order-consents/{ConsentId}
    alt Immediate
    Note over ASPSP_Resource_Server: Consent Status: AWAU
    Note over ASPSP_Resource_Server: Consent Status: AUTH
    Note over ASPSP_Resource_Server: Consent Status: RJCT
    end
    ASPSP_Resource_Server->>PISP: HTTP 200 (OK) payment-order-consent resource
    end

    opt payment-order
    PISP->>ASPSP_Resource_Server: Establish TLS 1.2 MA (mutual)
    PISP->>ASPSP_Resource_Server: GET /payment-orders/{Payment-Order Id}
    alt Immediate
    Note over ASPSP_Resource_Server: Payment Status: RCVD
    Note over ASPSP_Resource_Server: Payment Status: PDNG
    Note over ASPSP_Resource_Server: Payment Status: ACTC or PATC
    Note over ASPSP_Resource_Server: Payment Status: ACCP
    Note over ASPSP_Resource_Server: Payment Status: ACFC
    Note over ASPSP_Resource_Server: Payment Status: ACSP
    Note over ASPSP_Resource_Server: Payment Status: ACWC
    Note over ASPSP_Resource_Server: Payment Status: ACSC
    Note over ASPSP_Resource_Server: Payment Status: BLCK
    Note over ASPSP_Resource_Server: Payment Status: ACWP
    Note over ASPSP_Resource_Server: Payment Status: ACCC
    Note over ASPSP_Resource_Server: Payment Status: RJCT
    end
    alt Additional for FDP and SO
    Note over ASPSP_Resource_Server: Payment Status: CANC
    end
    ASPSP_Resource_Server->>PISP: HTTP 200 (OK) payment-order resource
    end

    opt payment-details
    PISP->>ASPSP_Resource_Server: Establish TLS 1.2 MA (mutual)
    PISP->>ASPSP_Resource_Server: GET /payment-orders/{Payment-Order Id}/payment-details
    alt Immediate
    Note over ASPSP_Resource_Server: Payment Status: RCVD
    Note over ASPSP_Resource_Server: Payment Status: PDNG
    Note over ASPSP_Resource_Server: Payment Status: ACTC or PATC
    Note over ASPSP_Resource_Server: Payment Status: ACCP
    Note over ASPSP_Resource_Server: Payment Status: ACFC
    Note over ASPSP_Resource_Server: Payment Status: ACSP
    Note over ASPSP_Resource_Server: Payment Status: ACWC
    Note over ASPSP_Resource_Server: Payment Status: ACSC
    Note over ASPSP_Resource_Server: Payment Status: BLCK
    Note over ASPSP_Resource_Server: Payment Status: ACWP
    Note over ASPSP_Resource_Server: Payment Status: ACCC
    Note over ASPSP_Resource_Server: Payment Status: RJCT
    end
    alt Additional for FDP and SO
    Note over ASPSP_Resource_Server: Payment Status: CANC
    end
    ASPSP_Resource_Server->>PISP: HTTP 200 (OK) payment-details resource
    end
`} />
