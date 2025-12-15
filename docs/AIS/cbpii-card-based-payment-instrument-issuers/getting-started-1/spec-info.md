---
title: Spec info
excerpt: >-
  Placeholder, with existing section headings.  More likely this will go into
  either Recipes or API Reference sections
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
**Overview**

* Document Structure - shouldn't need this if layout is sufficiently intuitive
* Resources

**Basics**

* Overview
  * Steps
  * Sequence Diagram
* Idempotency
* Release Management
  * Funds Confirmation Consent
    * POST
    * GET
    * DELETE
  * Funds Confirmation Resource
    * POST

**Security & Access Control**

* Scopes
* Grants Types
* Consent Authorisation
* Consent Elements
* Funds Confirmation Consent Status
* Consent Re-authentication
* Consent Revocation

**Data Model** - Don't need this as a separate section, as all classes etc are included in swagger

* Reused Classes
  * OBProxy1
    * Data Dictionary

**Swagger**

**Usage Examples**

<Cards columns={4}>
  <Card title="Warning" href="https://readme.com" icon="fa-exclamation-triangle" target="_blank">
    You must ensure API credentials are stored securely
  </Card>

  <Card title="Useful Info" icon="fa-info-circle">
    **ASPSP Developer portals will contain details of any additional statuses the ASPSP supports**
  </Card>

  <Card title="Tip" icon="fa-lightbulb">
    > Including TRIs in the Risk component will reduce the risk of false positive checks that slow down/reject payments
  </Card>

  <Card title="Find out more" icon="fa-question-circle">
    **Check the CodeSet repository for the full range of options**
  </Card>
</Cards>
