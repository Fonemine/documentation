# Configure, Price, Quote Admin Guide
An important aspect of the sales process for any business is the systematization of the processes encompassing pricing of products or services that the business sells. In a typical sales process, setting a price for a product not only impacts the profit margins and market share, it also streamlines the process of product discounts and uplifts in response to market conditions. The basic list of products and their prices is a Price Book, often the starting point of all CPQ systems.

## Price Books

Typically, the first thing a CPQ Administrator does is to create one or more price books. 
MobileForce CPQ supports the creation of multiple price books that can also be related to one another via a hierarchical parent relationship. For instance, Businesses could create one price book for local or national use with the local currency, and another price book for each international market they operate in (each with its own currency). Price books allow one to assign different prices for products for different regions with different currencies or for different markets. In order to create a quote, a user **must** select a price book.

![Create Price Book in MobileForce CPQ](/images/add_edit_price_book.png)

Each MobileForce CPQ price book has a (required) **name** field. In addition, price books typically have the following fields:

* **Currency**: specifying the currency used for all prices in the price book. For now, only "USA" is activated as default as a valid value for the currency field.

The following fields of a MobileForce CPQ price book are found in almost all CPQ entities. For brevity, they are described once here, and not described again in other entities that also have these fields. 

* **Effective Date**: The date starting which  products listed in the price book can be sold
* **Expiration Date**: The date after which products listed in the price book can no longer be sold.
* **Active**: a toggle indicating whether the price book is ready for use in CPQ systems or is still being developed.
* **ACL**: indicating the user roles for the users that are allowed access to the price book. For instance, the US price book may be accessible only by sales user roles who are employed and selling within the USA, and hence not accessible to sales reps who are not members of the sales-USA role, because they sell in the Japan market.

Once a price book is created, the next step is to create product categories,then create products and services within their respective product categories.
Finally we create pricing for the products where we specify the price specific to one or more price books to reflect the different prices for the product in the different markets that these different price books represent.

## Products/Services

A product/service is anything that is sold by the business, irrespective of whether it has a price. Typically products are individual **line items** in *quotes*.
When an end-user creates a new Quote, they can add one or more products

Products may contain nested products, representing bundled products or product features. Such nested products are stored in objects known as product groups. Products may also have attributes, (e.g., color). Rules can be specified on products to ensure valid configuration. To ease the management of products in the product catalog, products are organized in hierarchical categories.

Products can be broken down into two types: **Simple** and **Configurable**. Simple products have no attributes nor nested products. Configurable products may have attributes, nested products, or both. Configurable products have an associated **Product UI Layout** describing their attributes, nested products, and UIs that will be rendered to the end-user to configure the product after they have added it to the quote.

### Product Categories

Product Categories in MobileForce CPQ are hierarchal groupings of products. A product category can be nested within another category. Products can belong to multiple product categories. For a product to be usable, it must belong to at least one product category.

![Create Product Category in MobileForce CPQ](/images/add_product_category.png)

Each MobileForce CPQ Product Category has a (required) **name** field. In addition, it can have a **Parent** field, indicating the product category hierarchy to which this product category belongs. Additional optional fields include **description** and **Image**.


### Products, Configurations and Rules

Each product in MobileForce CPQ is specified through a UI consisting of 4 sections.

1. General Section: 
This section includes the (required) **name** field, and in addition, the unique product code or SKU.
An optional field, "Product Category" is used to provide one or more previously created product categories that the product belongs to.
Additional optional fields include **description** and **Image**.  

![Create Product General Section in MobileForce CPQ](/images/add_product_general.png)

2. Configuration Section: This section describes whether the product is a simple or a configurable product and in each case, additional configuration attributes.

The following fields are required:

**type** indicating whether this product is simple or can be configured. That is, whether this product has editable attributes.

The quantity attribute has the following fields:

1. **editable** : Boolean indicating whether the quantity field is editable by the user. By default, it is 0, (editable).
2. **Default**: Default value of the quantity. By default, it is 1.
3. **Minimum quantity** : Minimum allowed value of the quantity. By default, it is 1.
4. **Maximum quantity** : Maximum allowed value of the quantity. By default, it is 1,000,000.
5. **Unit of Measurement** : This is an optional string to display after a quantity. Example values are ea, users, ft, lbs.
6. **Multiply with Parent Product's quantity** : Boolean indicating whether the final quantity should be this product's quantity times the parent product's final quantity. For example, if one adds 3 PC computers with 2 hard-disks each, the quote should use a final quantity of 6 to compute the price. By default this field is 0, (false).
7. **QuantityStep** : Numerical step value of the quantity. An entered quantity must be an integer multiple of the step. This step can be fractional, (e.g., 0.01). By default, it is 1.

