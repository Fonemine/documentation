# Configure, Price, Quote Admin Guide
An important aspect of the sales process for any business is the systematization of the processes encompassing pricing of products or services that the business sells. In a typical sales process, setting a price for a product not only impacts the profit margins and market share, it also streamlines the process of product discounts and uplifts in response to market conditions. The basic list of products and their prices is a Price Book, often the starting point of all CPQ systems.

## Step 1: Price Books

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

## Step 2: Product/Service Categories

Product/Service Categories in MobileForce CPQ are hierarchal groupings of products or services that are configured and sold to the customer. 

In the MobileForce CPQ UI, it is simply called a **Product Category** to represent both products and service categories. 

A product or service category can be nested within another category. Products/Services can belong to multiple categories. For a Product/Service to be usable and added to a Quote, it must belong to at least one category.

![Create Product Category in MobileForce CPQ](/images/add_product_category.png)

Each MobileForce CPQ Product Category has a (required) **Name** field. In addition, it can have a **Parent** field, indicating the product category hierarchy to which this product category belongs. Additional optional fields include **Description** and **Image**.

## Step 3: Products/Services

A product/service is anything that is sold by the business, irrespective of whether it is free or has a price. A product/service belongs to a category. Typically products are individual **line items** in *quotes*. When an end-user creates a new Quote, they can add one or more products or service items by browsing or searching this catalog.

In the MobileForce CPQ UI, a Product/Service are collectively simply called a **Products** to represent both product and service items.

A product item in this catalog can represent a physical product, a software product or a virtual/online product or a recurring subscription product. Similarly, a service item can represent a one-time setup or installation service, a design consultation service, professional services, a maintenance/repair service or a recurring warranty service.

Products may contain nested products, representing bundled products or product features. Such nested products are stored in objects known as product groups. Products may also have attributes, (e.g., color). Rules can be specified on products to ensure valid configuration. To ease the management of products in the product catalog, products are organized in hierarchical categories.

Products can be broken down into two types: **Simple** and **Configurable**. Simple products have no attributes nor nested products. Configurable products may have attributes, nested products, or both. Configurable products have an associated **Product UI Layout** describing their attributes, nested products, and UIs that will be rendered to the end-user to configure the product after they have added it to the quote.

### Products, Configurations and Rules

Each product or service item in MobileForce CPQ is specified through a UI consisting of 4 sections.

###### General Section

This section includes the (required) **Name** field, and in addition, the unique product code or SKU.
An optional field, "Product Category" is used to provide one or more previously created product categories that the product belongs to.
Additional optional fields include **Description** and **Image**.  

![Create Product General Section in MobileForce CPQ](/images/add_product_general.png)

###### Configuration Section

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

![Create Product Configuration Section in MobileForce CPQ](/images/add_product_configuration.png)

###### Pricing Section

This section specifies the different ways that the product can be priced.

- **priceRecurrence**: Specifies how often the user is charged.  Can be one of the following:
 - **One Time**: Price is applied only once.
 - **Per Minute**: Price is applied per minute.
 - **Hourly**: Price is applied per hour.
 - **Weekly**: Price is applied per week
 - **Bi-weekly**: Price is applied every two weeks.
 - **Semi Monthly**: Price is applied twice a month.
 - **Monthly**: Price is applied once a month.
 - **Quarterly**: Price is applied every three months.
 - **Half Yearly**: Price is applied twice a year.
 - **Yearly**: Price is applied once a year.

- **Allow Discount**: Boolean indicating whether the user can specify a discount for this product.
- **Discount Unit**: Unit type of discount.  Can be one of the following
 - **Amount**: Discount is a fixed amount.
 - **Percent**: Discount is a percentage.
 - **Both**: Discount can be either a fixed amount or percentage.  The sales rep will select the type in the quote.

If the discount unit is percentage, then two additional fields provide the range of allowed discount percentage.

- **Discount Percentage Min**: Minimum percent discount that a user can enter.  Default is 0.
- **Discount Percentage Max**: Maximum percent discount that a user can enter.  Default is 100%.

If the discount unit is an amount, then two additional fields provide the range of allowed discount amount.

- **Discount Amount Min**: Minimum fixed discount that a user can enter.  Default is 0.
- **Discount Amount Max**: Maximum fixed discount that a user can enter.  Default is 1,000,000.

