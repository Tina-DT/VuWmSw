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

The following MindMap was designed to show the possible activites for a customer in the Shop Zalando:
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

The following Activity Diagram was designed to show the possible activites for a customer in the Shop Zalando:
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
<p align="left"><img src="Activity Diagram - Zalando Shopping.png" title="Activity Diagram - Zalando Shopping" width="100%" height="auto"><b>Abbildung 1: Activity Diagram - Zalando Shopping</b></p>


