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




``keypad_screen()``
Transitions current screen to checkout keypad screen


``def row_pressed(self, instance_table, instance_row):``
Desc:
Function obtains information from a row of data from inventory search results
Parameters:
instancetable-Content from MDDatatable
instancerow-Content from Row pressed

CheckoutCartScreen 
----------------
This screen displays all items that have been added to the current customer order as well as the current total price  for the order. When the Done button is pressed the order is complete


``casheir_cart()``
Adds items selected in checkout table screen to cart or from camera screen
Also creates string that contains receipt

``update_customer_orders_db()``
Updates the customer_orders db with customer order and creates popup prompt for receipt sent to text message

``close_rec()``
Closes the receipt popup

``go_receipt()``
Function sets current screen to sendreceipt screen

``go_menu()``
Sets current screen to menu screen

``clear_list()``
Resets the checkout cart by  removing its items and clearing the text in searchbar in checkoutkeypad screen

``display_price()``
Formats price label  in checkout cart screen to 2 decimal places

SendReceiptScreen 
----------------
This screen sends a text message with the customer receipt to the phone number entered. The screen contains a keypad for entry of a phone number.

``add_keypad()``
Adds keypad to sendreceipt screen

``send_text()``
Calls twilio api and send text message of receipt to valid phone number entered in screen


CameraScreen
----------------
This screen has camera permissions and classifies an image taken to items that were trained on the model.

``capture()``
Captures a picture and stores result in Fruit.png

``def preprocess(self, filepath):``
Desc:
Formats picture format in preparation for image classification
Parameters:
filepath:location of image in directory

``model_predictions(self, Img)``
Desc:
Function invokes tflite interpreter to classify  image and display corresponding label. 
Also displays popup confirming item is correctly identified
Parameters:
Img = Image object of Fruit.png



``go_amount()``
Sets current screen to checkout_keypad which is to select quantity of item








------------
.. autosummary::
   :toctree: generated

