---
title: Test
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

<Table align={["left","left","left"]}>
  <thead>
    <tr>
      <th style={{ textAlign: "left" }}>
        Situation
      </th>

      <th style={{ textAlign: "left" }}>
        Request
      </th>

      <th style={{ textAlign: "left" }}>
        Response
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td style={{ textAlign: "left" }}>
        A TPP attempts to retrieve a payment with a DomesticPaymentId that does not exist
      </td>

      <td style={{ textAlign: "left" }}>
        GET /domestic-payments/1001
      </td>

      <td style={{ textAlign: "left" }}>
        400 (Bad Request)
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        A TPP attempts to retrieve a resource that is not defined
      </td>

      <td style={{ textAlign: "left" }}>
        GET /bulk
      </td>

      <td style={{ textAlign: "left" }}>
        404 (Not Found)
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        A TPP attempts to retrieve a resource that is in the specification, but not implemented by the ASPSP. e.g., an ASPSP has chosen not to implement the status API endpoint for domestic-scheduled-payments
      </td>

      <td style={{ textAlign: "left" }}>
        GET /domestic-scheduled-payments/1002
      </td>

      <td style={{ textAlign: "left" }}>
        404 (Not Found)
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        A TPP attempts to retrieve standing orders for an AccountId that exists, but does not have any standing orders
      </td>

      <td style={{ textAlign: "left" }}>
        GET /accounts/1000/standing-orders
      </td>

      <td style={{ textAlign: "left" }}>
        <br />
      </td>
    </tr>
  </tbody>
</Table>

<br />

<br />

<pre>200 OK<br />{"{"}<br />"Data": {"{"}<br />    "StandingOrder": []<br />  {"}"},<br />  "Links": {"{"}<br />    "Self": "https://api.alphabank.com/open-banking/v4.0/aisp/accounts/1000/standing-orders/"<br />  {"}"},<br />  "Meta": {"{"}<br />    "TotalPages": 1<br />  {"}"}<br />{"}"}</pre>

<br />
