**Intended Audience:**  This document is intended for use by an **Administrator**: as such it provides a description of steps to be taken by an Administrator before the CPQ software can be used by Sales and Service teams (referred to jointly as the *Seller*) . In order to use this CPQ Admin Guide, you must have  control of (i.e., knowledge and access and update to) (a) Price books: reflecting the currency and the geographies in which you sell your products (b) Product Categories (c) Products (d) Pricing (e) Sales Quotes and Proposals that are typically sent to customers (f) Marketing and Legal elements to be included in Sales Quotes. (g) Pricing rules and Approval rules: for special pricing (h) Users with Email Addresses & Roles

# Configure, Price, Quote Admin Guide

An important aspect of the sales process for any business is the systematization of the processes encompassing pricing of products or services that the business sells. In a typical sales process, setting a price for a product not only impacts the profit margins and market share, it also streamlines the process of product discounts and uplifts in response to market conditions. The basic list of products and their prices is a Price Book, often the starting point of all CPQ systems.

This document first describes the Quick Start Setup sequence of steps that an Administrator needs to perform, in order to enable the rest of the organization to start using the CPQ systems. Then the document goes into details of the CPQ Administration.

## Setup and Quick Start to Administering your CPQ
As a best practice, it behooves an Administrator to perform the following steps *in order*, so as to best set up the CPQ Software.

1. **Create Price Books**: typically one, per geography/currency where you sell your products. Please pay attention to currency, channels, and any uplifts in pricing, when organizing price books.

2. **Create/Add Product Categories**: Product Categories help organize the products and services you sell . Examples of Product Categories include Hardware Products, Software Products, Subscription Products, Professional Services, Labor etc. Your CPQ system already includes some sample product categories which are already populated in your CPQ instance. You can continue to use them as-is, rename them or delete them and add your own product categories if the builtin categories are not applicable to your business.

3. **Add Products**: Products (or services) represent anything that you sell to your customers. Despite the name, this can be an actual product or it could refer to a service you provide. It typically has a unique code or SKU  among other attributes. When you add a product, you must add four sections :
    a) General Attributes
    b) Pricing
    c) Configuration Rules
    d) Approval Rules.
We will go into details of each of these sections later in this document

4. **Add/Update the Quote UI Layout**: This layout represents the seller experience and can be controlled precisely to optimize the CPQ session for your seller users. It is a Form-based experience that is suitable to create wizard-like workflows that are very easy for sellers to use while creating a quote. Keep in mind that your sellers may not only be sales personnel, but also service personnel, sometimes in the field. The CPQ system has a built-in Quote UI Layout which you acn use as is, or more often than not, modify it for your sales workflow and steps. The sample quote layout in your instance has a multi-tab form layout that can be modified to suit your needs by editing it using the built-in Form editor. The layout has both presentation directives and actual input form fields which are either populated by the seller during the quoting process or are auto populated with information from a 3rd party system like a CRM. It is best to use the sample quote layout by trying to create an actual quote (just as a seller typically would), in order to understand the directives as well as the form fields. Then you can easily modify the quote UI layout for your specific needs.

