---
title: "OpenAPI Specification"
description: "OpenAPI Specification for Dynamics 365 Business Central"
author: SusanneWindfeldPedersen
ms.date: 09/10/2021
ms.topic: article
ms.author: solsen
---

# OpenAPI Specification for Dynamics 365 Business Central

Standard APIs for Business Central are available as an [OpenAPI Specification (OAS)](https://swagger.io/specification/). OAS defines a standard interface to RESTful APIs, providing a uniform access to APIs and documentation.  

> [!IMPORTANT]  
> At this point in time, there is no downloadable .yaml file for version 2.0 of the API. This topic explains how to preview the OpenAPI contract based on a version 1.0 of the .yaml file. 

## Download Business Central OpenAPI specification

|API Version|YAML|
|-----------|------|
|1.0|[Download](../v1.0/contracts/BCOAS1.0.yaml)|

The OAS is set up to use OAuth2 and accessing the default sandbox environment. Details can be changed in the contact to connect to specific environments (servers URL). YAML can be converted to JSON if needed.

## Previewing the OpenAPI contract

There are [extensions](https://marketplace.visualstudio.com/search?term=openapi&target=VSCode&category=All%20categories&sortBy=Relevance) for Visual Studio Code that enable previewing and editing. [SwaggerHub](https://swagger.io/tools/swaggerhub/) enables previewing and editing online.

To run SwaggerUI locally, node.js can be used to serve the SwaggerUI, by following the steps below:

1) Download OAS for Business Central as shown above.
2) Install [Node.js](https://nodejs.org/en/download/).
3) Copy the javascript code shown below and save it to a file with the filename `BC_OAS.js`.  

    ```javascript
    const express = require('express');
    const app = express();
    const port = 3000;
    const swaggerUi = require('swagger-ui-express');
    const YAML = require('yamljs');
    const swaggerDocument = YAML.load('./BCOAS1.0.yaml'); 

    //const swaggerDocument = require('./BCOAS1.0.json');

    var options = { };
    app.use('/', swaggerUi.serve, swaggerUi.setup(swaggerDocument, options));
    app.listen(port, () => console.log(`Swagger UI for Business Central listening on port ${port}!`))
    ```

4) Install the required node packages by running *npm* from the command line:  
    ```
    npm install express swagger-ui-express yamljs
    ```
5) Run the node app created. From the command line run the following:
    ```
    node BC_OAS.js
    ```
6) Browse to `https://localhost:3000`.
7) To use **Try it out** authorization in SwaggerUI, an Azure Active Directory app must be created. [Follow these steps to create an AAD app, with access to Business Central](../../developer/devenv-develop-connect-apps.md#AAD). Copy and paste the client ID from the AAD app into the authorization dialog of SwaggerUI.

> [!NOTE]  
> For OAuth2 testing purposes, a multi-tenant AAD app has been created. Admin consent is needed. Client ID : 060af3ac-70c3-4c14-92bb-8a88230f3f38.

## See Also

[Developing Connect Apps for Dynamics 365 Business Central](../../developer/devenv-develop-connect-apps.md)  
