# MobileForce CPQ APIs

## Introduction

This document describes the APIs for reading and updating MobileForce CPQ objects,
such as Products, Categories, and Price Books.

The MobileForce CPQ API uses the [MobileForce API](mf_api.md) to access the CPQ object.
The MobileForce API allows one to list, read, create, update, and delete tables within
the MobileForce platform.  Please read the [MobileForce API document](mf_api.md)
before continuing with this document.  This document will not describe how to call
these APIs.  It will describe only the supported CPQ tables and their fields.

One may access the following CPQ tables using the MobileForce API.

| CPQ Table | API Table Name |
|---|---|
| Product | MFCPQProduct |
| Product Category | MFCPQProductCategory |
| Price Book | MFCPQPriceBook |
| Price Book Entry | MFCPQPriceBookItem |

## Products (MFCPQProduct)

A product is anything that can be added as a line-item to a quote.

A product has the following fields

* `id` *(text, readonly)*: Unique internal ID of product.
* `name` *(text, required)*: Name of the product.  Must be unique.
* `code` *(text, required)*: Product code or SKU.
* `description` *(text)*: User-friendly description.
* `image` *(text)*: URL of image to display for product in product selection.
* `categories` *(text)*, Comma-separated List of MFCPQProductCategory IDs of categories that this product belongs to.
* `configurable` *(int)*: 1 if the product is configurable, 0 if it is not.  Configurable products can have UI layouts and nested products.
* `selectable` *(int)*: 1 if the product can be selected in the product selection screen, 0 if it can't.  Unselectable products can still be added to quotes via configuration rules.
* `layout` *(text)*: Product UI for product.  Can only be set if `configurable` is 1.
* `qtyReadonly` *(int)*: 1 if the product's quantity is read-only, 0 otherwise.
* `qtyDefault` *(decimal)*: Default quantity for the product.
* `qtyMin` *(decimal)*: Minimum quantity for the product.
* `qtyMax` *(decimal)*: Maximum quantity for the product.
* `qtyStep` *(decimal)*: Step of the quantity.  Any entered quantity must be a multiple of the step.
* `uom` *(text)*: Unit of Measurement.  Short, informational text displayed next to the quantity.
* `qtyListItems` *(text)*: Picklist of selectable quantity values.  Currently unimplemented.
* `qtyParentMul` *(int): 1 if the quantity of this child product should be multiplied with its parent product's quantity, 0 otherwise.  Only used for nested products.
* `priceRecurrence` *(text): For recurring prices, this specifies the pricing interval.  Can be one of the following values:
  * `oneTime`
  * `perMinute`
  * `hourly`
  * `daily`
  * `weekly`
  * `biweekly`
  * `semimonthly`
  * `monthly`
  * `quarterly`
  * `halfyearly`
  * `yearly`
* `disEnabled` *(int)* 1 if one can discount the price for this product, 0 otherwise.
* `disUnit` *(text) Kind of discount that can be entered.  Can be `amount`, `percent`, or `both`.
* `disPctMin` *(decimal)* If entering a percentage discount, this is the minimum discount allowed.
* `disPctMax` *(decimal)* If entering a percentage discount, this is the maximum discount allowed.
* `disAmtMin` *(decimal)* If entering a fixed discount amount, this is the minimum discount allowed.
* `disAmtMax` *(decimal)* If entering a fixed discount amount, this is the maximum discount allowed.
* `externalId` *(text)*: ID of product in external an external CRM such as SugarCRM, Hubspot, or Zendesk.  Used for product synchronization.
* `active` *(int)*: 1 if the product is active, 0 if inactive.  Inactive products cannot be added to quotes.
* `acl` *(text)*: Access control list used to restrict which MobileForce users can add this product to quotes.
* `effectiveDate` *(date)*: Date in which this product becomes effective.  The product cannot be added to quotes before this date.  If blank the product has no starting effective date.
* `expirationDate` *(date)*: Date in which this product is no longer effective.  The product cannot be added to quotes after this date. If blank the product has no ending effective date.
* `createdTime` *(date/time, readonly)*: Date and time that the product was created.
* `createdById` *(text, readonly)*: User ID of MobileForce User that created the product.
* `createdByEmail` *(text, readonly)*: Email address of MobileForce User that created the product.
* `modifiedTime` *(date/time, readonly)*: Date and time that the product was last modified.
* `modifiedById` *(text, readonly)*: User ID of MobileForce User that last modified the product.
* `modifiedByEmail` *(text, readonly)*: Email address of MobileForce User that last modified the product.

## Product Categories (MFCPQProductCategory)

A product category is a named grouping of products.  The main purpose of categories are to
restrict and organize products in product selection.  However, they can also be used in
configuration and pricing rules.

Products can belong to multiple categories and categories can have multiple products.

Categories can be organized in a tree.  If a product belongs to a category, then that
product is accesible in that category as well as all parent categories.

A product category has the following fields

* `id` *(text, readonly)*: Unique internal ID of the category.
* `name` *(text, required)*: Name of the category.  Must be unique within its parent category.
* `parentId` *(MCPQProductCategory ID)*: ID of the parent product category.
* `description` *(text)*: User-friendly description.
* `image` *(text)*: URL of image to display for the category in product selection.
* `externalID` *(text)*: ID of a category in an external CRM, such as SugarCRM, Hubspot, or Zendesk.  Used in category synchronization with external CRMs.
* `active` *(int)*: 1 if the product is active, 0 if inactive.  Inactive category cannot be seen during product selection.
* `acl` *(text)*: Access control list used to restrict which MobileForce users can see this category during product selection.
* `effectiveDate` *(date)*: Date in which this category becomes effective.  Before this date, the category cannot be seen during product configuration.  If blank the category has no starting effective date.
* `expirationDate` *(date)*: Date in which this category is no longer effective.  After this date, the category cannot be seen during product configuration.  If blank the category has no ending effective date.
* `createdTime` *(date/time, readonly)*: Date and time that the category was created.
* `createdById` *(text, readonly)*: User ID of MobileForce User that created the category.
* `createdByEmail` *(text, readonly)*: Email address of MobileForce User that created the category.
* `modifiedTime` *(date/time, readonly)*: Date and time that the category was last modified.
* `modifiedById` *(text, readonly)*: User ID of MobileForce User that last modified the category.
* `modifiedByEmail` *(text, readonly)*: Email address of MobileForce User that last modified the category.

