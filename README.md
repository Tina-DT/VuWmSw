# VuWmSw


### Verfahren und Werkzeuge Moderner Softwareentwicklung
### Mentor: Prof. Dr. Stefan Edlich
### Einsendeaufgabe 1: UML Modellierung
<br /> <br />
| Name               | Matrikelnummer | Hochschule  |
| :----------------- | :------------- | :---------  |
| Tina Heilig        | 70268368       | FH Ostfalia |

<br /> <br />
#### ESA1: MindMap und Klassendiagramm in UML
<br /> <br />

The following UML diagrams are designed as a specification and visualization of an online shopping platform as an example.
The following MindMap was designed to show the possible activities for a customer in the online shop Zalando (or any other online shop, because the products and instances are not exactly specified). The MindMap was created with https://www.planttext.com/:

```
@startmindmap

* Zalando \nShopping \nproperly
 * Creating an account 
  * Enter your email address
  * click next
  * complete all needed fields
  * checking the confirmation email
  * confirm your registration
  * log in
  
 * Shopping with account
  * log in
  * browse offers
  * search for your product
  * add product into the shopping cart
    **** change the number of the products
    **** choose a payment type
    **** close the purchase
  * check old orders
   **** prepare return
   **** prepare a complaint
   **** further communication with Zalando Service
  * log out

 * Bying as a guest
  * browse offers
  * search for your product
  * add product into the shopping cart
   **** change the number of the product
   **** close the purchase
  
 * Just collecting ideas
  * browse offers
  * make screenshots
  * compare offers with other websites

@endmindmap
```
<p align="left"><img src="Mindmap Zalando Shopping.PNG" title="MindMap - Zalando Shopping" width="100%" height="auto"><b>Abbildung 1: MindMap - Zalando Shopping</b></p>

The following Activity Diagram was designed to show the possible activites for a customer in the Shop Zalando (or any other online shop, because the products and instances are not exactly specified).  The Activity Diagram was created with https://www.planttext.com/:
```
@startuml

title Activity Diagram - Creating an account and Shopping in Zalando

start

:enter your email address; 
note right: Existing accounts with the email will be checked

:click next; 


if (Account exists?) then (yes)
 if (Need a new password?) then (yes)
  :__change password__;
  else (no)
  endif
else (no)
  :complete all needed fields;
  
if (All fields are filled?) then (yes)
  :__confirm your registration__;
else (no)
  :fill out missing fields;
endif
endif

:log in;
note left: This is a note to the left

:choose an item;
if (Is this the correct item?) then (yes)
  :__add item to cart__;
else (no)
  :go on with searching;
endif

:display cart;
:click purchase order;
:get order status;
:receive order;

if (Does the item fits?) then (yes)
  :__keep it__!!!;
else (no)
  :sent it back to shop;
endif

stop

@enduml
```
<p align="left"><img src="Activity Diagram - Zalando Shopping.png" title="Activity Diagram - Zalando Shopping" width="100%" height="auto"><b>Abbildung 2: Activity Diagram - Zalando Shopping</b></p>


The following Class Diagram was designed to show the possible relationships in the Shop Zalando(or any other online shop, because the products and instances are not exactly specified). The Class Diagram was created with https://www.planttext.com/:
```
@startuml

title Zalando Shopping - Relationships Class Diagram

class Customer {
-custId: Integer
-custShoppingCart: Integer
+createShoppingCart(Product: Product{1..*]): boolean
+emptyShoppingCart(): void
+purchase()
 
}

class AccountCustomer {
-custId: Integer
-custName: String
-custEmail: String
-custPassword: String
-custAddress: String
-custPayment: Integer
-custOrder: Integer
+createShoppingCart(Product: Product{1..*]): boolean
+emptyShoppingCart(): void
+purchase(): Order
+changePassword(password: String): boolean
+changeEmail(email: String): boolean
+changeAddress(address: String): boolean 
}

class GuestCustomer{
-custId: Integer
-custShoppingCart
+createShoppingCart(Product: Product{1..*]): boolean
+emptyShoppingCart(): void
+purchase(): void
}

class Address{
-streetId: Integer
-streetName: String
-streetNumber: String
-city: String
-phoneNumber: Integer
}

class Category {
  -catId: Long
  -name: String
  -description: String
  -prodId: Integer
  +addProduct (Product) void
  +remove(Product): void
  +findProduct(Product): Product
}

class Product {
-prodId: Integer
-name: String
-prodPrice: Integer
-prodType: String
-prodSubtype: String
+statusSupplier(Supplier)
+filterProduct()
+searchProduct()
}

class ShoppingCart{
-cartId: Integer
-quantityOfProducts: Integer
-prodPrice: Integer
-totalPrice: Integer
-prodId: Integer
-createdCart: Date
  +updateContentShoppingCart(Product: Product{1..*]): boolean
  +findProduct(Product): Product
  +SumPrice(Product): void
  +purchase(): Order
}

class Order {
-orderId: Integer
-custId: Integer
-dateOfOrder: Date
-prodPrice: Integer
-totalPrice: Integer
+placeOrder(): Order
+listProduct: List

}


class Payment {
-custId: Integer
-custName: String
-paidDate: Date
-cardType: Integer
-cardNumber: Integer
-totalPrice: Integer
}

class Delivery {
-deliveryId: Integer
-orderId: Integer
-custAddress: Integer
-location: String
-prodList: List <Product>
}

class Supplier {
-supName: String
-supLocation: String
-prodCapability: Integer
-prodList: List <Product>
}

class Date {
-day: Integer
-month: Integer
-year: Integer
+constDate(day, month, year)
+void display()
}

AccountCustomer -up--|> Customer: Inheritance
GuestCustomer --|> Customer: Inheritance
Address "1" -down- "1" AccountCustomer: Owns
Category <|--down- Product: BelongsTo
Product "1..*" -down- "1..*" Supplier: Manage
Product "0..*" -down- "0..*" GuestCustomer: View
AccountCustomer "1" o--down- "1" ShoppingCart: MaintainContent
AccountCustomer "1" *--down- "1..*" Order: Makes
Order "1..*" -down-o "1..*" Product: Contains
Order "1" -down- "1..*" Payment: BelongsTo
Order "1" --down- "1..*" Delivery: RefersTo
Payment "1" *--down- "1..*" Delivery: RefersTo
Order "1" -down- "1" Date: Contains
ShoppingCart "1" - "1" Date: Uses
Product "1..*" --down- "0..1" ShoppingCart: Contains
AccountCustomer "1" *--down- "1..*" Payment: Uses
GuestCustomer "0..*" <- "0..1" ShoppingCart: Uses
GuestCustomer "1...*" - "0..*" Payment: Uses

@enduml
```
<p align="left"><img src="Class Diagram - Zalando Shopping.png" title="Class Diagram - Zalando Shopping" width="100%" height="auto"><b>Abbildung 3: Class Diagram - Zalando Shopping</b></p>

The version 2 of the Class Diagram was created with https://app.diagrams.net/:
<p align="left"><img src="Class Diagram 2 - Zalando Shopping.png" title="Class Diagram 2 - Zalando Shopping" width="100%" height="auto"><b>Abbildung 4: Class Diagram 2 - Online Shopping</b></p>
