# MobileForce Expressions: Language and Usage in Low Code Application Development

The Visual software development constructs in MobileForce Low-code/No-code Platform empower the citizen developer to visually create and connect with drag and drop, application components to easily create powerful enterprise applications. However, there are often situations when someone with development skills (for example, a business analyst) that go beyond the citizen developer, would like to rapidly construct custom forms or  UI elements using expressions to combine existing constructs in a powerful yet fairly composable manner. It is precisely for this purpose that MobileForce Expressions are created as a a powerful enhancement to the MobileForce Low-code/No-code platform. 

MobileForce expressions  extend the automation capabilities of the MobileForce Platform in ways that otherwise could only be achieved by an enterprise software developer, but without the learning and implementation overhead of a software development environment. 
The common expression language defined here is the common foundation, used to create powerful automation features in several different MobileForce products such as CPQ, Forms, and potentially even Field Service. 

Simply put, MobileForce expressions enhance forms with  dynamic functionality that enable dynamic (i.e., at run-time) changes to the **value** of form fields and sections, and in general any  **form elements**. Furthermore, MobileForce expressions also support dynamic modification to the **visibility** and **editability** of form elements. MobileForce expressions are easy to write using plain text fields within various elements of MobileForce Applications such as CPQ, and potentially also Field Service. Within MobileForce CPQ, expressions are specifically used to enhance Rules, Triggers, Macros, Email Templates etc.

When used in CPQ rules, MobileForce expressions specify a trigger condition for a configuration, pricing, or approval rule.  When the trigger condition evaluates to true, the action for that rule is executed.  When used in macro variables, one can specify a MobileForce expression instead of a variable. Please note that MobileForce expressions are much more likely to be used in forms and CPQ rules, and rather lightly used in Macros.  

MobileForce expressions do not exist on their own. Instead, they are treated as attributes of other components such as fields, form sections, or CPQ rules.

In forms, MobileForce expressions are used for:
* Specifying the value of an input
* Specifying whether an input is read only or disabled. 
* Specifying whether an input, section, table, row, column, or tab is hidden.
* Filtering picklist values.

In Quotes, MobileForce expressions are also used for:
* Triggers for configuration, pricing, or approval rules
* Reading email addresses from a form for an approval group.
* Macro variables in email templates or approver emails.
* Filtering document templates
* Control of Visibility of generated docs and doc templates

MobileForce expressions are almost invariably computed on the **client** side: the dynamic evaluation of expressions enables the Form elements within which MobileForce expressions are used to be highly responsive. Form expressions are evaluated locally in the form element to which they are tied, and make no changes to the surrounding context outside the form element. Hence their evaluation does not result in any side effects. MobileForce expressions include not only traditional values, identifiers, and variables combined using operators, but also include some pre-defined functions that enhance expressions. It must be noted that there are a select few pre-defined functions, specifically the **LOOKUPVALUE()** functions, which are actually evaluated on the **server side**, typically as a result of  invocation of database operations, but other than these functions, MobileForce expressions are invariably computed on the client side. Please note also that **Lookup** functions are not supported in CPQ rules or macro variables.


**MobileForce Expression Language (MFEL)**

Often, expressions in MobileForce are used in forms, CPQ rules, triggers, macros, email templates, etc. All of these uses  build upon **MFEL** in unique ways.
In order to define the MobileForce Expression Language, we start with primitives:

## 1. Primitive Values

The following primitive values are used in both **Forms Formula and Expressions** as well as **CPQ Formula, Rules, Expressions, Functions and Variables**.

The only supported primitive values are strings, numbers, and JSON key/value objects.  Numbers will be represented internally as double precision numbers.  Strings will be automatically converted to numbers when necessary and vice versa.  There is no boolean type.  A value is considered to be false if it is the empty string, zero or the string "0".  Otherwise, it is considered to be true.