## Price Books (MFCPQPriceBook)

All product prices are stored within price books.  Price books represent a collection of
prices, all with the same currency type.  Every quote will have an associated price book.

Price books can be organized in a tree.  If a product does not have a price in a price book,
its price is looked up in the parent price book.

* `id` *(text, readonly)*: Unique internal ID of the price book.
* `name` *(text, required)*: Name of the price book.  Must be unique.
* `parentId` *(MFCPQPriceBook ID)*: ID of the parent price book.
* `description` *(text)*: User-friendly description.
* `currency` *(text, required)*: Three-letter currency code for prices in this price book.
* `active` *(int)*: 1 if the price book is active, 0 if inactive.  Prices in inactive price books cannot be used.
* `acl` *(text)*: Access control list used to restrict which MobileForce users can use prices in this price book.
* `effectiveDate` *(date)*: Date in which this price book becomes effective.  Before this date, prices in this price book will not be used.  If blank the price book has no starting effective date.
* `expirationDate` *(date)*: Date in which this price book is no longer effective.  After this date, prices in this price book will not be used.  If blank the price book has no ending effective date.
* `createdTime` *(date/time, readonly)*: Date and time that the price book was created.
* `createdById` *(text, readonly)*: User ID of MobileForce User that created the price book.
* `createdByEmail` *(text, readonly)*: Email address of MobileForce User that created the price book.
* `modifiedTime` *(date/time, readonly)*: Date and time that the price book was last modified.
* `modifiedById` *(text, readonly)*: User ID of MobileForce User that last modified the price book.
* `modifiedByEmail` *(text, readonly)*: Email address of MobileForce User that last modified the price book.

## Price Book Entries (MFCPQPriceBookItem)

Price book entries are prices associated with a product and a price book.  It is possible
for a product to have multiple price book entries for a product and price book.

* `id` *(text, readonly)*: Unique internal ID of the price.
* `name` *(text)*: Name of the price.  Unused.
* `priceBookId` *(MFCPQPriceBook ID, required)*: ID of the price book this price belongs to.
* `productId` *(MFCPQProduct ID, required)*: ID of the product this price is for.
* `tag` *(text)*: Programming tag for the price.  The price will not be used unless there is a pricing rule that enables prices with this tag.  Used for dynamically overriding prices.
* `description` *(text)*: User-friendly description.
* `currency` *(text)*: Three-letter currency code for prices in this price book.
* `method` *(text, required)*: Method to determine the total price from its quantity.  Can be one of the following values:
  * `flatfee`: Quantity is ignored.
  * `perUnit`: Total is unit price time quantity.
  * `volume`: Total is the quantity times a value looked up in a table.
  * `tiered`: Total is a sum of pricing tiers, where each tier is the quantity times a value looked up in a table
  * `block`: Total is fixed price looked up from a table keyed off the quantity.
* `listPrice` *(decimal)*: The unit price.  Only used by the `perUnit` pricing method.
* `flatFee` *(decimal)*: A fixed price to be added to the total price, no matter what pricing method is used.
* `minPrice` *(decimal)*: Minimum allowed total price.  If the total price is less than the minimum price, the minimum price is used.
* `cost` *(decimal)*: Cost of the product.  Currently, only informational.
* `priceTiers` *(text)*: A JSON array of objects describing the price tiers/blocks to use for pricing.  Only used for the `volume`, `tiered`, and `block` pricing methods.
* `active` *(int)*: 1 if the price is active, 0 if inactive.  Inactive Prices cannot be used.
* `acl` *(text)*: Not used.
* `effectiveDate` *(date)*: Date in which this price becomes effective.  Before this date, the price will not be used.  If blank the price has no starting effective date.
* `expirationDate` *(date)*: Date in which this price book is no longer effective.  After this date, the price will not be used.  If blank the price has no ending effective date.
* `createdTime` *(date/time, readonly)*: Date and time that the price was created.
* `createdById` *(text, readonly)*: User ID of MobileForce User that created the price.
* `createdByEmail` *(text, readonly)*: Email address of MobileForce User that created the price.
* `modifiedTime` *(date/time, readonly)*: Date and time that the price was last modified.
* `modifiedById` *(text, readonly)*: User ID of MobileForce User that last modified the price.
* `modifiedByEmail` *(text, readonly)*: Email address of MobileForce User that last modified the price.

### Price tiers

For the `volume`, `tiered`, and `block` pricing methods, the pricing tiers or blocks are
specified in the `priceTiers` field.  This field is a JSON array of objects, where each
object has the following fields:

* `from`: Starting quantity that this price tier or block applies to
* `listPrice`: Unit price to use for this price Tier.

An example `priceTiers` value is:

```json
[
    { "from": 1, "listPrice": 10 },
    { "from": 51, "listPrice": 8 },
    { "from": 101, "listPrice": 6 }
]
```

Suppose the quantity is 70.  Then a `volume` pricing method using the above example
would be `70 * $8 = $560`, a `tiered` pricing method would be `50 * $10 + 20 * $8 = $660`,
and a `block` pricing method would be just `$8`.
