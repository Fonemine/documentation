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

### 1.2 Accessing MobileForce CPQ

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

Finally, once the quote has all the products and contract attributes, it can now be submitted for approval, using the Submit button, as shown in the screenshot below:

![Quote Submit for Approval](/images/cpq_user_guide_images/QuoteSubmit.png)

A quote can also be further validated, and also saved. This is especially useful if the quote isn't complete. This enables the seller to break the quote creation process into multiple sessions and even collaborate with the customer on the saved quote.

**(d) Approvals Tab** – If your quote requires an approval, Submit for Approval, track Approval Status & History
Once a quote is submitted for approval, a notification (via email) is sent out to the users that are configured (by the CPQ Admin) to approve the quote.
When an approver logs into the MobileForce CPQ system, they get to see, under the **Approvals** Tab, that the quote is pending approval. They are also given a choice to approve, decline, or if they are also the user who created the quote, they are given the ability to cancel the quote. The following screenshot shows the various elements of the approval tab, prior to a quote being approved.


![Approvals Tab](/images/cpq_user_guide_images/ApprovalsTab.png)

Once the approver approves the quote, the Approvals Tab changes and shows that the quote was approved. The following screenshot shows the various elements of the approval tab, after a quote is approved.

![Approvals Tab after a quote has been approved](/images/cpq_user_guide_images/ApprovedTab.png)

**(e) Signature Tab** – If you’d like to incorporate your digital signature in the output PDF document, please include it here along with signatory information
In this tab, the seller can provide their signature, and send the quote to the customer so as to obtain the customer's approval and signature. 
The following screenshot shows the signature tab.

![Signatures Tab](/images/cpq_user_guide_images/SignaturesTab.png)

The MobileForce CPQ system provides built-in digital signature capture, and also integrates with DocuSign for 3rd party signature capture and collaboration.
The following screenshot shows how a digital signature can be easily created and captured by the MobileForce CPQ system.

![Digital Signature capture](/images/cpq_user_guide_images/SignaturesTab.png)




**(f) Generate Docs Tab** – Validate and Save your quote. Then click on Generate Doc button to choose one of the output document templates to generate a professional looking Quote document. The following screenshot shows how you can select from a single-page or a multi-page quote layout. 
The Quote UI Layout determines the exact layout of the created quote. The quote UI Layout can also be customized but this is a CPQ Administrator function so if you need to make changes to the quote layout, please contact your CPQ Administrator.

![Generate Docs UI](/images/cpq_user_guide_images/GenerateDocsUI.png)

Further, if you select a multi-page Quote UI Layout, then you can optionally select specific documents (such as terms and marketing collateral) to include within your quote, as shown in the following screenshot.

![Generate Docs MultiPage](/images/cpq_user_guide_images/GenerateDocsMultiPage.png)

Once the quote documents are generated, they are shown as a list view, on the Generated Docs Tab.
You can view the prepared document online. You can also download it and email it to your customer via your desktop email client or optionally, email it via your DocuSign account. Finally, click on the Save to CRM button to store the quote document and information back in your CRM. All these actions are shown in the screenshot below:

![Generated Docs](/images/cpq_user_guide_images/GeneratedDocs.png)

Each time a quote is saved, a new version of the quote is created. This enables you to keep track of all the versions of the quote. In the screenshot above (under the **Generated Docs** Tab) you can see all the quotes that have been created and saved for a specific deal or opportunity. You can also download any quote and send it using your own email client to the customer.

### 2.1 Create a Quote Video Walkthrough 

For additional details, You can use this full walkthrough video 
https://youtu.be/6_L25kqDq_g

## 3. Quote Actions ## 
Quotes in MobileForce CPQ are rich not only in the data they show, but also in the meta-data that's adorned on a quote, thus enabling a rich set of actions on quotes. In contrast, most CPQ systems present quotes as opaque objects on which not many rich actions can be performed. The following actions on quotes highlight the richness of quotes in MobileForce CPQ.

### 3.1 List View

The list view of Quotes in MobileForce diplays a list of all quotes created for a specific opportunity or at the top level. In the list view, the following actions are supported:
 
 * **Sort on Columns** Each column can be used to sort the list of quotes: quotes are sorted by a column by clicking on the column header.
 * **Reorder Columns** Columns can be dragged and moved left or right, to create a specific order of columns that are shown in the list view of quotes.
 * **Select Columns** Specific columns can be selected for inclusion in the list view.
 * **Export as CSV** The list of quotes can be exported as a csv (including all the columns shown in the view being exported)

The following screenshot shows the above actions through the use of the "settings" in a listview for quotes

![Generated Docs](/images/cpq_user_guide_images/QuoteListViewSettings.png)

### 3.2 Quote Filters

Quotes in CPQ can be filtered using powerful filtering constructs. Quote Filtering is accessed using the filter icon as shown in the following screenshot:

![Generated Docs](/images/cpq_user_guide_images/QuoteFilter.png)

Within quote filters, one can perform the following operations to create filters

* **Group Operations** Filter rules can be grouped using and/or constructs, as shown in the screenshot below:
![Generated Docs](/images/cpq_user_guide_images/FilterStructGroup.png)

* **Filter Rules** Within a group, multiple rules can be specified and combined using and/or constructs as shown below:
![Generated Docs](/images/cpq_user_guide_images/FilterStructRules.png)

