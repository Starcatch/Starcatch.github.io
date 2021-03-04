---
layout: post
title:      "Building "one to many" association in JavaScript."
date:       2020-09-15 17:47:35 -0400
permalink:  building_one_to_many_association_in_javascript
---


A few months ago I called a good friend of mine to catch up, due to coronavirus pandemic this is the longest time we didn’t see each other. My friend is a great  restaurant and catering manager, and had a been very successful in the food industry prior to the Covid-19 situation. My friend took a temporary job as an emergency manager for a dying Bakery to make it prosper again. After talking to him for a few minutes he told me that his biggest challenge working there was  to organize an order system to  keep track of orders and deliveries. Thus, I have came up with the simple application, in which an employee takes an order by filling out a form with customer’s information. When the employee hits the Submit Order button, the OrdersAdapter class makes a POST request to Rails API and displays the order on our Index page, then the employee can add items to the order by entering an **Item** and a **Price** in the item's form fields. An employee is able to add multiple items to the same order. 

To build the **Rails Api**  didn’t take so my mush effort, after all we had been studying Ruby and Ruby on Rails for the past three models , it was much more challenging to build out “one to many” relationship, Order has Many Items, in JavaScript. After fixing a few issues on the backend and finally getting **JSON** data on the DOM, displaying data in Index page was definitely a learning curve, but that was an easy part. My struggle was to display items associated with particular orders. After taking a little break and looking at my Ruby code , I  realized that I just like in Ruby I can build this association using an **orderId**.  And create an innerHTML form for Item’s attributes. 

```
static renderNewOrderItemForm(orderId) {
      const formContainer = document.getElementById(`order-${orderId}`)
      const form = document.createElement("form")
      form.setAttribute('data-order-id', orderId)

      form.innerHTML = `
          Item: <input type="text" name="order-item-item_name" id="order-item-item_name"/><br>
          Item Price:<input type="text" name="order-item_price" id="order-item_price"/><br>            
          <button type="submit-item" id="submit-item-button">Submit Item</button>
      `

      
      formContainer.appendChild(form)
  }
```
After I got my app functionality working. I finally, had a moment to realize that  that my UI is very ugly, and I have to quickly do something with it, fast! 

```


body {
  font-family: 'Raleway', sans-serif;
  background: #eef0f1;
  color: rgb(36, 34, 34);
  line-height: 1.8;
}



.new-order-form {
width: 960 ;
margin: auto ;
}




label {
  display: inline-block;
  width: 100px;
  height: 20px;
  text-align: left;
  margin: auto;
}


#order-container {
  margin: 30px auto;
  max-width: 400px;
  padding: 20px;
}

#new-order-container {
  margin: 30px auto;
        max-width: 400px;
        padding: 20px;
}

#new-order-form label {
    display: block;
    color: #666;
  }

  #new-order-form input {
    width: 100%;
    padding: 10px;
    border: #ddd 1px solid;
    border-radius: 5px;
  }
  #new-order-form button {
    background: #f3b369;
    color: #fff;
    border: none;
    font-size: 16px;
    padding: 10px 20px;
    border-radius: 5px;
    cursor: pointer;
  }

  #new-order-form button:hover {
    background: #0c76a7
  }


#name-button{
  background: #4c6ca0;
  color: #fff;
  border: none;
  font-size: 16px;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}

#orders-content {
  margin: 30px auto;
  max-width: 400px;
  padding: 20px;
}

.delete-bttn {
  background: #ec5555;
  color: rgb(252, 247, 247);
  border: none;
  font-size: 16px;
  padding: 5px 10px;
  border-radius: 7px;
  cursor: pointer;

}

.new-item-button {
  background: #5dd677;
  color: #fff;
  border: none;
  font-size: 16px;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
}

#submit-item-button {
  background: #eec336;
  color: #fff;
  border: none;
  font-size: 16px;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
}

```
Prior to this project I used Bootstrap to style my previous projects. I got pretty nice results with it but this time, adding Bootstrap after the to already working app would require change a lot of things not only in** index.html** file but in my **order.js** and** orders.js** files. So I decided  not to change anything and use this opportunity to learn pure CSS. I wanted my app to be simple, easy to use, easy to look at and be user friendly, I moved the Order form and the text to the middle, added modern fonts , and  style to buttons, by doing these simple adjustments I learned the difference between selectors for classes, ids, and other elements and tags. 
Going forward I would like to revisit this app and add more CSS styles, as well as building more functionality, like delete and edit items and orders. 
