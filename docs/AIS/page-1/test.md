---
title: Test
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

<Table>
  <thead>
    <tr>
      <th>
        Situation
      </th>

      <th>
        Request
      </th>

      <th>
        Response
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        A TPP attempts to retrieve a payment with a DomesticPaymentId that does not exist
      </td>

      <td>
        GET /domestic-payments/1001
      </td>

      <td>
        400 (Bad Request)
      </td>
    </tr>

    <tr>
      <td>
        A TPP attempts to retrieve a resource that is not defined
      </td>

      <td>
        GET /bulk
      </td>

      <td>
        404 (Not Found)
      </td>
    </tr>

    <tr>
      <td>
        A TPP attempts to retrieve a resource that is in the specification, but not implemented by the ASPSP. e.g., an ASPSP has chosen not to implement the status API endpoint for domestic-scheduled-payments
      </td>

      <td>
        GET /domestic-scheduled-payments/1002
      </td>

      <td>
        404 (Not Found)
      </td>
    </tr>

    <tr>
      <td>
        A TPP attempts to retrieve standing orders for an AccountId that exists, but does not have any standing orders
      </td>

      <td>
        GET /accounts/1000/standing-orders
      </td>

      <td>
        `{
          "Data": {
            "StandingOrder": []
          },
          "Links": {
            "Self": "https://api.alphabank.com/open-banking/v4.0/aisp/accounts/1000/standing-orders/"
          },
          "Meta": {
            "TotalPages": 1
          }
        }`
      </td>
    </tr>
  </tbody>
</Table>
