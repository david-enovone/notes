Take aways:
- Easier to adopt the frontend to the what the backend system generates
- Build an example of how I want the data to be structured, and then collaborate to make sure the frontend will work, iterate, and then roll out

```js
require("dotenv").config();  
const express = require("express");  
const crypto = require("crypto");  
const axios = require("axios");  
const bodyParser = require("body-parser");
const app = express();  
const SHOPIFY_SECRET = process.env.SHOPIFY_SECRET;  
const SHOPIFY_ACCESS_TOKEN = process.env.SHOPIFY_ACCESS_TOKEN;  
const SHOPIFY_SECRET_HOOK = process.env.SHOPIFY_SECRET_HOOK;app.use(  
  "/webhooks/order-created",  
  bodyParser.raw({ type: "application/json", limit: "4mb" }),  
  async (req, res, next) => {  
    const hmac = req.headers["x-shopify-hmac-sha256"];  
    // Generate the HMAC using the raw body  
    const genHash = crypto  
      .createHmac("SHA256", SHOPIFY_SECRET_HOOK)  
      .update(req.body)  
      .digest("base64");    // compare the HMAC values  
    if (genHash !== hmac) {  
      return res.status(401).send("Couldn't verify incoming Webhook request!");  
    }    // Parse the body to JSON if the HMAC verification passes  
    req.body = JSON.parse(req.body.toString("utf8"));    next();  
  }  
);app.post("/webhooks/order-created", async (req, res) => {  
  const order = req.body;  
  const orderId =  order.id;  const noteAttributes = order.note_attributes || [];  
  const shippingDateAttribute = noteAttributes.find(  
    (attr) => attr.name === "shipping_date"  
  );  
  const shippingDate = shippingDateAttribute  
  ? shippingDateAttribute.value  
  : null;  if (!shippingDate) {  
    console.error("Shipping date not found in order");  
    return res.status(400).send("Shipping date not found in order");  
  }  
  try {  
    console.log(`Adding metafield to order ${orderId}`);  
    await axios.post(  
      `[https://teststoredandev.myshopify.com/admin/api/2024-07/orders/${orderId}/metafields.json](https://teststoredandev.myshopify.com/admin/api/2024-07/orders/$%7BorderId%7D/metafields.json)`,  
      {  
        metafield: {  
          namespace: "custom",  
          key: "ordershipdate",  
          value: shippingDate,  
          type: "date",  
        },  
      },  
      {  
        headers: {  
          "X-Shopify-Access-Token": SHOPIFY_ACCESS_TOKEN,  
          "Content-Type": "application/json",  
        },  
      }  
    );    if (!shippingDate) {  
      console.error("Shipping date not found in order", orderId);  
      return res.status(400).send("Shipping date not found in order");  
    } else {  
      const updatedTags = order.tags  
        ? `${order.tags}, Exception - Hold Until Date`  
        : "Exception - Hold Until Date";  
      console.log(`Updating tags for order ${orderId}`);  
      await axios.put(  
        `[https://teststoredandev.myshopify.com/admin/api/2024-07/orders/${orderId}.json](https://teststoredandev.myshopify.com/admin/api/2024-07/orders/$%7BorderId%7D.json)`,  
        {  
          order: {  
            id: orderId,  
            tags: updatedTags,  
          },  
        },  
        {  
          headers: {  
            "X-Shopify-Access-Token": SHOPIFY_ACCESS_TOKEN,  
            "Content-Type": "application/json",  
          },  
        }  
      );  
    }  
    const fulfillmentOrdersResponse = await axios.get(  
      `[https://teststoredandev.myshopify.com/admin/api/2024-07/orders/${orderId}/fulfillment_orders.json](https://teststoredandev.myshopify.com/admin/api/2024-07/orders/$%7BorderId%7D/fulfillment_orders.json)`,  
      {  
        headers: {  
          "X-Shopify-Access-Token": SHOPIFY_ACCESS_TOKEN,  
          "Content-Type": "application/json",  
        },  
      }  
    );    const fulfillmentOrders = fulfillmentOrdersResponse.data.fulfillment_orders;  
    const fulfillmentOrderId = fulfillmentOrders[0]?.id;    if (fulfillmentOrderId) {  
      console.log(`Placing fulfillment order ${fulfillmentOrderId} on hold`);      await axios.post(  
        `[https://teststoredandev.myshopify.com/admin/api/2024-07/fulfillment_orders/${fulfillmentOrderId}/hold.json](https://teststoredandev.myshopify.com/admin/api/2024-07/fulfillment_orders/$%7BfulfillmentOrderId%7D/hold.json)`,  
        {  
          fulfillment_hold: {  
            reason: "other",  
            reason_notes: "Some reason",  
          },  
        },  
        {  
          headers: {  
            "X-Shopify-Access-Token": SHOPIFY_ACCESS_TOKEN,  
            "Content-Type": "application/json",  
          },  
        }  
      );  
    }    res.status(200).send("Metafield added successfully");  
  } catch (error) {  
    console.error(  
      "Failed to add metafield:",  
      error.response ? error.response.data : error.message  
    );  
    res.status(500).send("Failed to add metafield");  
  }  
});  
app.listen(3000, () => {  
  console.log("Server is running on port 3000");  
});
```

```python
import requests  
import os  
from dotenv import load_dotenv  
import logging  
# Set up logging  
logging.basicConfig(level=logging.INFO)  
logger = logging.getLogger(name)  
# Load environment variables from .env file  
load_dotenv()  
# Shopify store and access token from environment variables  
SHOPIFY_STORE = os.getenv("SHOPIFY_STORE")  
ACCESS_TOKEN = os.getenv("ACCESS_TOKEN")  
# Debugging: Print environment variables safely  
if not SHOPIFY_STORE or not ACCESS_TOKEN:  
    logger.error("Environment variables not set properly!")  
    raise ValueError("Environment variables not set properly!")  
customer_id = 8375675158862  # Example customer ID  
# Add a metafield to the customer  
try:  
    logger.info(f"Adding metafield to customer {customer_id}")  
    # URL for the metafield POST request for a customer  
    url = f"{SHOPIFY_STORE}/admin/api/2024-07/customers/{customer_id}/metafields.json"  
    # Metafield data  
    metafield_data = {  
        "metafield": {  
            "namespace": "custom",  
            "key": "test_metafield",  
            "value": "New value",  
            "type": "string"  
        }  
    }  
    # Set headers for the API request  
    headers = {  
        "X-Shopify-Access-Token": ACCESS_TOKEN,  
        "Content-Type": "application/json"  
    }  
    # Send POST request to add metafield to customer  
    response = requests.post(url, json=metafield_data, headers=headers)  
    # Check if the request was successful  
    if response.status_code == 201:  
        logger.info("Metafield added successfully!")  
        logger.debug(response.json())  # Output the response for verification (only in debug mode)  
    else:  
        logger.error(f"Failed to add metafield. Status code: {response.status_code}")  
        logger.error(response.text)  
except Exception as e:  
    logger.error(f"An error occurred: {e}")
```
