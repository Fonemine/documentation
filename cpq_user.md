# Configure, Price, Quote End-user Guide

This document is intended for use by the sellers within a Business: these are typically the sales users who are responsible for interacting with a sales prospect and for creating a quote, sending it to the prospect, and getting budgetary approval from the prospect.

## 1. Getting Started

Here's how one starts using the MobileForce CPQ.

### 1.1 The CRM Context
MobileForce CPQ is used in the sales process, so it is natural to expect the CPQ Solution to be accessible from within the CRM that sellers are most familiar with. Indeed, the MobileForce CPQ is "installed" within the UI for most popular CRMs such as SugarCRM, Hubspot, and ZenDesk. More so, the MobileForce CPQ UI has the same look and feel, color schemes, layout, and user experience as the CRM it is embedded in, making it easy to use for sellers who are already familiar with their own CRM.

This document assumes that an Administrator (either a Sales or SalesOps admin, or an IT admin) has already installed, configured, and set up the MobileForce CPQ within the CRM.

### 1.2 Accessing the MobileForce CPQ

The MobileForce CPQ Solution is accessed from within the same CRM that is already being used by the seller. The seller just logs into their CRM like they always do using their CRM Credentials. The MobileForce CPQ magically appears within the  CRM UI, either as a top level Tab (e.g., SugarCRM), or as a card on the right side panel (e.g., Hubspot, Zendesk). Of course, features of the MobileForce CPQ can be controlled by setting up roles, so what a seller sees within their CPQ Solution depends on their own role in their CRM setup and what permissions that role has to create, list, read, update, or delete. 

From within a CRM, there are two ways to access the MobileForce CPQ 

**(a)** As a standalone CPQ solution at the top level.

**(b)** Contextually, from within the CRM Opportunity (SugarCRM, SalesForce) or Deal (Hubspot, Zendesk). This access makes sense since the process of creating a quote starts from an opportunity, where the account and contact info are pulled into the quote automatically by MobileForce CPQ, so as to provide the context for the quote.  

The following screenshot shows these two ways of accessing the MobileForce CPQ:

![Accessing MobileForce CPQ](/images/cpq_user_guide_images/AccessingMFCPQ.png)
The setup and administration of MobileForce CPQ is an admin function and is outside the scope of this document.

### 1.3 MobileForce CPQ UI 


## CPQ Terminology ## 

The following objects and terms are often mentioned, when using MobileForce CPQ.

* **ACL** Access Control List,typically tied to a CPQ object or a rule, which indicates which user-role can access the object.

* **Active** Indicates whether (or not) an object can be used in the CPQ system.

* **Approval Rules** Typically businesses require special product/pricing and discounting to be approved prior to creation of a quote. Approvals involve an organizational chain of approvers such as a Director and/or a Vice President of Sales. Approval rules provide the logic behind who can approve special pricing/discounting. Approval rules are specified as a part of the Product, for configurable products (aka products with nested child products), but are specified in the quote for most other products.

* **Configurable Products** have attributes, or nested products within them. In contrast, Simple products have no attributes nor nested products. Configurable products often require a special UI to "configure" their attributes or the nested products therein.

* **Discount Unit** indicates whether the discount is a fixed amount or dependent on the price (i.e., a percentage of the price). Discount Unit can be "Amount" or "Percent" or "Both".

* **Editable** Whether or not the CPQ User Interface allows an object or an attribute to be modified.

* **Effective Date** The date on which the object or rule takes effect. Prior to the effective date, the object cannot be used in the CPQ system.

* **Expiration Date** The date after which the object or rule can no longer be used in the CPQ system.

* **Expressions**  extend the automation capabilities of the CPQ Solution in powerful ways that otherwise could only be achieved by an enterprise software developer. Expressions enable the end user to create powerful automation features in several  parts of MobileForce CPQ, without the burdon of having to learn to program.

* **Generated Docs** The output of CPQ is one or more documents, professionally laid out as a sales proposal to wow the customer. These documents could contain marketing collateral, legal t&c, and even brocures and product literature.

* **Line Item** An entry that appears on a separate line in the Quote and describes the quantity, prices, and the discounts specific to a single product or service. A quote consists of many line items, one for each product or service being sold in the quote.

