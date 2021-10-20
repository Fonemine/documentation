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

##2. Formula

```abnf
formula              =  "=" expression
```

To allow the dynamic updating of certain fields based on the data provided by other fields, expressions can be used in some of the input attributes. These expressions will always start with a '=' character and are inspired-by/use a subset of MS Excel formula syntax. Only string and numeric scalar data types are supported together with a limited  set of allowed functions. The input fields of formula can be referenced by their names. A formula can only reference input fields that have been specified previously the current input.

Formulae are allowed in the "value" attribute of inputs of type "readonly" and "hidden". Formulae can also occur in the "hidden" and "disabled" attributes for inputs.

##3. Expressions

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

![Create Price Book in MobileForce CPQ](/images/add_edit_price_book.png)

