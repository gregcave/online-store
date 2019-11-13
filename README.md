# online-store
An online shopping site for a hypothetical company which sells books, games and DVDs

## Design of the Site

###  Outline

There is a home page for the shop with menus across the top and down the left hand side. There is four departments - books, CDs, games and DVDs. Each has a page of products for sale. Menus at top and side are consistent across all the pages of the site.

Behind the site is a MySQL database which is included in this repository. On the product pages, the title, text extracts, illustration image, price and stock count for each product are displayed. (i.e. how many are available to buy at that moment). The database contains information of this kind which you can use. 

There are two kinds of users of the site, firstly Customers, and secondly the Manager.

###  Customers

A customer of the site can do the following:

* View pages of books, music CDs, games and DVDs without logging on. Customers are able to see the price and stock count of each item, but they are not be able to buy without logging on.

* Log on as a customer and then buy an item by clicking a button which says ‘Buy’ which is next to each such item. Note there is no shopping cart and minimal process involved. Clicking the button goes to a purchase page where a button can be clicked to complete the purchase.

  Buying an item creates one new entry in the customer_order table and one new entry in the order_item table. (It is assumed a customer orders one item at a time and there is one customer_order and one order_item for that item.)

* Log out.

###  The Manager

The manager of the shop can do the following:

* Log on as manager and then view all the database tables on the system.

* Log out. 

In this website, the manager can only view the tables and cannot modify them or perform any other tasks.

## Structure and Merchandise

* The site has a home page, a user login page, a manager login page and
 one page each for Books, CDs, Games and DVDs.
* There are at least six items for sale in each category, i.e. Books,
 Music, Games and DVDs, each shown with a unique item code, a short
 description, an image, a price and a number in stock.
* Each item for sale has a different picture which relates specifically
 to the item.
* The database tables are used dynamically to create the pages of items
 for sale on the website. In other words, the items are not hard coded
 in an HTML page; instead, the HTML page is created dynamically from
 a .php page by consulting the database whenever that .php is loaded.
 
## Customer Logon and Purchase

* The user can log in to the site and log off again using their
 customer_number and passwd from the customer table in the database.
 Specifically, user 1001 can log in with password 'mollie' and this is
 checked by searching the database.
* There is Javascript validation of login information. It should check
 that username is a number and that the password submitted is not
 null.
* The user can 'purchase' an item which is for sale, but only when
 logged in. No 'shopping cart' or payment needed, just click on a
 button called 'Buy' which is next to an item. We will then go to a
 purchase page. The user can then click 'Complete Purchase' whereupon
 the item is purchased immediately as long as the user is logged
 in. Otherwise, it can say 'not logged in' or similar. The value
 field of the order_item is the same as the item_price for the item
 in the inventory, unless there is a discount (see below).
* On the purchase page there is a box to enter a promotional code. If
 the user enters a code in the box, it is looked up in the
 promotion_code table and the appropriate discount applied
 when 'Complete Purchase' is clicked. A discount of 10 means the cost
 is reduced by 10%. Invalid codes do not result in
 a discount! This feature will be verified by looking at the value
 field for the order_item created when the item is purchased.
* Stock goes down when an item is purchased. This will be verified by a
 customer making a purchase and observing if the stock count goes
 down.
* An item which is out of stock may not be purchased. This will be
 verified by a customer clicking Buy against an item which shows a
 stock count of zero. The system should give an error message and not
 purchase the item for the customer.
 
## Customer Review and Search

* Next to an item for sale is a Review button. If a logged-on user
 clicks that button they can enter a simple 1-5 integer
 rating using radio buttons. The review rating is recorded in
 the 'review' database table, which can be viewed from the manager
 page.
* There is a search box at the top of the screen. If a string is
 entered, this will display all items in the database (of whatever
 type) which contain the entered string in their item description
 field. For example, if you enter "playing", the album Netsky will be
 displayed.
 
### Manager Logon and Review

* The manager can log on to the site. Specifically, manager_number 100
 can log in with passwd 'luigia', and this is checked in the database.
* The manager can view the contents of all the database tables but only
 when logged in.
* For a new order, a delivery date three days in the future is recorded
 in the database. This will be checked by ordering an item and then
 from the manager page looking for one new entry in the customer_order
 table and one new entry in the order_item table. (We assume a
 customer always orders one item only and there is one customer_order
 and one order_item for that item.)

