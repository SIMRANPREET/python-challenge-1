# Module 2 Challenge

## Food Truck Menu

This is an application to simulate ordering food from a food truck.

### Requirements and Answers

#### Order System 

* An order list is initialized.

``` python
order = []
```

* User is prompted for their menu item selection and it's saved as a variable menu_selection.

``` python
menu_selection = input("Enter the menu item number you want: ")
```

* User input menu_selection is checked as a number and an error is printed if it is not.

``` python
if menu_selection.isdigit():
  # continue
else:
  print("You didn't select a number.")
```

* menu_selection is converted to an integer.

``` python
menu_selection = int(menu_selection)
```

* An if-else statement is used to check if menu_selection is in the menu_items keys, and an error is printed if it isn't.

``` python
if menu_selection in menu_items.keys():
  # continue
else:
  print(f"Item {menu_selection} is not available in the {menu_category_name} menu.")
```

* The item name of the customer's selection is extracted from the menu_items dictionary and stored as a variable.

``` python
item_name = menu_items[menu_selection]["Item name"]
```

* The customer is prompted for a quantity of their item selection and the value defaults to 1 if the customer does not input a valid number. 

``` python
quantity_of_item = input(f"How many of {item_name} do you want: ")
if quantity_of_item.isdigit():
  quantity_of_item = int(quantity_of_item)
else:
  quantity_of_item = 1
```

* The customer's selected item, price, and quantity are appended to the order list in dictionary format.

``` python
order.append({"Item Name":item_name, 
              "Price":menu_items[menu_selection]["Price"],
              "Quantity":quantity_of_item})
```

* A match-case statement is used to check if the customer would like to keep ordering, and performs the correct actions for y, n, and default cases.

``` python
keep_ordering = input("Would you like to keep ordering? (Y)es or (N)o: ").upper()

  match keep_ordering:
    case "YES" | "Y":
      break
    case "NO" | "N":
      print("Thank you for your order!")
      place_order = False
      break
    case _:
      print("Try again")
```

* The match-case statement converts the use input to lowercase or uppercase before checking the case.

``` python
keep_ordering = input("Would you like to keep ordering? (Y)es or (N)o: ").upper()
```

#### Order Receipt

* A for loop is used to loop through the order list.

``` python
for k in range(len(order)):
  # continue
```

* The value of each key in each order dictionary is saved as a variable.

``` python
order_item_name = order[k]['Item Name']
order_item_price = order[k]['Price']
order_item_quantity = order[k]['Quantity']
```

* The number of formatting spaces are correctly calculated.

``` python
num_item_spaces = 26 - len(order_item_name)
num_price_spaces = 8-len(str(order_item_price))-2
```

* Space strings are created using string multiplication.

``` python
item_spaces = " " * num_item_spaces
price_spaces = " " * num_price_spaces
```

* The customer's order is printed with the item name, price, and quantity.

``` python
print(f"{order_item_name}{item_spaces}| ${order_item_price}{price_spaces}| {order_item_quantity}")
```

* List comprehension is used to calculate the total price of the order.

``` python
total_price = sum(list(map(lambda item: item['Price']*item['Quantity'], order)))
```

* The total price of the order is printed to the screen.

``` python
print(f"\nThe total order price is: ${total_price:.2f}")
```
