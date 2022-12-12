================
Screens
================


CheckoutScreen
----------------
This screen is used to search items in the inventory to add to a customer order. It contains a keyboard for user entry and has buttons that lead to Camera, Menu, and CheckoutCart screens

``add_keyboard(self):`` 
Description:
Adds keyboard onto checkout screen


CheckoutKeypadScreen 
----------------
This screen is used to enter the quantity for an item after an item has been selected. The screen contains a keypad and text field for user entry.


``addkeypad()``
Adds keypad onto CheckoutKeypad screen

``check_user_error()``
Checks if a valid amount has been entered in keypad



CheckoutTableScreen
----------------
This screen retrieves information from database to display search results from inventory based on input


`loadTable()`
Queries the inventory database to display results based on item name entered in checkout screen




`keypad_screen()`
Transitions current screen to checkout keypad screen


`def row_pressed(self, instance_table, instance_row):`
Desc:
Function obtains information from a row of data from inventory search results
Parameters:
instancetable-Content from MDDatatable
instancerow-Content from Row pressed


------------
.. autosummary::
   :toctree: generated

