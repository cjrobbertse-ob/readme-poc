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
title="Payment authorisation sequence"
openLabel="View payment sequence"
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
