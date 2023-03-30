# ABBYY Readme

## 1 Introduction

The ABBYY Connector provides a way for you to enrich your Mendix app with the capability to extract data from documents.
**1.1 Typical Use Cases**
Extract data from documents in a structured manner.
**1.2 Prerequisites**
The ABBYY connector requires the Community Commons and Nanoflow Commons modules for atuhentication purposes. MxModelReflection is needed for mapping Concepts to MxObjects.

## 2 Installation

Follow the instructions in [How to Use Marketplace Content in Studio Pro](https://docs.mendix.com/appstore/general/app-store-content/) to import the ABBYY connector into your app.

## 3 Configuration

After you install the connector, you can find it in the **App Explorer**, in the **ABBYYConnector** section. The connector provides a [domain model](https://docs.mendix.com/appstore/connectors/aws/amazon-textract/#domain-model) and several [activities](https://docs.mendix.com/appstore/connectors/aws/amazon-textract/#activities) that you can use to connect your app to ABBYY. Each activity can be implemented by using it in a microflow. You must also configure the constants for the connector and set up an authorization flow.

**3.1 Configuring ABBYY Connector**
In order to use the ABBYY service, you need an ABBYY Vantage account: [Intelligent document processing for the Digital Workforce | ABBYY Vantage](https://www.abbyy.com/vantage/)

Create a new client in the ABBYY Vantage to retrieve the ClientId and ClientSecret. Set constant values Client_ID and Client_Secret in the Mendix environment with these values. Set the constant Endpoint (default is https://vantage-eu.abbyy.com)

Register the callback url in the ABBY Vantage environment as redirect URL (e.g. http://localhost:8080/rest/v1/callback or https://myapp.mendixcloud.com/rest/v1/callback)

**3.2 Authorization**
Use nanoflow ACT_Authorize_AuthorizationCodeFlow to authorize the application with your ABBYY credentials. You can add this nanoflow to a page in your application.

You can sue the microflow ACT_AuthorizationToken_View to view and manage the authorization token details.

## 4. Usage

Get Skills will provide an overview of all the skills that are available. Use Launch Transaction to start analyzing a document, this will return a TransactionId. Use the Get Transaction action to retrieve the latest status. After processing use Download Result to get the extracted data.