![Create Product Configuration Section in MobileForce CPQ](/images/add_product_configuration.png)

3. Pricing Section: This section specifies the different ways that the product can be priced.

* **priceRecurrence**: Specifies how often the user is charged.  Can be one of the following:
  * **oneTime**: Price is applied only once.
  * **perMinute**: Price is applied per minute.
  * **hourly**: Price is applied per hour.
  * **weekly**: Price is applied per week
  * **biweekly**: Price is applied every two weeks.
  * **semimonthly**: Price is applied twice a month.
  * **monthly**: Price is applied once a month.
  * **quarterly**: Price is applied every three months.
  * **halfYearly**: Price is applied twice a year.
  * **yearly**: Price is applied once a year.
* **Allow Discount**: Boolean indicating whether the user can specify a discount for this product.
* **discount Unit**: Unit type of discount.  Can be one of the following
  * **amount**: Discount is a fixed amount.
  * **percent**: Discount is a percentage.
  * **both**: Discount can be either a fixed amount or percentage.  The sales rep will select the type in the quote.

If the discount unit is percentage, then two additional fields provide the range of allowed discount percentage.

* **discount Percentage Min**: Minimum percent discount that a user can enter.  Default is 0.
* **discount Percentage Max**: Maximum percent discount that a user can enter.  Default is 100%.

If the discount unit is an amount, then two additional fields provide the range of allowed discount amount.

* **discount Amount Min**: Minimum fixed discount that a user can enter.  Default is 0.
* **discount Amount Max**: Maximum fixed discount that a user can enter.  Default is 1,000,000.

![Create Product Pricing Section in MobileForce CPQ](/images/add_product_pricing.png)

The price book entries sub-section within pricing section enables the product pricing to be specified in multiple price books. The following UI describes how this is done. First, the price book for which pricing is being provided is specified. Next, the product is specified. Both are required fields.
Under "Prices" sub-section, the two fields that can be specified are **List Price** and **Method** 

* **method**: Method to use to compute the product's subtotal from the product's quantity.  It can be one of the following:
  * **flatFee**: Subtotal is a flat fee.  Quantity is ignored.
  * **perUnit**: Subtotal is the list price multiplied by the quantity.
  * **volume**: Subtotal is determined by looking up the list price from the price matrix, then multiplying it by the quantity.
  * **tiered**: Similar to the **volume** method except the subtotal is computed by summing up the per tier prices.  For example, if tier 1 is $10 for 1-50 items and tier 2 is $8 for 51-100 items, then the price for a 70 items would be 50 x $10 + 20 x $8 = $660.  This is different from the **volume** method, where the subtotal would be 70 * $8 = $560.
  * **block**: Similar to the **volume** method except the value read from the table is not multiplied by the quantity.  For example, if the table has $500 for 51-100 items, then the subtotal for 70 items will be $500.
* **listPrice**: Unit price for the product.  Used by the **flatFee** and **perUnit** methods.

#### Price book item tier

For the **volume**, **tiered**, and **block** methods, the price book item will have an associated matrix of prices, which provide a list price for a given range of quantities.

Each row in this matrix will have the following fields.

* **id**: Internal unique numerical ID for this table row.
* **priceBookItemId**: Id of the price book item owning this tier
* **from**: Start quantity of this tier.
* **to**: End quantity of this tier.
* **listPrice**: Unit price for this tier.

![Create Product Pricing Section in MobileForce CPQ](/images/add_product_pricing_pricebook.png)



4. Approval Section: Here, one can specify the rules that are used to decide how the product pricing in a quote is approved. 

![Create Product Approval Section in MobileForce CPQ](/images/add_product_approval.png)

The individual approval rules are specified as follows. Each rule has the following **required** fields:

* **Name** : A descriptive name for the quote approval rule
* **Rule Evaluation Order** : A number indicating the order in which multiple rules are evaluated: higher numbered rules are evaluated first, followed by lower numbered rules.
* **Approval Request Email Template** : an email template used to send a request for approval of the quote.
* **Approval Request Cancel Template** : an email sent to an approver to indicate that an approval has been cancelled.
* **Approvers** : A comma separated list of email addresses of users that can approve the quote. These users will be notified on approval requests.
* **Approval Reason** : User-friendly description why the quote needs approval. This description can contain macro expressions using fields from the quote. These macro expressions written as ${expr} where expr is a valid expression.

