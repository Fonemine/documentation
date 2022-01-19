# Configure, Price, Quote End-user Guide

This document is intended for use by the sellers within a Business: these are typically the sales users who are responsible for interacting with a sales prospect and for creating a quote, sending it to the prospect, and getting budgetary approval from the prospect.

## 1. Getting Started

Here's how one starts using the MobileForce CPQ.

### 1.1 The CRM Context
MobileForce CPQ is used in the sales process, so it is natural to expect the CPQ Solution to be accessible from within the CRM that sellers are most familiar with. Indeed, the MobileForce CPQ is "installed" within the UI for most popular CRMs such as SugarCRM, Hubspot, and ZenDesk. More so, the MobileForce CPQ UI has the same look and feel, color schemes, layout, and user experience as the CRM it is embedded in, making it easy to use for sellers who are already familiar with their own CRM.

This document assumes that an Administrator (either a Sales or SalesOps admin, or an IT admin) has already installed, configured, and set up the MobileForce CPQ within the CRM. To verify that you have access to the MobileForce CPQ Solution from within your CRM, you can go on Zendesk to **Settings --> Integrations --> Apps** and you'll see MobileForce CPQ, or on Hupspot, you can go to **Settings --> Integrations --> Connected Apps** and verify that you can see MobileForce CPQ. Similarly, on SugarCRM, you can go to **Settings --> Developer Tools --> Module Loader** to verify that MobileForce CPQ has been installed on your instance.

The following screenshots show MobileForce CPQ installed within a CRM. If you don't find the MobileForce CRM installed on your CRM, please contact your CRM Administrator.

![MobileForce CPQ in Zendesk](/images/cpq_user_guide_images/ZendeskSettingsMF.png)

![MobileForce CPQ in Hubspot](/images/cpq_user_guide_images/HubspotSettingsMF.png)

The information that MobileForce CPQ automatically pulls from a CRM include Deals (or Opportunities), Contacts, and Customer Information. The power of MobileForce CPQ lies in its seamless integration with a variety of CRM systems for read as well as write of a quote information back to the CRM when a quote is completed. 

When you access the MobileForce CPQ for the first time, you'll receive a pop-up alert requesting you to confirm the integration between your CRM and MobileForce. Please accept this request in order for MobileForce CPQ to access (for read and write) CRM objects. From then onwards, information flows seamlessly between your CRM and MobileForce CPQ. Please note that both your CRM and MobileForce CPQ are on their specific clouds and none of your CRM information persists on the MobileForce side, thus providing you with a secure CPQ use scenario.

### 1.2 Accessing the MobileForce CPQ

The MobileForce CPQ Solution is accessed from within the same CRM that is already being used by the seller. The seller just logs into their CRM like they always do using their CRM Credentials. The MobileForce CPQ magically appears within the  CRM UI, either as a top level Tab (e.g., SugarCRM), or as a card on the right side panel (e.g., Hubspot, Zendesk). Of course, features of the MobileForce CPQ can be controlled by setting up roles, so what a seller sees within their CPQ Solution depends on their own role in their CRM setup and what permissions that role has to create, list, read, update, or delete. 

From within a CRM, there are two ways to access the MobileForce CPQ 

**(a)** As a standalone CPQ solution at the top level. Typically, MobileForce CPQ shows a list of previously created quotes and gives you the option to edit or view an existing quote, or to create a new quote. When creating a new quote this way, the customer and contact information will need to be filled in, because the quote isn't being created in the context of an existing deal or opportunity.

**(b)** Contextually, from within the CRM Opportunity (SugarCRM, SalesForce) or Deal (Hubspot, Zendesk). This access makes sense since the process of creating a quote starts from an opportunity, where the account and contact info are automatically pulled into the quote  by MobileForce CPQ, so as to provide the context for the quote.  What fields are automatically pre-filled in various Quote Tabs is determined by the CPQ Setup, so if you would like specific fields to be pre-filled by specific CRM attributes, please talk with your CRM or CPQ Administrator.

The following screenshot shows these two ways of accessing the MobileForce CPQ:

![Accessing MobileForce CPQ](/images/cpq_user_guide_images/AccessingMFCPQ.png)
The setup and administration of MobileForce CPQ is an admin function and is outside the scope of this document.

### 1.3 MobileForce CPQ UI 

The following screenshot shows the MobileForce CPQ UI embedded within a Sugar CRM instance. The CPQ User Interface shows a list of quotes that have previously been created. The actions available at the top level of the MobileForce CPQ UI are (a) to view/edit an existing quote or (b) to create a new quote.

![CPQ UI in SugarCRM](/images/cpq_user_guide_images/CPQUI.png)

Similarly, the following screenshot shows the MobileForce CPQ UI embedded within a Hubspot instance. The CPQ User Interface shows a list of quotes that have previously been created. The actions available at the top level of the MobileForce CPQ UI are (a) to view/edit an existing quote or (b) to create a new quote.

![CPQ UI in Hubspot](/images/cpq_user_guide_images/HubSpotCPQQuoteList.png)


## 2 Creating a Quote

