# Configure, Price, Quote Admin Guide
An important aspect of the sales process for any business is the systematization of the processes encompassing pricing of products or services that the business sells. In a typical sales process, setting a price for a product not only impacts the profit margins and market share, it also streamlines the process of product discounts and uplifts in response to market conditions. The basic list of products and their prices is a Price Book, often the starting point of all CPQ systems.

## Price Books

Typically, the first thing a CPQ Administrator does is to create one or more price books. 
MobileForce CPQ supports the creation of multiple price books that can also be related to one another via a hierarchical parent relationship. For instance, Businesses could create one price book for local or national use with the local currency, and another price book for each international market they operate in (each with its own currency). Price books allow one to assign different prices for products for different regions with different currencies or for different markets. In order to create a quote, a user **must** select a price book.



![Create Price Book in MobileForce CPQ](/images/add_edit_price_book.png)

Each MobileForce CPQ price book has a (required) **name** field. In addition, price books typically have the following fields:

* **Currency**: specifying the currency used for all prices in the price book. For now, only "USA" is supported as a valid value for the currency field.

The following fields of a MobileForce CPQ price book are found in almost all CPQ entities. For brevity, they are described once here, and not described again in other entities that also have these fields. 

* **Effective Date**: The date starting which  products listed in the price book can be sold
* **Expiration Date**: The date after which products listed in the price book can no longer be sold.
* **Active**: a toggle indicating whether the price book is ready for use in CPQ systems or is still being developed.
* **ACL**: indicating the user roles for the users that are allowed access to the price book. For instance, the US price book may be accessible only by sales user roles who are employed and selling within the USA, and hence not accessible to sales reps who are not members of the sales-USA role, because they sell in the Japan market.

Once a price book is created, the next step is to create product categories,then create products and services within their respective product categories.
Finally we create pricing for the products where we specify the price specific to one or more price books to reflect the different prices for the product in the different markets that these different price books represent.

## Products/Services

A product/service is anything that is sold by the business, irrespective of whether it has a price. Typically products are individual "line items" in *quotes*.

Products may contain nested products, representing bundled products or product features. Such nested products are stored in objects known as product groups. Products may also have attributes, (e.g., color). Rules can be specified on products to ensure valid configuration. To ease the management of products in the product catalog, products are organized in hierarchical categories.

Products can be broken down into two types: simple and configurable. Simple products have no attributes nor nested products. Configurable products may have attributes, nested products, or both. Configurable products  have an associated layout describing their attributes, nested products, and UIs.

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


![Create Product Pricing Section in MobileForce CPQ](/images/add_product_pricing_pricebook.png)



4. Approval Section:

![Create Product Approval Section in MobileForce CPQ](/images/add_product_approval.png)

### Product UI Layouts

## Quotes. 
### Quote UI Layouts
### Quote Templates and Rules

## Approvals
### Approver Groups
### Email Templates

## Contract Documents
### Template Files
### Document Templates

## CPQ Functions and Variables
### Built-in Variables
### Built-in Functions
### OpenTBS Variables in Document Templates