In addition, the following **optional** fields can be specified.

* **Skip later rules after trigger** : Once a specific rule is triggered, this toggle enables the remaining rules to be skipped. The default is that the remaining rules are not skipped, and instead evaluated.

![Create Product Approval Rule in MobileForce CPQ](/images/CPQApprovalRule.png)

#### Rules 

Products and quotes may have one or more rules.  A rule specifies an automated action that should be performed on a
product or quote when some event occurs on that product or quote.

#### Rule table

In addition to the common database fields described above, a rule will have the following fields:

* **sourceType**: Type of the source object that this rule is associated with.  This type may be one of the following:
  * **Product**: The rule is associated with a Product
  * **Quote**: The rule is associated with a Quote
* **sourceId**: ID of the source object this rule is associated with.
* **scope**: Scope or context for this rule.  Rules in different scopes will be executed independently of each other.  That is, a triggered rule in one scope cannot affect the triggering of another rule in another scope.  This can be one of the following values:
  * **configuration**: This rule is invoked as part of configuration validation.
  * **pricing**: This rule is invoked as part of pricing validation or computation.
  * **approval**: This rule is invoked to determine whether approvals are needed.
* **triggerType**: The type of the event that triggers this rule.  Can be one of the following:
  * **pageLoad**: This rule should trigger whenever the page is first loaded.
  * **save**: This rule should trigger whenever the user saves the source object.
  * **validate**: This rule should trigger whenever the user request validation for the source object or performs an action that requires validation.
  * **updateProductGroup**: This rule should trigger whenever a product is added to or deleted from a product group.
  * **updatePrice**: This rule should trigger when prices are computed or recomputed in the quote.
  * **action**: This rule should trigger whenever the user performs a user-defined action.  The name of the action is specified in the **triggerAction** field.
  * **checkApproval**: This rule should be triggered whenever the cpq_needs_approval field needs updating.  Generally, this is done any time whenever the quote needs to perform a server-side operation, (i.e., any of the above **triggerType** values).
  * **any**: This rule should be triggered for any event listed above.
* **triggerAction**: Name of the user-defined action that should trigger the rule.  This field is ignored if the **triggerType** field is not **triggerAction**.
* **triggerCondition**: An ADL Form expression that should be evaluated to determine whether the rule should trigger or not.  The syntax of this expression is described later.
* **triggerParams**: A JSON object specifying additional parameters in determining whether to trigger this rule.  The meaning of these parameters vary based on the value of the **triggerType** field.
* **triggerOrder**: A number specifying the order in which rules should be evaluated.  Rules with a lower order value will be evaluated before rules with a higher order value.
* **triggerStop**: A boolean value.  If set to true, then if this rule is triggered, no more rules will be checked.  That is, if there are two rules A and B that can be triggered when an event occurs, if **triggerStop** is true for A, rule evaluation will be stopped after A and rule B will never be evaluated.  Note that **triggerStop** only prevents execution of roles in the same scope.  Rules in other scopes will still be executed.
* **actionType**: Type of the action to perform if the rule triggers.  Can be one of the following values:
  * **fatal**: Generate an error message and abort the triggering operation.  Also perform no more rule checks.  This option is intended for developers only and should be only be used for serious, un-recoverable errors.  For most cases, one should use the **error** option below instead.  End users should not be allowed to select this option.
  * **error**: Generate an error message and abort the triggering operation.
  * **warning**: Generate an warning message.  The triggering operation will not be aborted.
  * **info**: Generate an informational message.  The triggering operation will not be aborted.
  * **debug**: Generate a debugging message.  The triggering operation will not be aborted.  This option is intended for developers only.  End users should not be allowed to select this option.
  * **addProduct**: Automatically add a product to the parent product or quote.
  * **deleteProduct**: Automatically delete a product to the parent product or quote.
  * **addDiscount**: Automatically add a pricing discount to the parent product or quote.
  * **needsApproval**: Mark this quote as needing approval.
* **actionParams**: A JSON object specifying additional parameters needed to peform the action.  The meaning of these parameters vary based on the value of the **actionType** field.

#### Trigger condition syntax

Trigger conditions in rules will use the formula syntax specified the [[ADL Form Objects]] document.

##### Formula variables

One can access any attribute, group, or CPQ-computed value using the naming syntax described in the previous section.

Additionally, the following special variables are defined

* **this**: The object that the condition or formula is attached to.

