**Shopify Order Fulfillment to Google Sheets Script**

This app script allows you to automatically update a Google Sheet with Shopify order details whenever an order is placed. The script is triggered by a Shopify webhook that is set up for order fulfillment. It fetches the order details and appends them to a Google Sheet, including some hardcoded values.

**Features**

* Automatically fetch Shopify order details upon order fulfillment.
* Extracts and displays customer information, order details, and shipping details in a Google Sheet.
* Adds hardcoded values such as ship-from address and delivery windows.
* Checks for duplicate order numbers to prevent duplication in the Google Sheet.
  
**How It Works**

* **Webhook Trigger:** A webhook for order fulfillment is created in Shopify. When an order is fulfilled, Shopify sends the order details to the script via an HTTP POST request.
* **Google Sheets:** The script processes the data and appends it as a new row in a Google Sheet.
* **Hardcoded Values:** Some values like ship-from address, delivery time window, and SMS notification settings are hardcoded into the script.

**Script Overview**

Here is a breakdown of what the script does:

**Retrieve the Shopify Order Data:**

The webhook sends order data in JSON format, which is parsed by the script.
Key details like order number, customer information, order total, and shipping address are extracted.

**Extracting Custom Attributes:**

The script looks for specific custom attributes (note_attributes) like "DDM Delivery Type" and "Delivery Date" to handle delivery-specific logic.

**Hardcoded Values:**

* Some values are hardcoded into the script for simplicity, such as:
* Ship From Name: Cake Craft UAE
* Ship From Address: Hor Al Anz East, Dubai
* Customer Mobile: 0585923497
* Delivery Time Window: Between 9:00 and 13:00
* SMS Notification: Enabled (TRUE)
  
**Duplicate Check:**

Before appending a new order to the sheet, the script checks if the order number already exists to avoid duplicates.

**Append Order Details to Google Sheet:**

* If the order number is new, it adds a row to the Google Sheet with all relevant details.

**Response:**

* After processing the order, the script sends a success response back to Shopify.


**How to Set Up**
**Create Google Sheet:**

* Create a new Google Sheet where you want to store the order data.
* Make sure the sheet has the columns listed above (in the same order).
  
**Install the Script:**

* Open the Google Sheet, go to Extensions > Apps Script.
* Paste the provided code into the script editor.

**Set Up the Webhook in Shopify:**

* In your Shopify admin, go to Settings > Notifications.
* Scroll down to the Webhooks section and click Create webhook.
* Select the event as Order Fulfillment, set the format to JSON, and paste the Google Apps Script's URL.

**Deploy the Script:**

* In the Google Apps Script editor, click on Deploy > Manage deployments.
* Deploy the script as a web app with access set to "Anyone, even anonymous".

**Testing:**

* Once the webhook is set up, fulfill a test order in your Shopify store to see the data populated in your Google Sheet.

**Customization**

If you need to modify the hardcoded values or add more details from the order, you can customize the script. Here are some values you can change:

* Ship From Details: Modify the shipFromName, shipFromAddress, and shipFromCity variables if your ship-from location changes.
* Delivery Time Window: Update the afterTime and beforeTime variables to reflect your preferred delivery window.
* Additional Order Information: Extract other order details from the Shopify webhook data by parsing additional fields from the data object.

**Conclusion**
This script provides a simple and effective way to log Shopify order details in a Google Sheet automatically using a webhook. It's customizable and scalable, so you can adjust it to suit your specific business needs.

For any issues or enhancements, feel free to reach out!
