================
Screens
================


CheckoutScreen
----------------
This screen is used to search items in the inventory to add to a customer order. It contains a keyboard for user entry and has buttons that lead to Camera, Menu, and CheckoutCart screens
Functions:
	``add_keyboard(self):`` 
	Description:
	Adds keyboard onto checkout screen


CheckoutKeypadScreen 
----------------
This screen is used to enter the quantity for an item after an item has been selected. The screen contains a keypad and text field for user entry.

Functions:
	``addkeypad()``
	Adds keypad onto CheckoutKeypad screen

	``check_user_error()``
	Checks if a valid amount has been entered in keypad



CheckoutTableScreen
----------------
This screen retrieves information from database to display search results from inventory based on input

Functions:
	``loadTable()``
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

Functions:
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

Functions:
	``add_keypad()``
	Adds keypad to sendreceipt screen

	``send_text()``
	Calls twilio api and send text message of receipt to valid phone number entered in screen


CameraScreen
----------------
This screen has camera permissions and classifies an image taken to items that were trained on the model.

Functions:
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

InventoryScreen 
----------------
This screen displays all items in the inventory_db with option to add item, remove item, update price and quantity of item
Functions:
	``addInvTable()``Adds MDDatatable with items from inventory_db

	``row_press()``
	Desc:
	Stores information of item in list row_info
	Parameters:
	Instance_table: MDDatable table object
	Instance_row: Row object from MDDatatable

	Returns: row_info , list with selected  item information


UpdateInvItemScreen
----------------
This screen allows user to modify quantity of selected item from inventory screen

Functions:
	``add_keypad()``
	Adds keypad to screen
	
	``def modify_quantity(self)``
	Modifies quantity in inventory_db of selected item


	``store_new_item()``
	Selects item to be modified and stores info in list

	``close_error_popup()``
	Closes MDDialog window for errors

	``close_update_price_popup()``
	Closes MDDialog window to update price


	``updatePriceQuery()``
	Opens MDDialog asking whether to update price of item 


	``callUpdateInvPriceScreen()``
	Closes MDDialog and changes screen to updateinvpricescreen


	``check_user_error()``
	 Checks if valid quantity has been entered


UpdateInvPriceScreen
----------------
This screen updates the price of an item selected from  inventory screen

Functions:
	``add_keypad()``
	Adds keypad to screen


	``store_new_price()``
	Stores selected item’s information in new_item list and calls modify price function to change price and changes screen to inventory screen



	``close_error_popup()``
	 Closes MDDialog window for errors


	``check_user_error()``
	Opens MDDialog if invalid price entered


AddItemNameScreen
----------------
This screen collects new item name  from keyboard to be inserted into database

Functions:
	``add_keyboard()``
	Adds keyboard to screen


	``store_new_item()``
	Stores item in new_item list and changes screen to additemprice screen


	``check_user_error()``
	Checks if item name entered is valid or already exists in the database


RemoveItemScreen
----------------
This screen removes item from inventory database

Functions:
	``add_keyboard()``'
	Adds keyboard to screen


	``def remove_item(self, text):``
	Desc:
	Removes item from inventory database by name
	Parameters:
	text: String entered from keyboard


	``def check_user_error(self, text):``
	Desc:
	Check if name entered is valid an can be removed from database
	Parameters
	text: String entered from keyboard

	
AddItemPriceScreen 
----------------
Screen collects new item price from keypad

Functions:
	``def add_keypad(self):``
	Adds keypad onto screen


	``def store_new_item(self, text):``
	Desc:
	Price is stored into new_item list and screen changed to additemquantity screen
	Parameter:
	text: string containing item price


	``def check_user_error(self, text):``
	Desc:
	Checks if valid price entered
	Parameters:
	text : String containing price of item


AddItemQuantityScreen 
----------------
Screen collects new item quantity from keypad

Functions:
	``def add_keypad(self):``
	Adds keypad onto screen


	``def store_new_item(self, text):``
	Desc:
	Adds quantity from user input into list and inserts all value from list into database
	Parameter
	Text: string from user input containing quantity of item


	``def check_user_error(self, text):``
	Desc
	Checks if user input is valid
	Parameter
	Text: String from user input


ReturnScreen 
----------------
Screen allows user to return item based on receipt number

Functions:
	``def add_keypad(self):``
	Adds keypad onto screen

	``def inputvalidation(self):``
	Checks if valid receipt number entered 


ReturnCartScreen 
----------------
Screen displays items from customer order


Fucntions:
	``def temp_connection(self):``
	Calls customersorders database to display all items in customer order


	``def display_info(self, cur, rec_num):``
	Desc:
	Adds price  and receipt labels to screen
	Parameters:
	Cur: Postgres database connection object
	Rec_num: receipt number for customer order


	``def go_menu(self, obj):``
	Change Current screen to menu screen


	``def remove_item(self, instance_table, instance_row):``
	Selects item from mddatable and stores selected information in list


	``def refund_amount(self):``
	Changes screen to return_amount screen


ReturnAmountScreen
----------------
Screen collects refund quantity for item

Functions:
	``def add_keypad(self):``
	Adds keypad to screen


	``def update_db(self):``
	Updates customer order database with new item quantity


	``def inputvalidation(self):``
	Checks if refund quantity is valid


StatisticsScreen
----------------
Screen displays graphs of customer orders


Functions:
	``def last_thirty(self):``
	Displays graph with total purchase amount from all orders from last 30 days


	``def top_sellers(self):``
	Displays graph with highest selling items


	``def by_week(self):``
	Displays graph with purchase amount for last week

	``def by_year(self):``
	Displays graph with average purchase price by year


	``def by_month(self):``
	Displays graph with  average order amount by month




CustomizationScreen 
----------------
Screen contains buttons to change background and button coolors

No Functions


BackgroundColorScreen 
----------------
Screen which changes background color of app by using color wheel

Functions:
	``def on_color(self, instance, value):``
	Changes color of background screen


	``def on_press(self):``
	Adds color values to new file in app phone directory


ButtonColorScreen
----------------
Screen which changes button color for all buttons


Functions:
	``def on_color(self, instance, value):``
	Changes color of button


	``def on_press(self):``
	Adds color values to new file in app phone directory



------------
.. autosummary::
   :toctree: generated