##### Formula functions

In addition to the standard ADL Form Object formula functions, the following functions will be supported:

* **PROD_COUNT(productCode [, productGroup])**: Returns a count of all products with the given code in the named group.  If the group name is missing, then this is for all groups.
* **PROD_QTY(productCode [, productGroup])**: Returns a the sum of the quantities of all products with the given code in the named group.  If the group name is missing, then this is for all groups.
* **HAS_PROD(productCode [, productGroup])**: Returns true if there is a product with the given code in the named group.  If the group name is missing, then this is for all groups.  This is basically just a shorthand for `(PROD_COUNT(productCode, productGroup) > 0)`.
* **CAT_COUNT(categoryName [, productGroup])**: Returns a count of all products in the given category in the named group.  If the group name is missing, then this is for all groups.
* **CAT_QTY(categoryName [, productGroup])**: Returns a the sum of the quantities of all products in the given category in the named group.  If the group name is missing, then this is for all groups.
* **HAS_CAT(productCode [, productGroup])**: Returns true if there is a product in the given category in the named group.  If the group name is blank, then this is for all missing.  This is basically just a shorthand for `(CAT_COUNT(productCode, productGroup) > 0)`.
* **QTY([productGroup])**: Returns a the sum of the quantities of all products in the named group.  If the group name is missing, then this is for all groups.

#### Rule trigger parameters

This section describes the allowed parameters in the **triggerParams** JSON object field of a rule.  The parameters allowed  vary based on the value of the **triggerType** field.

##### updatePrice trigger parameters

* **priceBook**: If specified, then this rule will only be applied to quotes that use this named price book.
* **stage**: This identifies at what time during the pricing computation that this rule should be executed.  This field can take one of the following values:
  * **lineItemSubtotal**:  This rule will be evaluated just after the subtotal (cpq_list_total_price) for a single line-item is computed, just before user-specified discounts are applied.
  * **lineItemTotal**: This rule will be evaluated just after the net price (cpq_net_total_price) for a single line-item is computed.  
  * **productGroupSubtotal**: This rule will be evaluated just after the subtotals for a product group are computed.
  * **quoteStart**: This rule will before any pricing computations in the quote have been performed.
  * **quoteEnd**: This rule will after all pricing computations in the quote have been performed.

##### checkApproval triggerParameters

* **watchedInputs**: Comma separated list of quote input fields that will be watched by this rule.  When a rule is approved, the values of all watched inputs will be saved.  If the quote is later modified, the rule will not be triggered unless one of the watched inputs change since the last approval.

#### Rule action parameters

This section describes the allowed parameters in the **actionParams** JSON object field of a rule.  The parameters allowed  vary based on the value of the **actionType** field.

##### Error action parameters

* **message**: Error message to display to the user.

##### Warning action parameters

* **message**: Informational message to display to the user.

##### Info action parameters

* **message**: Informational message to display to the user.

##### addProduct action parameters

* **product**: Name of the product to add to the parent product or quote.  If this product is already present, no action is taken.
* **group**: Name of the product group to add the product to.

##### addDiscount action parameters

* **label**: Label to display for this discount in the quote
* **disUnit**: Unit type of discount.  Can be one of the following
  * **amount**: Discount is a fixed amount.
  * **percent**: Discount is a percentage.
* **disMethod**: Method to use to compute the discount.  It can be one of the following:
  * **fixed**: Discount is a fixed value read from the **disValue** field.
  * **formula**: Discount is computed from the **disFormula** field.
* **disValue**: Amount of the discount.
* **disFormula**: ADL form expression to use to compute the discount

##### needsApproval action parameters

* **reason**: User-friendly description why the quote needs approval.  This description can contain macro expressions using fields from the quote.  These macro expressions written as `${expr}` where `expr` is a valid ADL form expression.
* **approver**: Approver Group that needs to approve this quote.
* **requestTemplate**: Email template for the approval request.
* **requestCancelledTemplate**: Email template sent to approvers when the request is cancelled.


### Product UI Layouts: TODO HERE ONWARDS

## Quotes. 
### Quote UI Layouts

Each quote in MobileForce CPQ is specified through a UI consisting of 5 sections.

1. General Section

![Create Quote General Section in MobileForce CPQ](/images/add_edit_quote_ui_layout_general.png)

2. Types Section

![Create Quote Types Section in MobileForce CPQ](/images/add_edit_quote_ui_layout_types.png)

3. Forms Section

![Create Quote Forms General Section in MobileForce CPQ](/images/add_edit_quote_ui_layout_form_general.png)

