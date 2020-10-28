# Configure, Price, Quote Admin Guide
An important aspect of the sales process for any business is the systematization of the processes encompassing pricing of products or services that the business sells. In a typical sales process, setting a price for a product not only impacts the profit margins and market share, it also streamlines the process of product discounts and uplifts in response to market conditions. The basic list of products and their prices is a Price Book, the starting point of all CPQ systems.

## Price Books

MobileForce CPQ supports the creation of multiple price books that can be related to one another via a hierarchical parent-child relationship. Businesses could create one price book for local or national use and another price book for each international market they operate in (each with its own currency). 

Each MobileForce CPQ price book has a (required) **name** field. In addition, price books typically have the following fields:

* Currency: specifying the currency used for all prices in the price book
* Effective Date: The date starting which  products listed in the price book can be sold
* Expiration Date: The date after which products listed in the price book can no longer be sold.
* Active: a toggle indicating whether the price book is ready for use in CPQ systems or is still being developed.
* ACL: indicating the user roles for the users that are allowed access to the price book. For instance, the US price book may be accessible only by sales user roles who are employed and selling within the USA, and hence not accessible to sales reps who sell in the Japan market.


![Create Price Book in MobileForce CPQ](/images/add_edit_price_book.png)

## Products/Services
### Product Categories
### Products, Configurations and Rules
### Product UI Layouts

## Quotes
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
