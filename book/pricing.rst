=======
Pricing
=======

To give users ultimate flexibility in pricing, Nilead uses a concept called **Price Component**


***************
Price component
***************

A price component is basically a data object that holds certain info:

- name
- description
- price calculator
- specific settings
- sort order

Any object (a product, an order, or anything) can have one or many price components.
A price component is associated with a specific price calculator.
The main calculator can loop through the list of price components associated to the object to calculate the final price of the object. This way, it's super simple to handle almost any kind of pricing.

Product Pricing
===============
A product has at least ONE variant and (on theory) can have unlimited number of variants. 

The price(s) is not associated directly with the product but is associated with the variant instead.

While variant price can be pre-set, it can also be adjusted under certain conditions such as:

- discount (per product, per category, etc . . .)
- sales promotion (buy 2 get 1 free, buy A get B free etc)
- group discount
- wholesale pricing

For that reason, a product has a base price and a product can be associated with more than one price component(s) that can adjust the product's price.

For performance purpose, the master variant's base price is recommended to be used as the listing price. The price (by default) is re-calculated on the shopping cart and another time on the order total.

Variant Price Calculation
-------------------------
Variant pricing is calculated in multiple passes (2). The first pass will apply all the price components that do not rely on external info such as order total or the existence of other item(s).. and the second pass will apply the price components that rely on external factor. 