![Create Product Pricing Section in MobileForce CPQ](/images/add_product_pricing.png)

The price book entries sub-section within pricing section enables the product pricing to be specified in multiple price books. The following UI describes how this is done. First, the price book for which pricing is being provided is specified. Next, the product is specified. Both are required fields.
Under **Prices** sub-section, the two fields that can be specified are **List Price** and **Method** 

- **Method**: Method to use to compute the product's subtotal from the product's quantity.  It can be one of the following:
  - **Flat Fee**: Subtotal is a flat fee.  Quantity is ignored.
  - **Per Unit**: Subtotal is the list price multiplied by the quantity.
  - **Volume**: Subtotal is determined by looking up the list price from the price matrix, then multiplying it by the quantity.
  - **Tiered**: Similar to the **volume** method except the subtotal is computed by summing up the per tier prices.  For example, if tier 1 is $10 for 1-50 items and tier 2 is $8 for 51-100 items, then the price for a 70 items would be 50 x $10 + 20 x $8 = $660. This is different from the **volume** method, where the subtotal would be 70 * $8 = $560.
  - **Block**: Similar to the **volume** method except the value read from the table is not multiplied by the quantity.  For example, if the table has $500 for 51-100 items, then the subtotal for 70 items will be $500.
- **List Price**: Unit price for the product.  Used by the **Flat Fee** and **Per Unit** methods.

###### Price Book Item Tier

For the **Volume**, **Tiered**, and **Block** methods, the price book item will have an associated matrix of prices, which provide a list price for a given range of quantities.

Each row in this matrix will have the following fields.

- **Id**: Internal unique numerical ID for this table row.
- **Price Book Item Id**: Id of the price book item owning this tier
- **From**: Start quantity of this tier.
- **To**: End quantity of this tier.
- **List Price**: Unit price for this tier.

![Create Product Pricing Section in MobileForce CPQ](/images/add_product_pricing_pricebook.png)


###### Approval Section

Here, one can specify the **rules** that are used to decide how the product pricing in a quote is approved. Note that ONLY individual product-related rules are specified here. Most **rules** are typically specified at the Quote level (see **Quote Templates** under the **Quotes** section below). Product-level rules typically only make sense for **Configurable Products** or products with nested child products.  They only apply within scope of the product itself. You can use them to validate custom fields, (e.g., end date must be less than start date), or make constraints or actions for line tables inside the product. 

![Create Product Approval Section in MobileForce CPQ](/images/add_product_approval.png)

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

## Approvals
### Approver Groups
### Email Templates

## Contract Documents
### Template Files
### Document Templates

## CPQ Rules, Functions and Variables

Products and Quotes may have one or more rules that are used in **Configuration**, **Pricing** and **Approvals**. A rule specifies an automated action that should be performed on a product or quote when some event occurs on that product or quote.

### Rule Expressions and Formula Syntax

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

### Built-in Formula Functions

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

###  Built-in Formula Variables

One can access any attribute, group, or CPQ-computed value using the formula and naming syntax described in the previous section. In the CPQ system, all the variables and values in the entire Quote is stored as a JSON object with nested fields. The top level JSON object will contain data for the entire quote.  Each attribute or product group (line items array) defined for the quote will be a field in this JSON object. So, a standard JSON notation can be used to refer to any variable contained in the quote using nested level references for hierarchy. In general, for non-primitive system or input variables, say, **arrays**, a JSON-object notation can be used to refer to variables inside them. For example: **line_items[1].cpq_quantity** will refer to the value of the Quantity field of the 2nd line item added in the Quote. By convention, the names of all CPQ-specific inputs will be prefixed with or contain 'cpq_'. Users are free to define their own inputs (variables) in **Product UI Layouts** or **Quote UI Layouts** with names that do not have 'cpq_' in them.

###### Quote Level System Variables

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

###### Product Group (Line Items in a Quote) System Variables

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

###### Product-related System Variables

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

* **this**: The object that the condition or formula is attached to.

###### OpenTBS Variables in Document Templates

The same JSON-style references to variables can be used in the Microsoft Word or other supported Office documents, as placeholders for their respective values in Quote and Contract Document Templates. The CPQ system will process and substitute these variables with their respective values at run-time during the production of a finalized document. Refer to the **Quote and Contract Documents** section above for more details.
