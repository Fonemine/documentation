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


## 1. MobileForce Expression Language (MFEL).

Often, expressions in MobileForce are used in form expressions, CPQ rules, triggers, macros, email templates, etc. All of these uses  build upon **MFEL** in unique ways.

## 2. Formula

```abnf
formula              =  "=" expression
```

To allow the dynamic updating of certain fields based on the data provided by other fields, expressions can be used in some of the input attributes. These expressions will always start with a '=' character and are inspired-by/use a subset of MS Excel formula syntax. Only string and numeric scalar data types are supported together with a limited  set of allowed functions. The input fields of formula can be referenced by their names. A formula can only reference input fields that have been specified previously the current input.

Formulae are allowed in the "value" attribute of inputs of type "readonly" and "hidden". Formulae can also occur in the "hidden" and "disabled" attributes for inputs.

## 3. Expressions

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

The only supported primitive values are strings, numbers, and JSON key/value objects.  Numbers will be represented internally as double precision numbers.  Strings will be automatically converted to numbers when necessary and vice versa.  There is no boolean type.  A value is considered to be false if it is the empty string, zero or the string "0".  Otherwise, it is considered to be true.

A JSON key/value object is a string that follows the [JSON object format](https://www.json.org/).  The JSON object must have a "key" and a "value" field.  An example JSON key/value object is `{"key": 1, "value": "One"}`.  The "key" field contains the actual or stored value while the "value" field contains the user-displayable string.  JSON key/value objects are often used for picklist inputs.  For example, a "user" picklist input may have its database ID stored in the "key" field and the user's name in the "value" field.

A JSON key/value value in any arithmetic or conditional expression will be automatically converted to its key.  For example '{"key": 1, "value": "One"}' + 3 will be evluated to 4.


![Create Price Book in MobileForce CPQ](/images/add_edit_price_book.png)

