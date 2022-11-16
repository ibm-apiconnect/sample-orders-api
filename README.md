# API Sample: Order tracking

This git repo contains a sample API to use with API Connect.  If you want to try API Connect, you can sign up for a [free 30 day trial](https://register.automation.ibm.com/apic/trial/aws?source=github_sample) and import this API.


This document will guide you through the introductory/basic steps to import the sample API into your API Connect instance, create an API definition, and test the response of your API in order to validate the API returns what you expect.

## About this sample

These days we all have purchased something online and after your payment is successful, you are provided a tracking number which enables you to track your package and receive daily status on your package.

This API demonstrates how you can build a composite API within API Connect combining data from two different backend sources - our order fulfillment system and the delivery companies shipment tracking to provide an order tracking API for App Developers to build on.  

Firstly the API takes the input of an order number and then uses it to query our mock internal order system to return the status of the order.  Within the order status returned we have the details of which delivery company the parcel was shipped with and the associated tracking reference.  Our API then passes these to a Lambda function to look up the parcel status from the appropriate shipping company. 


## Step by step guide:

1. Click here to access the [sample API](https://raw.githubusercontent.com/ibm-apiconnect/sample-orders-api/doc-changes/api/orders_api.yaml) in the github page

    - navigate to the API folder, open the “order_api.yaml” file and click raw
    - Then navigate to the API Connect Instance and follow the next step to import/paste the URL

2. Import the sample to your API Connect instance

 - In the homepage, select “Develop API”
 - Click "Add" and then select "API from REST, GraphGL or SOAP"
 - On the next page select Import "existing OpenAPI"
 - Paste the URL path (from step 1) `https://raw.githubusercontent.com/ibm-apiconnect/sample-orders-api/doc-changes/api/orders_api.yaml` in the "specify a file URL" field

**NB.** if you have previously imported the same API you will need to delete it first otherwise you will get an error. 

3. Activate the API
    - check the “Activate API” box and click Next
    - By activating your API, you now published the API into the development sandbox in order to test it right away. 
    - your API is now online and there are details such as Catalog URL and Sample Sandbox credentials which you don’t need to worry about at this point. 
    - Click "Edit API" to proceed to testing the API

4. Explore the API definition
    - On the “design” tab, you explore “API specifications”, “Path” and details about  your API definition presented on the left hand side navigation. 
    - Navigate to the “gateway” tab to view the flow
    - **order lookup**: invoke policy which calls the order fulfillment system to retrieve the order details for the provided order number such as “order status” ,“ shipping carrier”, “tracking number” 
    - **parse response**:  The gateway parses the JSON response containing the order details so the values can be used further in the flow. 
    - **map input to lambda**: take the “tracking number” and “shipping carrier” from the order details to build the input needed to invoke the Lambda function
    - **lambda: track shipment** : Call lambda function to look up the tracking for a  parcel with the associated shipping company.
    - **combine data for response**: map policy to take both responses and combine the data them into a single output so when the customer calls this API, they get both the order details from the company order database and shipping status from the carrier. 

** Please make sure your service is “online” so if it’s offline, click on the toggle to switch it make your API online and publish it to the gateway.

5. Test the API
    - Click on to the Test tab on the top
    - Type in a value to use for the “order-number” field and click “Send”
    - Now you can see the tracking details output.
    - we have the order “create_at” date coming form ordering Database
    - we also have the “status” of the order as “shipped” and the “shipped_at” date
    - you can see the "tracking_status" section showing the data from the shipping company
    - You can now click on the “Trace” tab to view how the API has gone through every step and debug your API.

You have now completed the introductory/basic steps to import the sample API, create an API definition, and test the API response. 

## Further things to do in API Connect

 - [**Secure**](https://www.ibm.com/docs/en/api-connect/saas?topic=apis-security-authentication) your API with additional security requirements such as OAuth
 - [**Automate**](automate.md) your API deployment as part of a CI/CD pipeline
 - **Analyse** your API traffic using the Analytics dashboards