* **Filter Rule Fields** Each filter rule can filter on a set of fields as specified by the CPQ Admin in the Summary Table in a Quote UI Layout.
![Generated Docs](/images/cpq_user_guide_images/FilterRuleField.png)

* **Filter Rule Operations** Each field that you want to filter can have the following operations specified on the field values
![Generated Docs](/images/cpq_user_guide_images/FilterRuleOps.png)

Quote Filters can even be shared (or subsequently unshared) by a user with other users, to facilitate ease of viewing of the same set of quotes by different users. This is achieved in the filter UI. Filters can also be copied to enable easy modification and updates to filters. In addition to the user defined filters, MobileForce provides a set of pre-defined global filters that are applicable to any customer quote filtering scenario. These global filters are visible on the top right side of the list view of quotes, and can be used by any user/customer.

### 3.3 Quote Search and Advanced Filters

Quotes can be searched using a simple textual search, made available on top of the list view of quotes. The search values can be values of any of the fields that are visible in the list view.
To support more complex searches, MobileForce datatable screens support advanced search filters.
using which one can specify filters on a per-field basis.  These filters are
context sensitive based on the type the field.  Additionally,
these filters can be combined with boolean OR and AND operators.

Mobileforce allows one to save and reuse one's search filters.  One can save both personal and shared
search filters, where shared search filters are visible by all.  Only users with sufficient permission
can save shared search filters.  Saved search filters also remember the displayed columns as part of the filter.

## Configuration

Search filters can be configured by CPQ Configuration properties such as 'search-filter-enable' which enables search filter for datatable screens.

All supported CPQ Configuration properties are shown below.

| Property | Default | Description |
| --- | --- | --- |
| search-filter-enable | 0 | If 1, enable search filters. |
| search-filter-update-shared | 0 | If 1, allow the saving of shared search filters. |
| search-filter-action | list | (Deprecated)  Specifies with columns that are filterable.  Can be 'list' or 'read'.  If 'list' only columns visible in the list view are filterable.  If 'read', only columns visible on the view screen are filterable.  This property is ignored for AG Grid tables.  For AG grid tables, all selectable columns are filterable. |

## UI

When advanced search filters are enabled a funnel icon is displayed to the right of the search box, clicking on which
opens the search filter dialog.  This dialog allows creation and selection of search filters.

All search filters are named.  Users a can select an existing search filter or create a new one.  Search filters
can also be copied, renamed or deleted.

There are two kinds of search filters: user and shared.  User search filters are private to the user.  Only that
user can view or edit those filters.  User search filters are saved as part of the user's configuration.  Shared
search filters are visible by all users.  Only users with the appropriate permissions can create shared search
filters.  The search filter name dropwdown first displays all user filters, then all shared filters.

Search filters are per table.  That is, different tables have different saved search filters.  User search filter
names and shared search filter names must be unique per table.  However,  a user search filter and
shared search filter can have the same name.

One can specify a list of conditional rules to filter by for a search filter.  Each rule applies to a single
table column.  The conditional operators allowed in a rule is based on the column's type.  The allowed operators
per column type are:

| Operator | Allowed Types | Description |
| --- | --- | --- |
| equals | text, picklist, numeric, date, time, datetime | True if the given field is equal to the given value |
| not equals | text, picklist, numeric, date, time, datetime | True if the given field is not-equal to the given value |
| empty | text, picklist, numeric, date, time, datetime | True if the given field is empty ('') |
| not empty | text, picklist, numeric, date, time, datetime | True if the given field is not empty ('') |
| contains | text | True if the given field contains the given string value |
| not contains | text | True if the given field does not contain the given string value |
| starts with | text | True if the given field starts with the given string value |
| not starts with | text | True if the given field does not start with the given string value |
| ends with | text | True if the given field ends with the given string value |
| not ends with | text | True if the given field does not end with the given string value |
| less than | numeric, date, time, datetime | True if the given field is less than the given value |
| less equal | numeric, date, time, datetime | True if the given field is less than or equal to the given value |
| greater than | numeric, date, time, datetime | True if the given field is greater than the given value |
| greater equal | numeric, date, time, datetime | True if the given field is greater than or equal to the given value |
| between | numeric, date, time, datetime | True if the given field is between the two given values |
| not between | numeric, date, time, datetime | True if the given field is not between the two given values |
| today | date, datetime | True if the given field's date is today |
| last N days | date, datetime | True if the given field's date occurs in the last N days, where N is the given value |
| next N days | date, datetime | True if the given field's date occurs in the next N days, where N is the given value |
| older than N days | date, datetime | True if the given field's date occurs before N days agoe, where N is the given value |

The entered values for each rule are also restricted by the column's type.  For example, one must select a picklist
value for picklist column, or a date picker will be displayed for a date column.

Rules can be grouped together by boolean conditions: AND or OR.  For the AND group, the filter is true if only all
rules are true.  For the OR group, the filter is true if just one of the rules are true.  One can nest conditional
groups for more complex boolean operations.

When one saves a search filter, one can also optionally save the displayed columns along with it.  If a
search filter has saved columns, selecting that filter will also automatically set the table's columns to
the saved columns.


## 4. CPQ Terminology ## 

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



