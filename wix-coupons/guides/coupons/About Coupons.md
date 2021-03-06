# Coupon Types  
Wix supports the following types of coupons:  
* *$ discount* - a.k.a. moneyOff, a fixed discount amount  
* *% discount* - a.k.a. percentOff, a discount as a % (e.g., 20% off)  
* *Free Shipping* - free shipping   
* *Sale Price* - a.k.a. fixedPrice, a fixed sale price      
* *Buy X Get Y* - get a certain number/kind of product for free (Y) when a customer buys a minimum number/kind of items (X). Both X and Y items must be in the customer's cart at time of purchase

## Coupon Scope
Wix site owners can define the coupon to apply to a specific product, a collection of products, or to all of their products within a specific Wix Business Solution. When creating a coupon via API, you will need to apply a coupon scope.

Coupons are available for the following Wix business solutions:
* Wix Stores
* Wix Bookings
* Wix Events

The scope should include:
* Namespace - the relevant Wix Business Solution. **Required**.
* Group - the relevant product/service type. Optional for most coupons - if not listed, the coupon will apply to all products/services/events in the namespace. Required for Wix Events event coupons.
* Entity ID - the unique ID of the product/service the coupon applies to. Required for Wix Event event coupons, otherwise relevant only when Group is listed.

### Wix Stores

| Namespace | Group | Entity ID | Result|
| --- | --- | --- | --- |
| stores|N/A|N/A|Coupon applies to all products |
| stores|product|product ID|Coupon applies to the specific product with the provided ID |
| stores|collection|collection ID|Coupon applies to the specific collection with the provided ID |

### Wix Bookings

| Namespace | Group | Entity ID | Result|
| --- | --- | --- | --- |
| bookings|N/A|N/A|Coupon applies to all services |
| bookings|service|service ID|Coupon applies to the specific service with the provided ID |

### Wix Events

| Namespace | Group | Entity ID | Result|
| --- | --- | --- | --- |
| events|event|event ID|Coupon applies to the specific event with the provided ID |
| events|ticket|N/A|Coupon applies to all tickets |
| events|ticket|ticket ID|Coupon applies to the specific ticket with the provided ID |

## Usage Limits
Coupons can be limited to:
* 1 item per order
* Minimum subtotal
* X number of uses in total (all purchases by all customers, including repeat uses by the same customer)

## Permissions
All the Coupons API endpoints require `COUPONS.MANAGE` permissions.

## Coupon Functionality
* Price discounts for collections apply to every item in that collection, no matter the item's price. If the coupon sets a $10 discount and there is an $8 item in that collection, that item will be free when a customer applies the coupon code.     
* Only 1 coupon can be applied per order. (It is, however, possible to offer free shipping above a set price along with another coupon.)  
* Coupon codes are case and space sensitive. (We recommend instructing customers to copy and paste the coupon code without making any changes.)  
* All discounts require a coupon.  
* Limit to 1 discount per order: If a customer buys multiple items that the coupon applies to, the discount is applied to the item with the lowest price.  
* Limited number of uses: You can set a limit for the number of times the coupon can be used in total, but you can't limit the number of times a specific customer can use the coupon. 
* If you or the Wix site owner created a coupon for a product, and then deletes that product, there is no notification that this product has a coupon attached to it.  
* Buy X Get Y:    
  * Applies only to products in the user’s cart (e.g., to apply a buy 3 get 1 free coupon, the customer must add 4 of the relevant product(s) to their cart.   
  * The defined scope for the coupon applies both to the product purchased and the product received for free (e.g., buy 3 of product X, the 4th is free, or buy 3 products from collection X, get the 4th for free).  
* Coupons can't be limited to a specific type/subset of customers (e.g., first-time or returning customers, customers from specific locales, etc.).  
* Wix Coupons does not send out a specific notification or provide analytics about when a coupon is used.  
* Coupons are not available for quantity based discounts in Wix Stores (e.g., if you buy 10 shirts, you get a 10% discount on the total price). However, you can add a quantity product option with a negative charge.  
* Gift card features are not available at this time.
* There is no bulk upload capability for coupons.   
* There is no coupon code usage tracking available through Wix. It is possible to export the orders to a .CSV file.  
* Coupon currency can't be defined per coupon - $ discount coupons will be applied in any currency that the Wix site owner has set up in their Wix Business Manager settings. 
* Coupons for bookings scopes can't be applied to membership plans, or to services that are set to "Free/Prices Vary".  
  