5. **Upload Output Template Files**: The CPQ system generates a professional quote PDF document using one or more source template documents – typically Microsoft Word or Excel documents. These source template documents typically contain a proposal boilerplate, marketing information, customer testimonials and legal terms and conditions. The source documents can also have OpenTBS (https://www.tinybutstrong.com) macros embedded : these macros  map to information (form) fields contained in the quote instance. These form fields have unique names that can be referenced in the template documents. These field names are all defined in the Quote UI Layout (see Step 4 above). Your CPQ system already includes  a couple of sample Microsoft Word based source template files for you to use and adapt to your business needs. You can download them, modify them using Word and then re-upload them back to the CPQ system.

6. **Create or Update Document Templates**: A document template is essentially a consolidated source template that the CPQ system uses to generate the output quote or proposal document. A document template can encapsulate multiple template files you have uploaded in the previous step (see Step 5 above). For example, there is a sample document template in the system that combines a proposal boilerplate file and a terms & conditions template file in that order. You can use or modify this as you see fit, or you can  create your own Document Templates.

7. **Create or Update Quote Template**: A quote template is where all of the previous elements come together. It is used by the CPQ system to render the seller UI experience and also to make decisions during the quote creation session as to what products and services to show to the seller for inclusion in a quote, what configuration rules to apply or enforce, what prices to select, manage any discount and approvals and finally generate an output quote document. Included in your CPQ system is a fully configured sample Quote Template that you can use and adapt to your business needs or modify as you desire.


## CPQ Administration: Detailed Operations

Please refer to the following sections  for more details on the different components of your CPQ system and how to administer each of them.

## 1. Price Books

Typically, the first thing a CPQ Administrator does is to create one or more price books. 
MobileForce CPQ supports the creation of multiple price books that can also be related to one another via a hierarchical parent relationship. For instance, Businesses could create one price book for local or national use with the local currency, and another price book for each international market they operate in (each with its own currency). Price books allow one to assign different prices for products for different regions with different currencies or for different markets. In order to create a quote, a user **must** select a price book.

![Create Price Book in MobileForce CPQ](/zendesk_images/PriceBook.png)

Each MobileForce CPQ price book has a (required) **name** field. In addition, price books typically have the following fields:

* **Currency**: specifying the currency used for all prices in the price book. For now, only "USA" is activated as default as a valid value for the currency field.

The following fields of a MobileForce CPQ price book are found in almost all CPQ entities. For brevity, they are described once here, and not described again in other entities that also have these fields. 

* **Effective Date**: The date starting which  products listed in the price book can be sold
* **Expiration Date**: The date after which products listed in the price book can no longer be sold.
* **Active**: a toggle indicating whether the price book is ready for use in CPQ systems or is still being developed.
* **ACL**: indicating the user roles for the users that are allowed access to the price book. For instance, the US price book may be accessible only by sales user roles who are employed and selling within the USA, and hence not accessible to sales reps who are not members of the sales-USA role, because they sell in the Japan market.

Once a price book is created, the next step is to create product categories,then create products and services within their respective product categories.
Finally we create pricing for the products where we specify the price relative to a price book to reflect the price for the product in the specific market that this price book represents. A product may have different pricing entries and price values for different price books.

## 2. Product/Service Categories

Product/Service Categories in MobileForce CPQ are hierarchal groupings of products or services that are sold to the customer. 

In the MobileForce CPQ, this entity is simply called a **Product Category** to represent both products and service categories. 

A product or service category can be nested within another category. Products/Services can belong to multiple categories. For a Product/Service to be usable and added to a Quote, it must belong to at least one product category.

![Create Product Category in MobileForce CPQ](/zendesk_images/ProductCategories.png)

Each MobileForce CPQ Product Category has a (required) **Name** field. In addition, it can have a **Parent** field, indicating the product category hierarchy to which this product category belongs. Additional optional fields include **Description** and **Image**.

## 3. Products/Services

A product/service is anything that is sold by the business, irrespective of whether it is free or has a price. A product/service belongs to a category. Typically products are individual **line items** in *quotes*. When a MobileForce CPQ end-user creates a new Quote, they can add one or more products or service items by browsing or searching this catalog.

In the MobileForce CPQ, Products/Services are collectively simply called **Products** to represent both product and service items.

A product item can represent a physical product, a software product or a virtual/online product or a recurring subscription product. Similarly, a service item can represent a one-time setup or installation service, a design consultation service, professional services, a maintenance/repair service or a recurring warranty service.

Products may be nested i.e., a product may contain other products, representing bundled products or product features. Such nested products are stored in objects known as product groups. Products may also have attributes, (e.g., color). Rules can be specified on products to ensure valid configuration. To ease the management of products in the product catalog, products are organized in hierarchical categories.

Products can be broken down into two types: **Simple** and **Configurable**. Simple products have no attributes nor nested products. Configurable products may have attributes, nested products, or both. Configurable products have an associated **Product UI Layout** describing their attributes, nested products, and UIs that will be rendered to the end-user to configure the product after they have added it to the quote.

### 3.1. Products, Configurations and Rules

Each product or service item in MobileForce CPQ is specified through a UI consisting of 4 sections.

#### 3.1.1. General Section

This section includes the (required) **Name** field, and in addition, the unique product code or SKU.
An optional field, "Product Category" is used to provide one or more previously created product categories that the product belongs to.
Additional optional fields include **Description** and **Image**.  

![Create Product General Section in MobileForce CPQ](/zendesk_images/ProductsGeneral.png)

#### 3.1.2. Configuration Section

This section describes whether the product is a simple or a configurable product and in each case, additional configuration attributes.

The following fields are required:

**Type** indicating whether this product is simple or can be configured. That is, whether this product has editable attributes.

The quantity attribute has the following fields:

- **Editable** : Boolean indicating whether the quantity field is editable by the user. By default, it is 0, (editable).
- **Default**: Default value of the quantity. By default, it is 1.
- **Minimum Quantity** : Minimum allowed value of the quantity. By default, it is 1.
- **Maximum Quantity** : Maximum allowed value of the quantity. By default, it is 1,000,000.
- **Unit of Measurement** : This is an optional string to display after a quantity. Example values are ea, users, ft, lbs.
- **Multiply with Parent Product's Quantity** : Yes/No indicating whether the final quantity should be this product's quantity times the parent product's final quantity. For example, if one adds 3 PC computers with 2 hard-disks each, the quote should use a final quantity of 6 to compute the price. By default this field is 0, (false).
- **Quantity Step** : Numerical step value of the quantity. An entered quantity must be an integer multiple of the step. This step can be fractional, (e.g., 0.01). By default, it is 1.

![Create Product Configuration Section in MobileForce CPQ](/zendesk_images/ProductsConfig.png)

#### 3.1.3. Pricing Section

This section specifies the different ways that the product can be priced.

**Price Recurrence**: Specifies how often the user is charged.  Can be one of the following:
 * **One Time**: Price is applied only once.
 * **Per Minute**: Price is applied per minute.
 * **Hourly**: Price is applied per hour.
 * **Weekly**: Price is applied per week
 * **Bi-weekly**: Price is applied every two weeks.
 * **Semi Monthly**: Price is applied twice a month.
 * **Monthly**: Price is applied once a month.
 * **Quarterly**: Price is applied every three months.
 * **Half Yearly**: Price is applied twice a year.
 * **Yearly**: Price is applied once a year.

**Allow Discount**: Boolean indicating whether the user can specify a discount for this product.
**Discount Unit**: Unit type of discount.  Can be one of the following
 * **Amount**: Discount is a fixed amount.
 * **Percent**: Discount is a percentage.
 * **Both**: Discount can be either a fixed amount or percentage.  The sales rep will select the type in the quote.

If the discount unit is percentage, then two additional fields provide the range of allowed discount percentage.

- **Discount Percentage Min**: Minimum percent discount that a user can enter.  Default is 0.
- **Discount Percentage Max**: Maximum percent discount that a user can enter.  Default is 100%.

If the discount unit is an amount, then two additional fields provide the range of allowed discount amount.

- **Discount Amount Min**: Minimum fixed discount that a user can enter.  Default is 0.
- **Discount Amount Max**: Maximum fixed discount that a user can enter.  Default is 1,000,000.

![Create Product Pricing Section in MobileForce CPQ](/zendesk_images/ProductsPricing.png)

The price book entries sub-section within pricing section enables the product pricing to be specified in multiple price books. The following UI describes how this is done. First, the price book for which pricing is being provided is specified. Next, the product is specified. Both are required fields.
Under **Prices** sub-section, the two fields that can be specified are **List Price** and **Method** 

- **Method**: Method to use to compute the product's subtotal from the product's quantity.  It can be one of the following:
  * **Flat Fee**: Subtotal is a flat fee.  Quantity is ignored.
  * **Per Unit**: Subtotal is the list price multiplied by the quantity.
  * **Volume**: Subtotal is determined by looking up the list price from the price matrix, then multiplying it by the quantity.
  * **Tiered**: Similar to the **volume** method except the subtotal is computed by summing up the per tier prices.  For example, if tier 1 is $10 for 1-50 items and tier 2 is $8 for 51-100 items, then the price for a 70 items would be 50 x $10 + 20 x $8 = $660. This is different from the **volume** method, where the subtotal would be 70 * $8 = $560.
  * **Block**: Similar to the **volume** method except the value read from the table is not multiplied by the quantity.  For example, if the table has $500 for 51-100 items, then the subtotal for 70 items will be $500.
   
**List Price**: Unit price for the product.  Used by the **Flat Fee** and **Per Unit** methods.

##### 3.1.3.1. Price Book Item Tier

For the **Volume**, **Tiered**, and **Block** methods, the price book item will have an associated matrix of prices, which provide a list price for a given range of quantities.

Each row in this matrix has the following fields.

- **Id**: Internal unique numerical ID for this table row.
- **Price Book Item Id**: Id of the price book item owning this tier
- **From**: Start quantity of this tier.
- **To**: End quantity of this tier.
- **List Price**: Unit price for this tier.

![Create Product Pricing Section in MobileForce CPQ](/zendesk_images/ProductPricingPriceBook.png)

#### 3.1.4. Approval Section

In this section, we specify the **rules** that are used to decide how the product pricing in a quote is approved. Note that ONLY individual product-related rules are specified here. Most **rules** are typically specified at the Quote level (see **Quote Templates** under the **Quotes** section below). Product-level rules typically only make sense for **Configurable Products** or products with nested child products.  They only apply within scope of the product itself. You can use them to validate custom fields, (e.g., end date must be less than start date), or make constraints or actions for line tables inside the product. 

![Create Product Approval Section in MobileForce CPQ](/zendesk_images/ProductApproval.png)

The individual approval rules are specified as follows. Each rule has the following **required** fields:

* **Name**: A descriptive name for the quote approval rule
* **Trigger Condition**: This is actual *rule expression* that is evaluated at run-time. If this expression evaluates to *true* then the rule action is triggered. To specify a valid rule expression, please refer to the **Rules** section below which describes the trigger condition (rule expression) syntax and also gives a comprehensive list of available functions and system variables that can be used in rule expressions.
* **Rule Evaluation Order**: A number indicating the order in which multiple rules are evaluated: higher numbered rules are evaluated first, followed by lower numbered rules.
* **Approval Request Email Template**: an email template used to send a request for approval of the quote.
* **Approval Request Cancel Template**: an email sent to an approver to indicate that an approval has been cancelled.
* **Approvers**: A comma separated list of email addresses of users that can approve the quote. These users will be notified on approval requests.
* **Approval Reason**: User-friendly description why the quote needs approval. This description can contain macro expressions using fields from the quote. These macro expressions written as ${expr} where expr is a valid expression.

In addition, the following **Optional** fields can be specified.

* **Skip later rules after trigger** : Once a specific rule is triggered, this toggle enables the remaining rules to be skipped. The default is that the remaining rules are not skipped, and instead evaluated.

![Create Product Approval Rule in MobileForce CPQ](/images/CPQApprovalRule.png)


### 3.2. Product UI Layouts

Product or Service items that are of type **Configurable** must have an associated **Product UI Layout**. A **Product UI Layout** is very similar to a **Quote UI Layout** and share the same underlying **Form Configurator Specification and Engine**. Please refer to the **Quote UI Layout** section below for more details on how to create a UI Layout. For convenience, CPQ System has *Export*, *Import* and *Copy* functions built-in so UI Layouts can be easily created, copied, and modified fast. These UI Layouts are specified in a familiar XML specification that can even be modified by hand in your editor of choice.

## 4. Quotes

A **Quote** in the MobileForce CPQ System consists of two separate modular components designed for ease of use, ease of maintenance and scalability:
- **Quote Template**: This represents the structure, state and logic of what products/services can go into a Quote, what price book to use, what rules constrain products/services that can be added or how they can be priced/discounted, and finally what approvals need to be processed based on various conditions.
- **Quote UI Layout**: This represents the UI that guides the end-user to create a valid quote and go through the whole Configure, Price, Quote, Approvals and Document Generation workflow as quickly and efficiently as possible.

In the MobileForce CPQ system, both the **Quote Template** and the **Quote UI Layout** come with a Default Template and a Default Layout, respectively. This enables administrators to quickly get started and customize them by simply copying and modifying them.

From an end-user perspective, the CPQ system enables the end-user to create a Quote for a specific Quote Template. In essence, the user implicitly creates a Quote from a Quote Template. In the end-user UI, the CPQ system maintains different sections, where it lists all Quotes created from a specific Quote Template separately from Quotes created from a different Quote Template.

It is recommended that the administrator first setup a **Quote UI Layout** and then proceed to setup a **Quote Template** as the layout will need to be specified when creating a template.

### 4.1. Quote UI Layouts

A **Quote UI Layout** and a **Product UI Layout** are essentially **UI Layout** specifications that share the same underlying **Form Configurator Specification and Engine**. For convenience, CPQ System has built-in *Export*, *Import* and *Copy* functions so UI Layouts can be easily created, copied, and modified fast. The CPQ System provides a **Graphical UI Layout Builder** for ease of use in constructing customized UI Layouts and previewing them. These UI Layouts are specified in a familiar XML specification that can even be modified by hand in your editor of choice by first exporting them out of the CPQ System and later importing the modified versions.

UI Layouts are essentially a HTML Form-type responsive layout specified using a combination of **Tabs**, **Sections** and **Input Elements** of various types, each with its own unique name. **Input Elements** are roughly modeled after HTML form inputs but with more extensive set of types supported. These input names  that is automatically rendered by the system for the end-user are then made available by the CPQ System to be used in **Product and Pricing Rule Expressions** and also in **Quote and Contract Document Templates**.

A **Quote UI Layout** in MobileForce CPQ Graphical UI Layout Builder has 5 sections.

#### 4.1.1. General Section

This has general information such as **Name** and the choices to show/hide or enable/disable explicit user-action buttons to **Save**, **Validate** and **Close/Reopen** a Quote.

![Create Quote General Section in MobileForce CPQ](/zendesk_images/QuoteUILayoutGeneral.png)

#### 4.1.2. Types Section

This section enabled the administrator to create their own **Custom Data Types** that extend the CPQ Systems built-in input field types. For example: you can define your own compound type called **Address** made up of 5 primitive data types in it - **Street Address**, **City**, **State or Province**, **Postal Code**, **Country**. This custom **Address** type can then be used as a type for an input field specified in the form described in the next section. The CPQ System will detect that it is a custom type and render all the component fields at once so an end-user can populate all the components when specifying an **Address**.

![Create Quote Types Section in MobileForce CPQ](/zendesk_images/QuoteUILayoutTypes.png)

#### 4.1.3. Form Section

This section is the core of the **UI Layout**. It specifies exactly how the Quote or the Product Configuration UI is to be rendered to the end-user. It typically has a collapsible, tree-like structure on the left panel that starts with **Tabs** each of which contain one or more **Sections**, each of which in-turn contain one or more **Input Fields**. **Sections** can be of different layouts like a **Multi-column** or **Table** layout. It is modeled after a **HTML DOM** structure. The right panel gives a **Preview** of the entire Form in different form factors - **Phone**, **Tablet** or **Computer**. It also provides complete **Details** of a specific item selected in the left panel such as a **Tab**, **Section**, **Table** or an **Input Field**. The left panel supports drag-n-drop functionality to easily re-order tabs, sections and input fields.

The CPQ System comes with a built-in **Default Quote UI Layout** that has the following tabs, sections and input fields.

##### 4.1.3.1. Customer Tab

This is where the end-user can select an Account, Opportunity and Contact to prepare the Quote for. It also has their own contact information and their company information.

![Create Quote Forms General Section in MobileForce CPQ](/zendesk_images/QuoteUILayoutFormC.png)

##### 4.1.3.2. Quote Tab

This tab has a combination of common Quote fields such as dates, status etc. at the top followed by one or more **Line Items** tables where the end-user can add Product/Service line items from the catalog. This table also has sub-totals and total fields. It also has designated areas to specify line-item level discounts or global discounts.

![Create Quote Forms Quote Section in MobileForce CPQ](/zendesk_images/QuoteUILayoutFormQ.png)

##### 4.1.3.3. Approvals Tab

This tab shows the history of all Quote Approvals including approval requests that are pending. It enables the end-user to submit and track quote approvals status in one place.

![Create Quote Forms Approvals Section in MobileForce CPQ](/zendesk_images/QuoteUILayoutFormA.png)

##### 4.1.3.4. Signatures Tab

This tab enables the end-user to collect Digital Signatures. This is especially helpful in scenarios where sales or service personnel are at customer premises and would like to capture a digital signature on a touch-enabled device like a Tablet or a Smartphone, so they can accelerate the contracting process.

![Create Quote Forms Signature Section in MobileForce CPQ](/zendesk_images/QuoteUILayoutFormS.png)

##### 4.1.3.5. Generated Docs

This tab enables the end-user to Generate the final quote, proposal or a multi-page contract document in a PDF format by utilizing a pre-configured document template (see **Document Templates** section below). The CPQ System will utilize all the information from the Quote and infuse appropriate values into the selected document template to generate a PDF document. The end-user can then view the generated document, share it with the customer via email and also click on the *Save to CRM* button to save this entire quote with line items and generated document to a CRM Opportunity.

![Create Quote Forms Documents Section in MobileForce CPQ](/zendesk_images/QuoteUILayoutFormG.png)

#### 4.1.4. Actions Section

This section in the Graphical Form Builder UI contains built-in and custom actions to be performed by the CPQ System, each of which are tied to specific **Events** during the CPQ process. For example, there are built-in actions like *Validate Action* that get triggered when the end-user clicks on the *Validate* button in the UI, that results in the CPQ System validating all elements of the Quote configured thus far. Similarly, an administrator can define custom actions that are specific to their business and can extend the system easily by writing server-side action scripts that are coded to the CPQ System specification.

![Create Quote Actions Section in MobileForce CPQ](/zendesk_images/QuoteUILayoutAction.png)


#### 4.1.5. Summary Section

This section enables the administrator to choose which input variables to show as columns in the list view of all the Quotes. It comes with default columns such as name, status and id. The administrator can add and tailor the columns to what the end-users would like to see in the list view.

![Create Quote Summary Section in MobileForce CPQ](/zendesk_images/QuoteUILayoutSummary.png)

### 4.2. Quote Templates

A **Quote Template** is a template that is used to create any quote in the CPQ System. It contains the structure and logic of what products/services can go into a Quote, what price book to use, what rules constrain products/services that can be added or how they can be priced/discounted, and finally what approvals need to be processed based on various conditions.

The CPQ System comes with a built-in Default Quote Template that uses the Default Quote UI Layout. A fully functional Default Quote Template enables an administrator to easily copy and customize the template extending it to meet their specific needs. The following sections describe the component sections of a Quote Template.

#### 4.2.1. General Section

This section primarily consists of informational attributes such as **Name** and a **Unique Form ID** that are required to create a Quote Template. In addition, it also has a **Access Control** subsection that has the following attributes that can be optionally specified.

- **Active**: A switch to *Activate* or *De-activate* a template. Only Active templates can be used by the end-user to create Quotes.
- **ACL**: A logical combination (Any or All) of roles that dictate which end-user roles this template is visible to and who can use them to create Quotes.
- **Effective Date**: A date starting which this template is available to authorized end-users to create Quotes.
- **Expiration Date**: A date after which this template will no longer be available to authorized end-users to create Quotes.

![Create Quote Template in MobileForce CPQ](/zendesk_images/QuoteTemplateGeneral.png)

#### 4.2.2. Configuration Section

This section consists of constraints and rules that govern how the CPQ System renders a Quote and validates. Every Quote Template must have an associated **Quote UI Layout** that is specified here.

![Create Quote Template in MobileForce CPQ](/zendesk_images/QuoteTemplateConfig.png)

##### 4.2.2.1. Line Item Tables

A **Line Item Table (also called Product Group)** holds the Product/Service items that the end-user adds while creating a Quote in the Configure, Price, Quote workflow.

One or more **Product Groups or Line Item Tables** must be added to the Quote template which will enable the end-user to choose select **Product/Service** items from the catalog and store them here. Each such **Product Group or Line Item Table** is uniquely identified by the **Name** field. This name is internally represented as a system variable that can be used in **Rule Expressions** and **Document Templates** to refer to the added line items and their attributes. It is typically represented as a JSON-style array and can be accessed using JSON array notation. For ex: if the table name is *line_items* and there 3 Product/Service items added to it, then it will be represented as a 3-item array accessible as *line_items[0], line_items[1] and line_items[2]* in any expression. To access a specific attribute of a specific item, one can use JSON-style dot-notation. For example, *line_items[1].cpq_quantity* will give you the user-entered Quantity of the 2nd Product/Service line item they added in the quote.

Each **Product Group or Line Item Table** can be configured to only allow adding **Product/Service** items from specific **Product/Service Categories** and can also be constrained to have a **Minimum** and **Maximum** number of items.

![Create Quote Template in MobileForce CPQ](/zendesk_images/QuoteTemplateLineItems.png)

##### 4.2.2.2. Product Rules

This subsection enables an administrator to specify any number of **Configuration Rules** that govern what types of **Product/Service** items can be added together in the **Line Item Tables**. The CPQ System evaluates these rules in the specified **Rule Evaluation Order**. The CPQ System always evaluates all the **Product Rules** before it proceeds to evaluate all the **Pricing Rules** and finally the **Approval Rules**.

Please refer to the **Product, Pricing and Approval Rules Specification** below to learn how to create and configure Product Rules.

#### 4.2.3. Pricing Section

This section enables an administrator to specify the **Price Book** that is associated with this Quote Template. When an end-user creates a Quote using this template, all **Product/Service Items** added to the Quote will only derive the corresponding Pricing Item from the associated **Price Book**. Typically, a **Product/Service** item in the catalog can have multiple Price Book entries. For example, one for USA region specified in USD, one for EMEA region specified in EUR etc. Accordingly, two different Quote Templates must be created (one for USA Price Book and a separate one associated with the EMA Price Book) that will enable the CPQ System to appropriately pick up the right Price Book Entry for an added Product/Service item.

![Create Quote Template in MobileForce CPQ](/zendesk_images/QuoteTemplatePricing.png)

##### 4.2.3.1. Pricing Rules

This subsection enables an administrator to specify any number of **Pricing Rules** that govern what pricing changes must be made for **Product/Service** items in the **Global Quote Adjustments**. For example, one can specify a rule based on the current date to automatically add a *End of Month* or *End of Quarter* promotional discount to the Quote. The CPQ System evaluates these rules in the specified **Rule Evaluation Order**. The CPQ System always evaluates all the **Product Rules** before it proceeds to evaluate all the **Pricing Rules** and finally the **Approval Rules**.

#### 4.2.4. Approvals Section

This section enables the administrator to specify the appropriate **Email Templates** to be be used for **Approved**, **Declined** and **Cancelled** approval requests. In addition, the administrator can optionally set the initial approval status of all Quotes to a custom value. They can also optionally specify a numerical value for **Close After (Days)** that instructs the CPQ System to close the quote (set its status to **Closed**) automatically after the specified number of days from its creation.

![Create Quote Template in MobileForce CPQ](/zendesk_images/QuoteTemplateApproval.png)

##### 4.2.4.1. Approval Rules

This subsection enables an administrator to specify any number of **Approval Rules** that govern under what conditions Approvals are needed. For example, a discount beyond 20% may require a Manager approval. Once can also specify multiple levels of approvals depending on increased discount (escalated approvals) by specifying them in a particular evaluation order. The CPQ System evaluates these rules in the specified **Rule Evaluation Order**. The CPQ System always evaluates all the **Product Rules** before it proceeds to evaluate all the **Pricing Rules** and finally the **Approval Rules**.

![Create Quote Template in MobileForce CPQ](/zendesk_images/QuoteTemplateApprovalRule.png)

#### 4.2.5. Product, Pricing and Approval Rules Specification

When creating a **Product Rule**, a **Pricing Rule** or an **Approval Rule** the following attributes must be specified.

First, one must specify what type of action in the CPQ System triggers this rule.

* **Triggered By**: The type of the event that triggers this rule.  Can be one of the following:
  * **Page Load**: This rule should trigger whenever the page is first loaded.
  * **Save**: This rule should trigger whenever the user saves the source object.
  * **Validate**: This rule should trigger whenever the user request validation for the source object or performs an action that requires validation.
  * **Add Product**: This rule should trigger whenever a product is added to or deleted from a product group.
  * **Price Computation**: This rule should trigger when prices are computed or recomputed in the quote.
  * **User Action**: This rule should trigger whenever the user performs a user-defined action.  The name of the action is specified in the **triggerAction** field.
  * **Approval Check**: This rule should be triggered whenever the cpq_needs_approval field needs updating. Generally, this is done any time whenever the quote needs to perform a server-side operation, (i.e., any of the above **Triggered By** values).

**Pricing Rules** can only be triggered by **Price Computation**.
**Approval Rules** can only be triggered by **Approval Check**.

![Create Quote Template in MobileForce CPQ](/zendesk_images/QuoteTemplatePricingRule.png)

In a **Product Rule** if the **Triggered By** field is set to a **User Action**, then the following additional action type must be specified.
* **Trigger Action**: Name of the user-defined action that should trigger the rule. 

In all cases, one must specify the condition under which a Rule is triggered. This can be specified using a **Rule Expression**.
* **Trigger Condition**: An rule expression that should be evaluated to determine whether the rule should trigger or not.  The syntax of this expression is described later. (see **CPQ Rules, Expressions, Functions and Variables** section below) 

A Rule Evaluation Order (numerical value) must be specified so the CPQ System knows the order of rule evaluation when multiple rules are specified.
* **Evaluation Order**: A number specifying the order in which rules should be evaluated.  Rules with a lower order value will be evaluated before rules with a higher order value.

When multiple rules are specified, and a rule is triggered, one can optionally instruct the CPQ System to abort subsequent rule processing down the evaluation order by setting the following option to true.
* **Skip Later Rules After Trigger**: True/False boolean value. If set to true, then if this rule is triggered, no more rules will be checked.  That is, if there are two rules A and B that can be triggered when an event occurs, if **Skip Later Rules After Trigger** is true for A, rule evaluation will be stopped after A and rule B will never be evaluated.  Note that **Skip Later Rules After Trigger** only prevents execution of roles in the same scope.  Rules in other scopes will still be executed.

Finally, in the **Response** subsection, the administrator can specify what type of action to take.

* **Action Type**: Type of the action to perform if the rule triggers.  Can be one of the following values:
  * **Show Error**: Generate an error message and abort the triggering operation.
  * **Show Warning**: Generate an warning message.  The triggering operation will not be aborted.
  * **Show Informational Message**: Generate an informational message.  The triggering operation will not be aborted.
  * **Add Product**: Automatically add a product to the parent product or quote within a specific product group (line items table).
  * **Delete Product**: Automatically delete a product from the parent product or quote. If there are multiple product groups (line items tables) within the quote, one can specify which product group (line items table) to delete from.
  * **Add Discount**: Automatically add a pricing discount to the parent product or quote. One can specify the discount type as a fixed **percent** or a fixed **amount** or a dynamically computed formula using an expression (see **CPQ Rules, Functions and Variables** section for syntax of expressions).
  * **Needs Approval**: Mark this quote as needing approval along with a specific reason (user-friendly description why the quote needs approval). This description can contain macro expressions using fields from the quote. These macro expressions written as `${expr}` where `expr` is a valid CPQ expression. In addition, one can specify a specific **Email Template** to use and an **Approver Group** to send this approval to.

For **Approval Rules**, only a **Needs Approval** action type is supported.
For **Pricing Rules**, **Add Product**, **Delete Product** and **Needs Approval** action types are not available as they are all product or approval related.


## 5. Approvals

Once a quote is generated, it sometimes needs to be approved, especially if the quote used non-standard pricing or it is inaccurate because it is missing some key details. While the quote may be valid, (based on application of the validation rules), it may still not meet the business objectives. To address this issue, the MobileForce CPQ system provides a mechanism for human intervention: whereby valid quotes are sent through a business chain of command for approval. The idea is that the approvers would eyeball the quote to make sure that business objectives are met, thus approving or rejecting the quote. While quote approvals can quickly morph into complex approval workflows, it is important to keep the approval process simple, transparent, and easy to understand and program.

Approval rules can be attached to a quote, a product, or a product group to specify the conditions under which the quote needs approval. The CPQ Approval process supports  multiple levels of approvals, where approvers at one level will need to approve the quote before an approval request is sent to the next level. If multiple approval rules trigger, approval is required from the highest approval level specified by the rules.

The CPQ System manages multiple levels of approvals for Quotes. An approval request can be sent to a specific individual or a group of individuals (**Approver Groups**). The actual email that is sent out in each of the approval workflow steps can be customized by the administrator. 

### 5.1. Approver Groups

This section enables administrators to create a named **Approver Group** that consists of a combination of individuals specified by direct emails or role names. An approver group identifies a set of one or more users than can approve a quote. The CPQ System also supports escalated approvals workflow. For example, an approval is first sent to a Manager before it is set to a Vice President and then to a CEO.

In addition to specifying whom to notify for approvals, the CPQ System enables an administrator to specify authorized additional approvers who are not notified in the regular approval workflow process but are authorized to login to the system to approve requests on a contingency basis. For example, if a regular approver is out of office and unavailable, an authorized additional approver can step in and approve the request on their behalf.

Each Approval Group has a (required) **Name** field. In addition, Approval Groups typically have the following fields:

* **Level** : Numerical approval level. When a quote needs approval from multiple approval groups, it will request approval from groups with lower approval levels before requesting approval from groups with higher approval levels. For example, if a quote needs approval from a 'Manager' approval group at level 1 and a 'VP' approval group at level 2, an approval request to the 'VP' group will not be sent until after the 'Manager' approval group has approved it.

Approvers can be individual users or roles. In addition, approvers can be notified approvers, who get notified, or additional approvers who do not get notified of approvals. The following kinds of approvers are supported, each allowing optional notification. Thus, you can specify approvers in three ways, by explicit email addresses, by MobileForce roles, or by a form expression that evaluates to an email address.

* **User Emails** :A comma separated list of email addresses of users that can approve the quote. These users will be NOT be notified on approval requests.
* **User Roles** : A comma separated list of MobileForce roles. All MobileForce users in these roles can approve the quote. These users will be NOT be notified on approval requests.
* **Dynamic Expression** : An  form expression that returns a comma separated list of email addresses that can approve the quote. These users will be NOT be notified on approval requests.

![Create Approval Groups in MobileForce CPQ](/zendesk_images/ApproverGroups.png)

Approval Groups splits approvers into two categories: notified approvers and un-notified approvers. Both kinds of approvers can approve the quote. However, only notified approvers receive notifications on approval requests. For example, one may wish to make a supervisor be a notified approver but the supervisor's manager be an un-notified approver. This is done so that the supervisor's manager does not get spammed by day-to-day approval requests but can approve a quote for exceptional cases, (e.g., the supervisor is sick that day.)

In future, MobileForce CPQ will support approval history, where every quote will have an associated approval history, for the purposes of creating an audit trail.

### 5.2. Email Templates

Since quotes are sent for approval by email, it is natural to provide email templates that can be used to generate the approval requests as well as the approval/rejection. The CPQ System not only supports email templates for various approval workflows, it also supports distinct email templates that can be created and saved for subsequent use by different users for different purposes.

Quotes can have one or more email templates. These templates are used to generate emails as part of the quote process, such as approvals.

The subject and body of email templates can contain macro variables of the form '${form-expr}', where form-expr is a valid  form expression that can reference fields in the quote.

Each MobileForce CPQ Email Template has a (required) **Name** field. In addition, Email Templates typically have the following fields:

* **Purpose** : Purpose of the email template. Can be one of the following:
  * Approval Request: Approval request sent to an approver.
  * Cancel a Pending Approval Request: Email sent to an approver to indicate that an approval has been cancelled.
  * Approved Confirmation: Email sent to the quote owner indicating that the quote is approved.
  * Declined Confirmation: Email sent to the quote owner indicating that the quote is declined.
  * Approval Cancelled Confirmation: Email sent to the quote owner indicating that the quote's approval process was cancelled.

* **Subject** : Email subject. Can contain macro variables.
* **Body** : Email body. Can contain macro variables
* **Body Format** : Format of the email body. Can be one of the following:
  * Text: Body is plain text
  * Html: Body is a HTML document

The MobileForce CPQ System provides a default built-in HTML content for each of the different types of template that can be used as a starting point by an administrator. An administrator can set the email to default content by clicking on *Set Content to Default* button.

![Create Email Templates in MobileForce CPQ](/zendesk_images/EmailTemplate.png)

## 6. Quote and Contract Documents
A sales contract is a formal agreement between the seller and a buyer, where the seller provides products or services, for payment or a promise of payment from the buyer. Since sales contracts cover legal aspects of a sale, they often have distinct sections such as legal provisions (state laws and arbitration) as well terms and conditions of the sale. In order to simplify the creation of sales contracts, document templates are used. These templates contain customizable sections that provide the presentation of sales  records such as line items, signature fields, and terms and conditions. The sections can be included or excluded.

Starting from a quote, MobileForce CPQ can generate a set of documents. Each document is generated from a document template which contains one or more sections. Each section has an associated MS word or excel file containing macro variables that are expanded upon generation. Users  have the option to include or exclude sections from the document.

### 6.1. Document Templates

The following document template is used to generate a proposal for a customer that is based on their use of a CRM such as Hubspot, SugarCRM and Zendesk Sell. This document template has the following sections

Each MobileForce document template has a (required) **Name** field. In addition, document templates typically have the following fields:

![Create Proposal with quote in MobileForce CPQ](/zendesk_images/DocumentTemplate.png)

* **Owning Quote**: the quote from which the proposal is being generated
* **Quote must be valid**: a toggle which ensures that only valid quotes can be used to generate a proposal. If set to true, and the owning quote is not a valid quote, then the proposal will not be generated. By default, it is set to True.
* **Can generate when locked**: a toggle which if set to true permits the proposal to be generated from this template even if the current quote instance is locked. By default, it is set to True. 
* **Hidden Condition** : An optional rule expression that should be evaluated to determine whether this document template should be displayed when displaying the list of documents that can be generated.
* **Disabled Condition** : An optional rule expression that should be evaluated to determine whether this document template should be disabled, (i.e., shown but unselectable), in the list of documents that can be generated.

* **Generated File Format** : Format of the target document generated from this template. Can be one of the following:
  * docx: A MS Word document. Templates using this format can only have one section. Additionally, that section's template file must be a MS Word document.
  * xlsx: A MS Excel document. Templates using this format can only have one section. Additionally, that section's template file must be a MS Excel document.
  * pdf: A PDF document. Templates using this format can have one or more sections.

* **Generated Filename** : File name of the generated document. You can use macro variables in the ‘Generated Filename’ field to create unique filenames (for example, by using a date expression).  The macro variable syntax is the same as the syntax used for email templates, i.e., **(‘${form-expr}’)**.  For example, the value **"${DATE_FORMAT(NOW(), ‘Mj'}_${customer_name}_proposal.pdf”** would generate **‘Apr1_Spacely Sprockets_proposal.pdf'** if it was invoked on April 1st, and the customer name was Spacely Sprockets.  Note also that in order to ensure that previously created files aren't accidentally overwritten, the quote will still automatically append a ‘ (num)’ to the end of the filename if there is already a file with the same name.


* **Generated File ACL** : Access Control List (ACL) for the generated document. Users that are authorized by this ACL can view the generated document. Note that this is different than the acl field for this object, which identifies which users can generate the document.

* **Generated File Hidden Condition** : An optional rule expression which will determine if the generated document will be visible to the user.

* **Document Sections** : the various sections in the document template, indicating the order in which they appear, and whether they are optional or not. Furthermore, each section has an associated filename, which describes the file from which the section is generated. Different sections can use different files.
 Document template sections  have the following required fields:
 
 ![Create section in document template for a proposal in MobileForce CPQ](/zendesk_images/DocumentTemplateSection.png)

  * **Name** : Displayed name for this section.
  * **Order** : Order of this section within the parent document template. Sections within a document template are ordered by this field in ascending order.
   * **SourceFilename** : Name of the template file to use to generate this section. This file must be either a MS Word file, a MS Excel file, or a PDF file. If this is a MS Word or Excel file, it can include macro expressions.
   
In addition, the following optional fields are supported in a document template section:

  * **Hidden Condition** : An optional rule expression which determines whether this section should be hidden from the user. Hidden senctions will never be included in the generated document.
  * **Optional** : Boolean value indicating whether the user is allowed to exclude this section from the document on document generation. 
 
## 7. CPQ Rules, Expressions, Functions and Variables

Products and Quotes may have one or more rules that are used in **Configuration**, **Pricing** and **Approvals**. A rule specifies an automated action that should be performed on a product or quote when some event occurs on that product or quote.

### 7.1. Rule Expressions and  Syntax

Rule expressions can be composed using a combination of built-in system variables, user-specified custom variables, built-in functions and built-in operators (logical and arithmetic). Rule expressions are modeled after the familiar Microsoft Excel formula syntax.  More exactly, only string and numeric scalar data types are supported and the set of allowed functions are listed below.  The variables in the formula can be referenced by their names.  A formula can only reference variables that are either built-in system variables listed below or input field names that are specified in **Quote UI Layout** or a **Product UI Layout**. 

The grammar for formula is as follows.  This grammar is written in [Augmented Backus-Naur Form](https://en.wikipedia.org/wiki/Augmented_Backus%E2%80%93Naur_form).

```abnf
formula              =  "=" expression

expression           =  "(" *WSP expression *WSP ")"
expression           =/ prefix-operator *WSP expression
expression           =/ expression *WSP infix-operator *WSP expression
expression           =/ expression *WSP postfix-operator
expression           =/ constant
expression           =/ variable
expression           =/ function

prefix-operator      =  "-" / "!"

postfix-operator     =  "%"  ; Percent operator.  Divides value by 100

infix-operator       =  arithmetic-operator
infix-operator       =/ concatenate-operator
infix-operator       =/ comparison-operator
infix-operator       =/ logical-operator

arithmetic-operator  =  "^" / "*" / "/" / "+" / "-"

concatenate-operator =  "&"

comparison-operator  =  "=" / "==" / "<>" / "!=" / "<" / "<=" / ">" / ">="

logical-operator     =  "&&" / "||"

constant             =  numeric-constant / string-constant

numeric-constant     =  1*DIGIT ["." 1*DIGIT]
numeric-constant     =/ "." 1*DIGIT

string-constant      =  DQUOTE *CHAR DQUOTE  ; Double quote chars are escaped via '""'
string-constant      =/ "'" *CHAR "'"  ; Single quote chars are escaped via "''"

variable             =  name
variable             =/ variable *WSP "[" *WSP expression *WSP "]"
variable             =/ variable *WSP "." *WSP name

function             =  name *WSP "(" *WSP expression *(*WSP "," *WSP expression ) *WSP ")"

name                 =  (ALPHA / "_") *( ALPHA / DIGIT / "_")
```

### 7.2. Built-in  Functions

The following standard Microsoft Excel-like functions are supported:

The only supported primitive values are strings, numbers, and JSON key/value objects.  Numbers will be represented internally as double precision numbers.  Strings will be automatically converted to numbers when necessary and vice versa.  There is no boolean type.  A value is considered to be false if it is the empty string, zero or the string "0".  Otherwise, it is considered to be true.

A JSON key/value object is a string that follows the [JSON object format](https://www.json.org/).  The JSON object must have a "key" and a "value" field.  An example JSON key/value object is `{"key": 1, "value": "One"}`.  The "key" field contains the actual or stored value while the "value" field contains the user-displayable string.  JSON key/value objects are often used for picklist inputs.  For example, a "user" picklist input may have its database ID stored in the "key" field and the user's name in the "value" field.

A JSON key/value value in any arithmetic or conditional expression will be automatically converted to its key.  For example '{"key": 1, "value": "One"}' + 3 will be evluated to 4.

* **ABS(number)**: Return the absolute value of the given number.
* **AND(arg1, arg2, ..._)**: Return the logical AND of the given arguments.
* **IF(cond, then-expr, else-expr)**: If the first argument is true, return the second argument, else return the third argument.
* **INT(number)**: Round the given number down to the nearest integer.
* **MAX(num1, num2, ...)**: Return the maximum value of the given arguments.
* **MIN(num1, num2, ...)**: Return the minimum value of the given arguments.
* **NOT(expr)**: Return the logical NOT of the given argument.
* **OR(arg1, arg2, ...)**: Return the logical OR of the given arguments.
* **ROUND(number [, num-digits])**: Round the given number to the nearest integer.  If `num-digits` is specified, then the specified number of digits after the decimal point will be displayed.
* **SEARCH(needle, haystack [, offset])**:  Return the index of the needle string within the haystack string.  If the needle is not in the haystack, return '#VALUE!'.
* **COUNT(array)**: Returns the count of the number of elements in the given array.
* **SUM(array [, fieldName])**: Returns the sum of all the elements in the given array.  If 'fieldName' is specified, then the array is assumed to be an array of objects instead of an array of numbers.  'fieldName` specifies which field in the array of objects should be summed together.
* **AVG(array [, fieldName])**: Returns the average of all the elements in the given array.  If 'fieldName' is specified, then the array is assumed to be an array of objects instead of an array of numbers.  'fieldName` specifies which field in the array of objects should be averaged together.
* **IN(element, array)**:  Return true if the given element is in the given array.
* **ACLMATCH(acl, array)**: Return true if the given ACL matches the given array.  The ACL uses MobileForce's ADL ACL syntax.  The array must be an array of strings.
* **CURRENCY_FORMAT(number [, locale [, format] ])**: Format the given number as a currency, using PHP's money_format() function.
* **NUMBER_FORMAT(number [, decimals [, decPoint [, thousandsSep] ] ])**: Format the given number using PHP's number_format() function.
* **KEY(arg)**: If the given argument is a JSON key/value object, return the 'key' field of the object.  Otherwise, return the argument unchanged.
* **VALUE(arg)**: If the given argument is a JSON key/value object, return the 'value' field of the object.  Otherwise, return the argument unchanged.
* **KEYVALUE(key, value)**: return a JSON key/value object, whose key and value are the given arguments.
* **DATEADD(date, val, unit)**: Adds the given value to the given date or date/time.  'date' must be a valid date or date/time string in ISO-8601 format. 'val' must be an integer.  'unit' identifies the unit-type of the value. 'unit' must be one of: 'y', 'm', 'd', 'w', 'h', 'i', or 's'.  ('m' is months, 'i' is minutes).
* **TODAY()**: Return today's date
* **NOW()**: Return todays's date and time.

In addition, the following CPQ-specific functions are supported:

* **PROD_COUNT(productCode [, productGroup])**: Returns a count of all products with the given code in the named group.  If the group name is missing, then this is for all groups.
* **PROD_QTY(productCode [, productGroup])**: Returns a the sum of the quantities of all products with the given code in the named group.  If the group name is missing, then this is for all groups.
* **HAS_PROD(productCode [, productGroup])**: Returns true if there is a product with the given code in the named group.  If the group name is missing, then this is for all groups.  This is basically just a shorthand for `(PROD_COUNT(productCode, productGroup) > 0)`.
* **CAT_COUNT(categoryName [, productGroup])**: Returns a count of all products in the given category in the named group.  If the group name is missing, then this is for all groups.
* **CAT_QTY(categoryName [, productGroup])**: Returns a the sum of the quantities of all products in the given category in the named group.  If the group name is missing, then this is for all groups.
* **HAS_CAT(productCode [, productGroup])**: Returns true if there is a product in the given category in the named group.  If the group name is blank, then this is for all missing.  This is basically just a shorthand for `(CAT_COUNT(productCode, productGroup) > 0)`.
* **QTY([productGroup])**: Returns a the sum of the quantities of all products in the named group.  If the group name is missing, then this is for all groups.
* **PROD_LIST_PRICE(productCode [, productGroup])**: Fetch the total list price for the product, without any discounts.
* **PROD_SYSTEM_PRICE(productCode [, productGroup])**: Fetch the total list price for the product, with only system (pricing-rule) discounts included. User discounts are not included.
* **PROD_NET_PRICE(productCode [, productGroup])**: Fetch the total list price for the product, with both system and user discounts included.
* **CAT_LIST_PRICE(categoryName [, productGroup])**: Fetch the total list price for all products in the given category, without any discounts.
* **CAT_SYSTEM_PRICE(categoryName [, productGroup])**: Fetch the total list price for all products in the given category, with only system (pricing-rule) discounts included. User discounts are not included.
* **CAT_NET_PRICE(categoryName [, productGroup])**: Fetch the total list price for all products in the given category, with both system and user discounts included.

###  7.3. Built-in  Variables

One can access any attribute, group, or CPQ-computed value using the naming syntax described in the previous section. In the CPQ system, all the variables and values in the entire Quote is stored as a JSON object with nested fields. The top level JSON object will contain data for the entire quote.  Each attribute or product group (line items array) defined for the quote will be a field in this JSON object. So, a standard JSON notation can be used to refer to any variable contained in the quote using nested level references for hierarchy. In general, for non-primitive system or input variables, say, **arrays**, a JSON-object notation can be used to refer to variables inside them. For example: **line_items[1].cpq_quantity** will refer to the value of the Quantity field of the 2nd line item added in the Quote. By convention, the names of all CPQ-specific inputs will be prefixed with or contain 'cpq_'. Users are free to define their own inputs (variables) in **Product UI Layouts** or **Quote UI Layouts** with names that do not have 'cpq_' in them.

#### 7.3.1. Quote Level System Variables

The quote object will have the following CPQ specific fields:

* **cpq_id**: ID of the quote that created this form.
* **cpq_name**: Name of the quote.
* **cpq_desc**: Description of the quote.
* **cpq_status**: Status of the quote
* **cpq_price_book**: Name of price book for the quote
* **cpq_eff_date**: Effective date for the quote
* **cpq_exp_date**: Expiration (close) date for the quote
* **cpq_subtotal**: Subtotal of the quote before discounts.
* **cpq_user_discount**: User entered discount of the quote.
* **cpq_user_discount_type**: Type of the user discount.  Can be either "percent" or "amount".
* **cpq_total**: Total price of the quote after discounts.

#### 7.3.2. Product Group (Line Items in a Quote) System Variables

A product or quote can have one or more product groups, each of which can contain one or more products.  The data for a product group named '{PG}' will be stored in fields starting with '{PG}'.  CPQ specific fields will start with '{PG}\_cpq\_'.  For example, the ID field for a product group named 'line_items' will be stored in 'line_items_cpq_id'.  These fields are as follows.

* **{PG}**: A JSON array of JSON objects, where each object represents a single configured product in the product group.
* **{PG}_cpq_id**: ID of the product group
* **{PG}_cpq_name**: Name of the product group.
* **{PG}_cpq_desc**: Description of the product group.
* **{PG}_cpq_list_subtotal**: Sum of product total list prices (**cpq_list_total_price**) for all products in the product group.
* **{PG}_cpq_system_subtotal**: Sum of product total system prices (**cpq_system_total_price**) for all products in the product group.
* **{PG}_cpq_net_subtotal**: Sum of product total prices (**cpq_net_total_price**) for all products in the product group.
* **{PG}_user_discount_subtotal**: Total percentage user discount for all products in the product group.  This is computed via the formula (**{PG}_cpq_system_subtotal** - **{PG}_cpq_net_subtotal**) / **{PG}_cpq_system_subtotal**
* **{PG}_cpq_system_total**:  **{PG}_cpq_net_subtotal** with product-group system discounts (price-rules) applied.

#### 7.3.3. Product-related System Variables

Each configured product is stored as a JSON object.  Each attribute or product group defined for the product will be a field in this JSON object.

The CPQ specific fields for a product will be stored in the following fields:

* **cpq_id**: ID of the product
* **cpq_name**: Name of the product
* **cpq_desc**: Description of the product
* **cpq_code**: Code (SKU) of the product
* **cpq_quantity**: Quantity of the product
* **cpq_list_unit_price**: List price of a single product unit
* **cpq_list_total_price**: Total list price of the product for the given quantity, without any discounts.
* **cpq_system_total_price**: Total list price of the product for the given quantity, after system (price-rule) discounts are applied.
* **cpq_user_discount**: User entered discount of the product
* **cpq_user_discount_type**: Type of the discount.  Can be either "percent" (percent) or "amount" (fixed amount).
* **cpq_net_total_price**: Total price of the product for the given quantity, after both system and user discounts are applied.

Additionally, the following special variables are defined

* **this**: The object that the condition is attached to.

#### 7.3.4. OpenTBS Variables in Document Templates

The same JSON-style references to variables can be used in the Microsoft Word or other supported Office documents, as placeholders for their respective values in Quote and Contract Document Templates. The CPQ system will process and substitute these variables with their respective values at run-time during the production of a finalized document. Refer to the **Quote and Contract Documents** section above for more details.

#### 7.3.4.1 Macro syntax

The source files in document template sections will use [Open TBS](http://www.tinybutstrong.com/opentbs.php?doc) for macro expressions.  The macro expressions have the form `[{block-name}.{field-name};{options}]`, where `{block-name}` is the name of a section or block of data, `{field-name}` is the name of an input in that block, and `{options} are OpenTBS options for formatting the expression or expanding the macro,

All top-level inputs in the quote are accessible using the `q` block.  For example, the effective data can be accessed by the macro `[q.cpq_eff_date;frm=’mm/dd/yyyy’]`, (the `;frm=’mm/dd/yyyy’` part is OpenTBS option describing how to format the date).

Any input in a table, such product groups, are accessed by using the table's name as the block name.  For example, to access the net price for an element in the `line_items` product group, use the macro `[line_items.cpq_net_total_price;frm=’$ 0,000.00’]`.  Note that to get the table row to expand properly in the document to list all product group items, one of the items in the row must have the OpenTBS option ';block=tbs:row'

### 7.4 Example Rule Expressions

#### 7.4.1 Example Rule Trigger Expressions

Here are some example expressions used in rule triggers.

* Trigger if product with product code 'apple' is in quote:<br/>
  `HAS_PROD('apple')`
* Trigger if product with product code 'apple' is in quote but not product with code 'bananas':<br/>
  `HAS_PROD('apple') && ! HAS_PROD('bananas')`
* Trigger if there is no product in category 'fruit' in the quote:<br/>
  `! HAS_CAT('fruit')`
* Trigger if Line Items Table 'line_items' has a quantity less than 5 of a product with code 'oranges':<br/>
  `PROD_QTY('oranges', 'line_items') < 5`
* Trigger if custom input named 'B' is less than custom input named 'C':<br/>
  `B < C`
* Trigger if the total discount is greater than 10%:<br/>
  `line_items_cpq_user_discount_subtotal > 10`

#### 7.4.2 Example value expressions

Here are some example expressions used to compute values for read-only form inputs.

* Multiple input 'X' containing a price with an input 'Y' containing a percentage discount and round it to the nearest penny:<br/>
  `ROUND(X * Y / 100, 2)`
* If switch input 'F' is set to 1 ('Yes'), return 'X' plus the value 'Y, else return just 'X':<br/>
  `IF(F = 1, X + Y, X)`
* Add 30 days to the date input 'D':<br/>
  `DATEADD(D, 30, 'd')`
  
## 8. XML Specifications (For Advanced Admin Users Only)
 
The CPQ System provides powerful mechanisms for power users (or developers) to get fine grain control of Product and Quote UI Layouts via the  XML specifications. Please note that XML specifications are intended only for use by developers and users who understand and are familiar with XML. Since there are powerful XML editors available as developer tools, these UI Layouts can be modified by hand in your XML editor of choice by first exporting them out of the CPQ System and later importing the modified versions.

### 8.1 Accessing the XML Specifications

Product UI Layouts (see Section 3.2) include an XML tab which exposes the XML Specification. See the screenshot below:
![Product UI Layout XML Tab in MobileForce CPQ](/zendesk_images/ProdUILayoutXML.png)

Clicking on the XML tab, exposes the XML Specification for the Product UI Layout, as seen below:
![Product UI Layout XML Specification in MobileForce CPQ](/zendesk_images/ProdUILayoutXMLSpec.png)

Similarly, Quote UI Layouts (see Section 4.1) include an XML tab which exposes the XML Specification. See the screenshot below:
![Quote UI Layout XML Tab in MobileForce CPQ](/zendesk_images/QuoteUILayoutXML.png)


Clicking on the XML tab, exposes the XML Specification for the Quote UI Layout, as seen below:
![Quote UI Layout XML Specification in MobileForce CPQ](/zendesk_images/QuoteUILayoutXMLSpec.png)

### 8.2 Structure of Forms

In MobileForce CPQ, forms are the underlying common representation used to specify Product and Quote UI Layouts. A form is specified primarily by two XML elements: the **form element** and the **input element**. A form element represents a single form. It contains a list of input elements. Each input element describes a single field in the form.

A form specification is an XML document with the following XML elements (tags).

* **form**: Top level element. This element specifies what actions to perform when the form is submitted. The child elements of this object specify the fields to display in the form.
* **data**: Standard ADL property data section. Only form elements can have a data element.
* **prop**: A single property under a data element. This is the standard ADL prop element and represents a single key/value pair.
* **formsection**: This element represents a collection of related input fields.
* **row**: This represents a single row of fields in a section.
* **col**: This represents a single column in a row of fields.
* **input**: This element represents a single input field.

The screenshot above, of a quote UI Layout shows the various sections of the quote UI Layout form.

Form elements may contain an optional data element, followed by zero or more type elements, then followed by zero or more input elements, and then followed by zero or more formsection elements.

### 8.2 Input Elements in Forms XML Specification

An input element represents a single field input. It may be either directly underneath a form element, or within a formsection element. The input element may have the following common attributes:

* **name**: (Required) Unique name for this field. It must be made up of only alphanumeric characters or '_' characters, (more exactly, it must be a legal variable name.) The name must be unique for the enclosing table. Duplicate fields across tables are allowed. This field will not be displayed to the end user.
* **type**: (Required) Type of the field. The type must be one of the following values:
* **text**: Field is an arbitrary string. A single-line input element should be displayed for this field.
* **password**: Field is a password string.
* **email**: Field contains an email address.
* **tel**: Field contains a phone number.
* **mobile**: Field contains a phone number. This phone number is for a mobile device that accepts text messages.
* **number**: Field contains an signed integer.
* **decimal**: Field contains a signed number. Decimal points are allowed.
* **currency**: Field contains an positive number. Decimal points are allowed.
* **percent**: Field contains a positive integer between 0 and 100.
* **slider**: Field is a slider.
* **textbox**: Field is an arbitrary string. A multi-line text box should be displayed for this field.
* **checkbox**: Field is a boolean and should be displayed as a checkbox. If the checkbox is set, this submitted value for this field will be "1". Otherwise, "0" will be submitted.
* **switch**: Fields is a boolean and should be displayed as an off/on switch. If the switch is set to "on", the submitted value for this fields should be "1". Otherwise, "0" will be submitted.
* **picklist**: Field can take one of several values. If possible, it should be displayed as a drop-down list
* **radio**: Field is a sub-type of the 'picklist' field type where the items are displayed as a vertical list of radio buttons.
* **togglebutton**s: Field is a sub-type of the 'picklist' field type where the elements are displayed as a horizontal list of toggle-buttons.
* **multipicklist**: Field can take zero or more values from a list of values. If possible, this list of values should be displayed as a vertical list of checkboxes.
* **date**: Field contains a date.
* **time**: Field contains the time of day.
* **datetime**: Field contains both a date and a time of day.
* **file**: Field contains the name of a file to be uploaded.
* **imageurl**: Field contains the URL of a displayable image. The image itself will be displayed when the field is disabled or read-only. When editable, it will be displayed as a text box with an associated image preview.
* **header1**: Read-only field representing a section header. Only the label is displayed and the label spans the full width of the screen. The name and value fields are ignored.
* **header2**: Read-only field representing a sub-section header. Only the label is displayed and the label spans the full width of the screen. The name and value fields are ignored.
* **info**: Read-only field representing read-only informational text. Only the label is displayed and the label spans the full width of the screen. The name and value fields are ignored.
* **image**: Read-only field representing an image to display in the form. The image will be centered and take up the full width of the form. The URL of the image is in the value field. For autoforms generated in HTML, the label field will contain the alt text for the image. The label field is ignored for native screens. The name field is ignored.
* **separator**: Read-only field representing a textual separator displayed between other fields on the same line and column. The displayed value is in the label attribute.
* **hidden**: This field is read-only and not displayed to the user.
* **readonly**: Read-only field. The label is displayed like most other fields. The value is displayed as plain text in the field portion of the form. This field is useful for displaying non-editable formula results.
* **type**: This input is a complex data type. The name of this complex type is specified by the subtype attribute.
empty: This input is an empty placeholder. It is typically used to specify that a particular column should be blank for a given row.
buttonlink: This input is displayed as a button whose label is the label attribute. Clicking on this button will cause the form to go to the URL specified in the value attribute.
* **hidden**: If set to a non-empty and non-zero value, then this field will not be displayed to the user. Formulae can be used in this attribute.
* **label**: Label to be display to the end user.
* **listitems** : List of possible values for a picklist or multipicklist input types or one of their subtypes. It is required for these input types. It is ignored for other input types. The value of this attribute take the format "value1|label1|value2|label2|...".
* **required**: If set to a non-empty and non-zero value, then the value of this field cannot be null or the empty string.
* **value**: Initial value for this input. Formulae can be used in this attribute for some input types, ("readonly" and "hidden").


### 8.3 Input Types in Forms XML Specification

The various input types supported in Forms convey the richness of the MobileForce Forms Engine that is the underlying basis for CPQ. The supported input types are categorized as follows:
* **Text Fields**: These include text, multi-line text, password, email address, phone number, mobile phone number, and URL address.
* **Numeric Fields**: These include number, decimal, percent, currency, slider, and range (now deprecated).
* **Date/Time Fields**: These include date, time, and datetime.
* **Selection Fields**: These include picklist, multi-picklist, toggle buttons, radio buttons, switch, one radio button, and checkbox.
* **Resource/Type Fields**: These include file, image url address, map point, map region, signature, color, and user-defined type.
* **Read Only Fields**: These include read-only, and hidden fields.
* **UI Elements**: These include section header (now deprecated), sub-section header, informational, image, separator, empty placeholder (now deprecated) and button.

The following screenshots show the input type selection options for form fields.

![Text, Numeric, Date/Time, and Selection Input Field Types](/zendesk_images/InputTypeA.png)

![Resource/Type Fields, Read-only Fields, UI ELements](/zendesk_images/InputTypeB.png)


### 8.4 Using Forms XML Specification to control Quote Layout

Here are some layout controls that can be specified in XML to control Quote Layouts. Please note that this section is not intended to be a complete documentation, nor do we suggest that you use the XML specification, unless you're a power user/developer. If you'd like additional details about how to control Product and Quote UI Layouts using XML, please contact your MobileForce Support Team and request a paid developer consultation.

**Display read-only text in quote screens**

XML Inputs of type read only text or textarea can be used to display fields that are meant to be read-only. However, there are other ways to do this and these other methods have some additional benefits.

There are two informational input types named **‘Informational’** and **‘Separator’**.

The ‘Informational’ input type spans the entire width of the column.  So if you don’t want the ‘label: input’ format, where the label takes the first third of the column, you can use this input type instead.

The ‘Separator’ input type acts like a read-only text input, except that its value isn’t saved in the form. 

Input Labels, Column Labels, Informational inputs, and Separator inputs support limited styling, such as colors, bold, italics, and font-awesome icons.

Here are some examples: 

* [b]Bold text[/b]
* [I]Italic text[/I]
* [color=#ff333]Red text[/color]
* [color=#dd8800]Orange text[/color]
* [color=#00cc00][fa-check][/color]: A green checkmark
* [color=#cc0000][fa-times][/color]: A red X.
* [br]: line break
* [nbsp]: Non breakable space

There are also some field layout tricks you can use.  You can display multiple inputs side by side in a column by setting the ‘Column Width’ field.  The column width takes percentages.  So, you can show two fields side by side, such as a start and end date, by putting two inputs in a column and setting each input’s column width to 50%.  This also works on separator inputs.

Separator and informational inputs support conditional hiding.  So, one can build conditional warning messages.  Or you can conditionally show and hide status icons by using separator inputs with font-awesome icons.
