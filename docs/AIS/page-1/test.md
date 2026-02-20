---
title: Test
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

| Situation                                                                                                                                                                                                | Request                               | Response          |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------- | ----------------- |
| A TPP attempts to retrieve a payment with a DomesticPaymentId that does not exist                                                                                                                        | GET /domestic-payments/1001           | 400 (Bad Request) |
| A TPP attempts to retrieve a resource that is not defined                                                                                                                                                | GET /bulk                             | 404 (Not Found)   |
| A TPP attempts to retrieve a resource that is in the specification, but not implemented by the ASPSP. e.g., an ASPSP has chosen not to implement the status API endpoint for domestic-scheduled-payments | GET /domestic-scheduled-payments/1002 | 404 (Not Found)   |
| A TPP attempts to retrieve standing orders for an AccountId that exists, but does not have any standing orders                                                                                           | GET /accounts/1000/standing-orders    | pre removed       |
