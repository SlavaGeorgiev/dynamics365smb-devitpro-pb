---
title: Get balanceSheet  
description: Gets a balance sheet object in Dynamics 365 Business Central. 
author: SusanneWindfeldPedersen
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/01/2021
ms.author: solsen
---

# Get balanceSheet

[!INCLUDE[api_v2_note](../../../includes/api_v2_note.md)]

Retrieve the properties and relationships of a balance sheet report object for [!INCLUDE[prod_short](../../../includes/prod_short.md)].

## HTTP request
Replace the URL prefix for [!INCLUDE[prod_short](../../../includes/prod_short.md)] depending on environment following the [guideline](../../v2.0/endpoints-apis-for-dynamics.md).
```
GET businesscentralPrefix/companies({id})/balanceSheets
```

## Request headers

|Header|Value|
|------|-----|
|Authorization  |Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a ```200 OK``` response code and a **balanceSheet** object in the response body.

## Example

**Request**

Here is an example of the request.
```json
GET https://{businesscentralPrefix}/api/v2.0/companies({id})/balanceSheet?$orderby=lineNumber&$filter=dateFilter eq 2020-12-30
```

**Response**

Here is an example of the response. 

> [!NOTE]  
>   The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
    "id": "a0fbf171-44e3-ea11-bb43-000d3a2feca1",
    "lineNumber": 10000,
    "display": "Assets",
    "balance": 0,
    "lineType": "header",
    "indentation": 0,
    "dateFilter": "2020-08-21"
}
```


## See also

[Tips for working with the APIs](../../../developer/devenv-connect-apps-tips.md)  
[balancesheet](../resources/dynamics_balancesheet.md)  