* **Price Book** The basic list of products and their prices, for a specific country or geography or region. Price Books are the starting point for CPQ Activities.

* **Price Recurrence** In today's world of flexible pricing, one important characteristic of any price is "how often a user is charged".Price recurrence sets the time period for which the Product is charged to the Customer. The MobileForce CPQ Solution offers flexibility in specifying Price recurrence  from "one time" (i.e., no recurrence) to a sliding recurrence scale:  from "each minute", all the way to "yearly".

* **Price Method** Given a product price and a product quantity, the Price Method is used to compute the product's subtotal from the product's quantity. MobileForce CPQ offers a rich set of pricing methods including  Flat Pricing, Per-Unit, Volume, Tiered, and Block Pricing.

* **Price Tier** A tier represents a range of quantity for which a specific indicated price applies. Tiers are used for Volume, Tiered, and Block Price Methods

* **Pricing Rules** control what pricing changes must be made for Product/Service items in the  Quote. An example of a pricing rule is to add a special discount automatically to a quote at the end of the month.

* **Product Rules** enable an action (such as adding a discount or even adding another product to a quote) to be taken when a condition (such as adding a product to a quote) is met.

* **Product Approval Rules** Specific kinds of Approval Rules, that are specified as a part of the Product, often for configurable products (aka products with nested child products).

* **Product Attributes** Every product can be described using properties such as details, subjective descriptions, or even intangible characteristics. Such properties are collectively called attributes, and help users compare and choose products.

* **Product Categories** When you sell hundreds of products, its almost always a good idea to organize them in hierarchies; Product Categories help organize the products and services you sell, based on shared or common characteristics.

* **Product Configuration Rules** Rules that govern what types of Product/Service items can be added together in the Line Item Tables and include restrictions on such additions

* **Product UI Layouts**  Configurable products are configured via a UI that enables the selection and validation of their parts and sub-products. The specification of this UI is done via Product UI Layouts.

* **Quantity Step** Indicates the number of units that are bundled together. So, if the Quantity Step is 10, then the product can be sold in units of 10, i.e., 10, 20, 30, and so on.

* **Quote** In MobileForce CPQ, a quote consists (a) a Quote Template and (b) a Quote UI Layout.

* **Quote Template** describes the structure, state and logic of what products/services can go into a Quote and how their pricing is approved.

* **Quote UI Layout** The UI and Workflow that guides the end-user to create a valid quote by going  through the  Configure, Price, Quote, Approvals and Document Generation workflow as intuitively and efficiently as possible

* **Sales Quotes** (or just **Quotes**)

* **Templates** The MobileForce CPQ system provides a collection of re-usable document structures (or Templates) which are used as a boiler-plate to customize various parts of the CPQ process such as (a) Approval Emails for requesting approvals, approving or even rejecting quotes (b) Document Templates for creating quotes out of the Line Items and other related documents.

* **UoM** Unit of Measurement is used to describe the magnitude of any quantity. Any other quantity can be expressed as a multiple of the unit of measurement.

**Creating a CPQ Quote**: The following are the easy steps you can follow to quickly start quoting with the CPQ application.
 
Click Add to start a new CPQ Session or start a new CPQ Session from a Deal or Opportunity record page in your CRM
Customer Tab – Fill in customer information as required. Some of the fields may be auto-populated from your CRM.
Quote Tab – Choose a Price Book, enter contractual term attributes and add Product & Service Line Items
Approvals Tab – If your quote requires an approval, Submit for Approval, track Approval Status & History
Signature Tab – If you’d like to incorporate your digital signature in the output PDF document, please include it here along with signatory information
Generate Docs Tab – Validate and Save your quote. Then click on Generate Doc button to choose one of the output document templates to generate a professional looking Quote document. View the prepared document online. Download it and email it to your customer via your desktop email client or optionally, email it via your DocuSign account. Finally, click on the Save to CRM button to store the quote document and information in your CRM.

## 1. Price Books

### 1.1. Products, Configurations and Rules

For additional details, You can use this full walkthrough video 
https://youtu.be/6_L25kqDq_g