When creating a quote, if you  start from a deal or an opportunity, the quote will auto-populate many fields of the customer tab using information from your CRM.
The Quote creation process in MobileForce is made simple via a wizard which consists of multiple tabs that are filled in left to right order. The left to right order of filling information in the quote creation process captures the quote workflow, and can be customized to use as few or as many tabs as your business workflow mandates. Similarly the fields that are shown in individual tabs can also be customized in the CPQ Setup (talk with your CRM/CPQ Admin if you need specific CRM Attributes to show up as fields in your quoting process and hence in your quote.

At every stage of the quoting process, you can validate the data you've entered, as well as save the partial quote that you've completed so far, thus finding and fixing errors as they occur, as well as giving you the flexibility to create a quote in multiple sessions (rather than all at once).

**Creating a CPQ Quote**: Here are some easy steps that you can follow to quickly start quoting with the MobileForce CPQ application. 
 
**(a) Add/Create** Click Add or Create to start a new CPQ Session or start a new CPQ Session from a Deal or Opportunity record page in your CRM

The following screenshot shows how you can start a new CPQ session directly from a Deal in Zendesk. Please note that Zendesk provides two UI Options for accessing the CPQ: (a) as a popup window or (b) as a new browser tab. These two ways are identical except for the UI Placement. Some users prever to see the surrounding Deal context when creating a quote, whereas others prefer the CPQ quote to be a completely new tab within their browser.

![Add a new CPQ Quote in Zendesk](/images/cpq_user_guide_images/ZendeskAddQuote.png)

A variation of the same experience can be seen in SugarCRM where within a specific opportunity, you can **Create** a CPQ quote. The following screenshot shows this.

![Add a new CPQ Quote in SugarCRM](/images/cpq_user_guide_images/SugarCRMCreateQuote.png)


**(b) Customer Tab** – Fill in customer information as required. Many of the fields may be auto-populated from your CRM if you started from an opportunity or a deal. You can always over-ride the pre-filled fields with values specific to your quote scenario. The Customer Tab in MobileForce CPQ on SugarCRM looks as follows: 

![Customer Tab in CPQ Quote in SugarCRM](/images/cpq_user_guide_images/SugarCRMCustomerTab.png)

The Customer Tab in MobileForce CPQ on Zendesk looks quite similar:

![Customer Tab in CPQ Quote in SugarCRM](/images/cpq_user_guide_images/ZendeskCustomerTab.png)



**(c) Quote Tab** – Choose a Price Book, enter contractual term attributes and add Product & Service Line Items

The quote tab looks as follows:

![Quote Tab in CPQ Quote in SugarCRM](/images/cpq_user_guide_images/ZendeskQuoteTab.png)

Once the Price Book, and Contract Term attributes are selected, the real work of the CPQ begins with the selection of Product (and Service) Line Items.

The action of adding Line Items brings up the product catalog displayed as hierarchical product categories from which you can drill down and select specific products to add to the line items, as shown inthe following screensho

![Quote Tab in CPQ Quote in SugarCRM](/images/cpq_user_guide_images/ZendeskLineItemProductSelection.png)

When adding products in line items, you can not only browse products (via the Product Categories hierarchy as shown above) but also search for products in the search bar. In addition, products can be laid out in a list view (the default) or you can change the layout to a grid view. The following screenshot shows these features.

![Search Products and Product Layouts](/images/cpq_user_guide_images/ProductSearchView.png)

Once products are selected and added to the Line Items, the Quote now contains one or more line items (one for each product that was added). You can now specify the quantity and discount for each line item in the quote.

The following screenshot shows a quote with two line items.

![Search Products and Product Layouts](/images/cpq_user_guide_images/QuoteLineItems.png)

At this stage you can "validate" the quote by clicking on the validate button on the top right. The process of quote validation runs the various rules for quotes to ensure the correct set of products (with correct quantities, discount and combinations) are included in the quote. Validation can also result in additional line items being added (if for example, a product rule that specified that including a product necessitated adding a warranty line item). Product validation rules prevent mistakes from being made when creating quotes. The set up of Product rules that may include configuration rules (for configurable products), pricing rules, and discounting rules, all of which is done by the CRM/CPQ Administrator ahead of time. 

The Quote Tab also provides action buttons on the far right, that enable the line items to be re-ordered by moving them up or down. Further, line items can also be copied for easy duplication. See the screenshot below.

![Action buttons for Line Items in Quote](/images/cpq_user_guide_images/LineItemsAction.png)


**(d) Approvals Tab** – If your quote requires an approval, Submit for Approval, track Approval Status & History


**(e) Signature Tab** – If you’d like to incorporate your digital signature in the output PDF document, please include it here along with signatory information

**(f) Generate Docs Tab** – Validate and Save your quote. Then click on Generate Doc button to choose one of the output document templates to generate a professional looking Quote document. View the prepared document online. Download it and email it to your customer via your desktop email client or optionally, email it via your DocuSign account. Finally, click on the Save to CRM button to store the quote document and information in your CRM. 


### 2.1 Create a Quote Video Walkthrough 

For additional details, You can use this full walkthrough video 
https://youtu.be/6_L25kqDq_g

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

* **Price Book** The basic list of products and their prices, for a specific country or geography or region. Price books can also be specific to specific currencies or even specific customer segments or customers. Price Books are the starting point for CPQ Activities.

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