![Create Quote Forms Quote Section in MobileForce CPQ](/images/add_edit_quote_ui_layout_form_quote.png)

![Create Quote Forms Approvals Section in MobileForce CPQ](/images/add_edit_quote_ui_layout_form_approvals.png)

![Create Quote Forms Signature Section in MobileForce CPQ](/images/add_edit_quote_ui_layout_form_signatures.png)

![Create Quote Forms Signature Section in MobileForce CPQ](/images/add_edit_quote_ui_layout_form_generated_docs.png)


4. Actions Section

![Create Quote Actions Section in MobileForce CPQ](/images/add_edit_quote_ui_layout_form_action.png)


5. Summary Section

![Create Quote Summary Section in MobileForce CPQ](/images/add_edit_quote_ui_layout_form_summary.png)


### Quote Templates and Rules

## Approvals
### Approver Groups
### Email Templates

## Contract Documents
A sales contract is a formal agreement between the seller and a buyer, where the seller provides products or services, for payment or a promise of payment from the buyer. Since sales contracts cover legal aspects of a sale, they often have distinct sections such as legal provisions (state laws and arbitration) as well terms and conditions of the sale. In order to simplify the creation of sales contracts, document templates are used. These templates contain customizable sections that provide the presentation of sales  records such as line items, signature fields, and terms and conditions. The sections can be included or excluded.

Starting from a quote, MobileForce CPQ can generate a set of documents. Each document is generated from a document template which contains one or more sections. Each section has an associated MS word or excel file containing macro variables that are expanded upon generation. Users  have the option to include or exclude sections from the document.

### Template Files


### Document Templates

The following document template is used to generate a proposal for a customer that is based on their use of SugarCRM CRM. This document template has the following sections

Each MobileForce document template has a (required) **name** field. In addition, document templates typically have the following fields:

![Create Proposal with quote in MobileForce CPQ](/images/sugarcrm_proposal_document_template.png)

* **Owning Quote**: the quote from which the proposal is being generated
* **Quote must be valid**: a toggle which ensures that only valid quotes can be used to generate a proposal. If set to true, and the owning quote is not a valid quote, then the proposal will not be generated. By default, it is set to True.
* **Can generate when locked**: a toggle which if set to true permits the proposal to be generated from this template even if the current quote instance is locked. By default, it is set to True. 
* **Hidden Condition** : An optional  Form expression that should be evaluated to determine whether this document template should be displayed when displaying the list of documents that can be generated.
* **Disabled Condition** : An optional  Form expression that should be evaluated to determine whether this document template should be disabled, (i.e., shown but unselectable), in the list of documents that can be generated.

* **Generated File Format** : Format of the target document generated from this template. Can be one of the following:

  * docx: A MS Word document. Templates using this format can only have one section. Additionally, that section's template file must be a MS Word document.
  * xlsx: A MS Excel document. Templates using this format can only have one section. Additionally, that section's template file must be a MS Excel document.
  * pdf: A PDF document. Templates using this format can have one or more sections.

* **Generated Filename** : File name of the generated document.

* **Generated File ACL** : Access Control List (ACL) for the generated document. Users that are authorized by this ACL can view the generated document. Note that this is different than the acl field for this object, which identifies which users can generate the document.

* **Generated File Hidden Condition** : An optional ADL form expression which will determine if the generated document will be visible to the user.

* **Document Sections** : the various sections in the document template, indicating the order in which they appear, and whether they are optional or not. Furthermore, each section has an associated filename, which describes the file from which the section is generated. Different sections can use different files.
 Document template sections  have the following required fields:
 
 ![Create section in document template for a proposal in MobileForce CPQ](/images/add_edit_proposal_document_template_section.png)

  * **Name** : Displayed name for this section.
  * **Order** : Order of this section within the parent document template. Sections within a document template are ordered by this field in ascending order.
   * **SourceFilename** : Name of the template file to use to generate this section. This file must be either a MS Word file, a MS Excel file, or a PDF file. If this is a MS Word or Excel file, it can include macro expressions.
   
In addition, the following optional fields are supported in a document template section:

  * **hidden condition** : An optional  form expression which determines whether this section should be hidden from the user. Hidden senctions will never be included in the generated document.
  * **Optional** : Boolean value indicating whether the user is allowed to exclude this section from the document on document generation. 
 
## CPQ Functions and Variables
### Built-in Variables
### Built-in Functions
### OpenTBS Variables in Document Templates