A JSON key/value object is a string that follows the [JSON object format](https://www.json.org/).  The JSON object must have a "key" and a "value" field.  An example JSON key/value object is `{"key": 1, "value": "One"}`.  The "key" field contains the actual or stored value while the "value" field contains the user-displayable string.  JSON key/value objects are often used for picklist inputs.  For example, a "user" picklist input may have its database ID stored in the "key" field and the user's name in the "value" field.

A JSON key/value value in any arithmetic or conditional expression will be automatically converted to its key.  For example '{"key": 1, "value": "One"}' + 3 will be evluated to 4.

## 2. Form Formula

```abnf
formula              =  "=" expression
```

To allow the dynamic updating of certain fields based on the data provided by other fields, expressions can be used in some of the input attributes. These expressions will always start with a '=' character and are inspired-by/use a subset of MS Excel formula syntax. Only string and numeric scalar data types are supported together with a limited  set of allowed functions. The input fields of formula can be referenced by their names. A formula can only reference input fields that have been specified previously the current input.

Formulae are allowed in the "value" attribute of inputs of type "readonly" and "hidden". Formulae can also occur in the "hidden" and "disabled" attributes for inputs.

Formulae can be used in **FormSection** attributes, specifically the **hidden** and **lock** attributes.
Formulae can also be used in a Row Element or Col Element which represent a row or a column of fields in a section. Specifically, the **hidden** attributes of these elements can include a formula.
Formula can also be used in the Input Attributes of an Input Element, specifically within the **readonly** type field, the **hidden** and **value** fields, **disabled** attribute, the **invalidmessage** attribute, the **listitemfilter**, the **readonly** and the **validate** attributes, 

Now we can define Form expressions as follows: 

### 2.1. Form Expressions

```abnf
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

### 2.2. Form Built-in Functions 

The following built-in functions are supported in MobileForce expressions:

* **ABS(number)**: Return the absolute value of the given number.
* **AND(arg1, arg2, ..._)**: Return the logical AND of the given arguments.
* **IF(cond, then-expr, else-expr)**: If the first argument is true, return the second argument, else return the third argument.
* **INT(number)**: Round the given number down to the nearest integer.
* **MAX(num1, num2, ...)**: Return the maximum value of the given arguments.
* **MIN(num1, num2, ...)**: Return the minimum value of the given arguments.
* **NOT(expr)**: Return the logical NOT of the given argument.
* **OR(arg1, arg2, ...)**: Return the logical OR of the given arguments.
* **ROUND(number [, num-digits])**: Round the given number to the nearest integer.  If `num-digits` is specified, then the specified number of digits after the decimal point will be displayed.
* **SEARCH(needle, haystack [, offset])**:  Return the index of the needle string within the haystack string.  If the needle is not in the haystack, return -1.
* **COUNT(array)**: Returns the count of the number of elements in the given array.
* **SUM(array [, fieldName])**: Returns the sum of all the elements in the given array.  If 'fieldName' is specified, then the array is assumed to be an array of objects instead of an array of numbers.  'fieldName` specifies which field in the array of objects should be summed together.
* **AVG(array [, fieldName])**: Returns the average of all the elements in the given array.  If 'fieldName' is specified, then the array is assumed to be an array of objects instead of an array of numbers.  'fieldName` specifies which field in the array of objects should be averaged together.
* **ARRAY_MIN(array [, fieldName])**: Returns the minimum of all the elements in the given array.  If 'fieldName' is specified, then the array is assumed to be an array of objects instead of an array of numbers.  'fieldName` specifies which field in the array of objects should be read.
* **ARRAY_MAX(array [, fieldName])**: Returns the maximum of all the elements in the given array.  If 'fieldName' is specified, then the array is assumed to be an array of objects instead of an array of numbers.  'fieldName` specifies which field in the array of objects should be read.
* **IN(element, array)**:  Return true if the given element is in the given array.  If the second argument is not an array, then return true if the two arguments are equal.
* **ACLMATCH(acl [, array])**: Return true if the given ACL matches the given array.  The ACL uses MobileForce's ADL ACL syntax.  The array must be an array of strings.  If the second argument is missing, an array of the currently logged in user's roles is used.  
* **CURRENCY_FORMAT(number [, format [, locale] ])**: Format the given number as a currency, using PHP's money_format() function.  The 'format' and 'locale' arguments are deprecated.
* **NUMBER_FORMAT(number [, decimals [, decPoint [, thousandsSep] ] ])**: Format the given number using PHP's number_format() function.
* **DATE_FORMAT(date [, format [, timezone] ])**: Format the given date or date/time using the PHP's date() function.
* **KEY(arg)**: If the given argument is a JSON key/value object, return the 'key' field of the object.  Otherwise, return the argument unchanged.
* **VALUE(arg)**: If the given argument is a JSON key/value object, return the 'value' field of the object.  Otherwise, return the argument unchanged.
* **KEYVALUE(key, value)**: return a JSON key/value object, whose key and value are the given arguments.
* **DATEADD(date, val, unit)**: Adds the given value to the given date or date/time.  'date' must be a valid date or date/time string in ISO-8601 format. 'val' must be an integer.  'unit' identifies the unit-type of the value. 'unit' must be one of: 'y', 'm', 'd', 'w', 'h', 'i', or 's'.  ('m' is months, 'i' is minutes).
* **TODAY()**: Return today's date
* **NOW()**: Return todays's date and time.
* **JOIN(separator, array)**: Returns a string that is a concatenation of the given array values separated by the given separator string.  For example, `JOIN(',', ['A', 'B', 'C'])` will return 'A,B,C'.  If the second argument is not an array, this function will return it unchanged.
* **CASE(value, key1, expr1, key2, expr2, ...)**:  This function acts similar to a switch statement in other languages, or to a nested sequence of IF() form expressions, (that is, `IF(value=key1, expr1, IF(value=key2, expr2, ...))`).  The first argument will be evaluated and will be compared against all even arguments (2x) of the function.  If it is equal to a particular argument (2x), the next argument (2x+1) is evaluated and returned.  Otherwise, the first argument is returned.  For example, `CASE(2, 1, 'a', 2, 'b', 3, 'c')` will return 'b' and`CASE(4, 1, 'a', 2, 'b', 3, 'c')` will return 4.

In addition to forms, MobileForce expressions are also used in CPQ as follows:

## 3. CPQ Formula, Rules, Expressions, Functions and Variables

Products and Quotes may have one or more rules that are used in **Configuration**, **Pricing** and **Approvals**. A rule specifies an automated action that should be performed on a product or quote when some event occurs on that product or quote.

### 3.1. CPQ Rule Formula and Expressions Syntax

CPQ Rule expressions can be composed using a combination of built-in system variables, user-specified custom variables, built-in functions and built-in operators (logical and arithmetic). Rule expressions are modeled after the familiar Microsoft Excel formula syntax.  More exactly, only string and numeric scalar data types are supported and the set of allowed functions are listed below.  The variables in the formula can be referenced by their names.  A formula can only reference variables that are either built-in system variables listed below or input field names that are specified in **Quote UI Layout** or a **Product UI Layout**. 

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

### 3.2. Built-in CPQ Functions

The following standard Microsoft Excel-like functions are supported:


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

###  3.3. Built-in CPQ Formula Variables

One can access any attribute, group, or CPQ-computed value using the formula and naming syntax described in the previous section. In the CPQ system, all the variables and values in the entire Quote is stored as a JSON object with nested fields. The top level JSON object will contain data for the entire quote.  Each attribute or product group (line items array) defined for the quote will be a field in this JSON object. So, a standard JSON notation can be used to refer to any variable contained in the quote using nested level references for hierarchy. In general, for non-primitive system or input variables, say, **arrays**, a JSON-object notation can be used to refer to variables inside them. For example: **line_items[1].cpq_quantity** will refer to the value of the Quantity field of the 2nd line item added in the Quote. By convention, the names of all CPQ-specific inputs will be prefixed with or contain 'cpq_'. Users are free to define their own inputs (variables) in **Product UI Layouts** or **Quote UI Layouts** with names that do not have 'cpq_' in them.

#### 3.3.1. Quote Level System Variables

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

#### 3.3.2. Product Group (Line Items in a Quote) System Variables

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

#### 3.3.3. Product-related System Variables

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

#### 3.3.4. OpenTBS Variables in Document Templates

The same JSON-style references to variables can be used in the Microsoft Word or other supported Office documents, as placeholders for their respective values in Quote and Contract Document Templates. The CPQ system will process and substitute these variables with their respective values at run-time during the production of a finalized document. Refer to the **Quote and Contract Documents** section above for more details.

### 3.4 Expression usage in CPQ

MobileForce Expressions can be used in the following context within CPQ

* Product -> Approval
	* in Trigger conditions
	* in Approval Reason: as macro expressions written using the syntax ${expr}
* Product, Pricing, or Approval Rules
	* in Trigger conditions
	* in Response section
		* action type == "Add Discount"
		* action type == "Needs Approval" : as macro expressions written using the syntax ${expr}
* Approver Groups
	* in email addresses
* Email Templates
	*  the subject and body of email templates can contain macro variables of the form ‘${form-expr}’
* Document Templates
	* in Hidden Condition
	* in Disabled Condition
	* Generated File Hidden Condition
	* SourceFileName

## 4. Lookup Functions 

Finally, we define Lookup functions, which are actually evaluated on the server side (and not the client side). Due to this distinction, lookup functions are extremely powerful, and if used incorrectly, say  by the novice developer, could cause serious unstability and even crash  MobileForce Applications. Thus, lookup functions should be used with caution, and only by expert developers.

### 4.1 Lookup Table

LOOKUP(table [,filter [, column]]) – Lookup up a value from a different datatable table.  Can be used only in external picklist fields.  Not really used anymore.  Only works for form expressions in datatable forms for form apps.

### 4.2 Lookup Value

LOOKUPVALUE(table [,filter [, column]]) – Lookup up a value from a different datatable table.  Can be used in any field, except for some external picklist fields.  Only works for form expressions in datatable forms for form apps. By far, this is the most commonly used of the LOOKUP* functions.

### 4.3 Lookup Key/Value

LOOKUPKEYVALUE(table [,filter [, column]]) – Lookup up a value from a different datatable table.  Meant solely for setting values of external picklist fields.  Only works for form expressions in datatable forms for form apps.

### 4.4 DTLookupValue : DataTable

DTLOOKUPVALUE(param-prefix, table [, filter [, column]]) - Lookup up a value from a different datatable table, using a datatable adapter different from the current datatable screen.  Can be used in datatable forms, form apps, form-config forms, and CPQ quotes. 

## 5 Examples of MobileForce Expressions

In CPQ Product Rules **Condition** :
```
HAS_PROD('7782') && ! HAS_PROD('7779') && (opportunity_type == 'New Business')

(PROD_QTY('7783') > 1 && PROD_QTY('7783') < 50)
	
HAS_PROD('7789') && (! HAS_PROD('7779') || ! HAS_PROD('7792'))

(HAS_CAT('TimeClock: Accessories (NR)') || HAS_CAT('TimeClock: Parts (NR)') || HAS_CAT('TimeClock: Sage (NR)') || 
HAS_CAT('TimeClocks: NXG G2+ Ethernet Clock (NR)') || HAS_CAT('TimeClocks: NXG G2+CN - Cellular Biometric Clock (NR)') || 
HAS_CAT('TimeClocks: NXG G2+EFN - Ethernet Biometric Clock (NR)') || 
HAS_CAT('TimeClocks: NXG G2+WFN - WiFi Biometric Clock (NR)') || 
HAS_CAT('TimeClocks: NXG G2+WN - WiFi Clock (NR)') || HAS_CAT('TimeClocks: NXG G7 Ethernet Biometric Clock (NR)') || 
HAS_CAT('TimeClocks: NXG G7 Ethernet Clock (NR)') || HAS_CAT('TimeClocks: NXG LE (Ethernet) (NR)') || 
HAS_CAT('TimeClocks: NXG LE (Wifi) (NR)') || HAS_CAT('TimeClocks: Touch Clock (NR)') || 
HAS_CAT('TimeClocks: Velocity 800 (NR)') || HAS_CAT('TimeClocks: Velocity 850 (NR)') || 
HAS_CAT('TimeClocks: Virtual Clock (NR)') || HAS_CAT('TimeForce (NR)')) && ((opportunity_type == 'New Business') && HAS_PROD('7796'))
```
In Quote UI Layout **Form** access-control hide-condition

```
In Quote: 

!(HAS_PROD('3709') || HAS_PROD('3712') || HAS_PROD('3706') || HAS_PROD('3714') || HAS_PROD('5409') || HAS_PROD('5410') || HAS_PROD('5408') || HAS_PROD('5407')  || HAS_PROD('5413') || HAS_PROD('5414') || HAS_PROD('5412') || HAS_PROD('5411'))

In Generated Docs: 

cpq_approval_needed || cpq_approval_in_progress || !contact || is_primary == 'no'

In Layouts: making fields READ-ONLY for specific roles: Note the use of single quote (') to demarcate roles since roles can have blank spaces.

ACLMATCH(‘role1’)
!ACLMATCH(‘role2')
ACLMATCH(‘role1 | role2’)
ACLMATCH(‘role1 & role2’)
```

In Quote UI Layouts: Access control to make fields **visible** or **hidden** or **conditional** based on roles that can be combined using MobileForce expressions, i.e., using and(&) as well as or(|). 


In the case of **conditional** visibility , a condition can further be specified, which is based on expressions that are created using variables that are previously defined in the same CPQ form element.

```
 As an example, we can control the visibility of a section based on the ACL that expresses that the product 3709 or 3712 have NOT been selected.

!(HAS_PROD('3709') || HAS_PROD('3712'))

```


```
Example: the quote_summary section is made visible only for roles 'admin' or 'sales-admin' by writing the Visibility ACL as:

admin | sales-admin

Example: the discount field is made visible only if the total


```

In CPQ Pricing Rules **Condition** 
```
benefits_pricing == 'minimum'
is_network_opportunity == 'yes'
```

In Approval Rules and Approvers
```
term_years == '4' || term_years == '5'

ARRAY_MAX(line_items, 'cpq_user_discount') > 40 && (!HAS_CAT('Advanced Service (NR)')) && (!HAS_CAT('Advanced Service'))

SVP Approval Group (Individual Product >40% Discount))

```



