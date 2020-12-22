---
title: "List appConsentRequestsForApproval"
description: "List the appConsentRequest resources from the appConsentRequestsForApproval navigation property."
author: "Zawad"
localization_priority: Normal
ms.prod: "microsoft-identity-platform"
doc_type: apiPageType
---

# List appConsentRequestsForApproval
Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

List the [appConsentRequest](../resources/appconsentrequest.md) resources from the **appConsentRequestsForApproval** navigation property. Registered reviewers can obtain the list of pending appConsentRequests that require their review. 

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type|Permissions (from most to least privileged)|
|:---|:---|
|Delegated (work or school account)|ConsentRequest.Read.All, ConsentRequest.ReadWrite.All |
|Delegated (personal Microsoft account)|Not supported. |
|Application|Not supported. |

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /me/appConsentRequestsForApproval/
GET /me/appConsentRequestsForApproval/{id}/userConsentRequests
```

## Optional query parameters
This method supports the `$skip`, and `$top` OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|

## Request body
Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [appConsentRequest](../resources/appconsentrequest.md) objects in the response body.

## Example 1: List all appConsentRequestsForApproval that you are an approver of

### Request
<!-- {
  "blockType": "request",
  "name": "list_appconsentrequest"
}
-->
``` http
GET https://graph.microsoft.com/beta/me/appConsentRequestsForApproval/
```


### Response
**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.appConsentRequest)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('22075847-329a-4195-8bcf-2775ee97f0a8')/appConsentRequestsForApproval",
      "@odata.count": 1,
      "value": [
        {
          "id": "5a3a0f94-b89d-4cd3-a4ad-fd78faec333f",
          "appId": "3fa97b03-0af0-4773-93ed-4c247cb62ce2",
          "appDisplayName": "Salesforce",
          "consentType": "Dynamic",
          "pendingScopes": [
            {
              "displayName": "Salesforce.ReadWrite.Users"
            },
            {
              "displayName": "Salesforce.ReadWrite.Groups"
            }
          ]
        }
      ]
    }
  ]
}
```

## Example 2: List all userConsentRequests for the appConsentRequests that are pending your approval

### Request
<!-- {
  "blockType": "request",
  "name": "list_appconsentrequest_userconsentrequest"
}
-->
``` http
GET /me/appConsentRequestsForApproval/{id}/userConsentRequests
```


### Response
**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.appConsentRequest)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('22075847-329a-4195-8bcf-2775ee97f0a8')/appConsentRequestsForApproval('b3c380a0-9180-445c-b20e-1d76e7b51df7')/userConsentRequests",
    "@odata.count": 2,
    "value": [
        {
            "id": "e8b37cac-33a9-4be9-b728-87281944058f",
            "reason": "I need this app to work.",
            "status": "InProgress",
            "createdDateTime": "2020-12-21T21:17:05.8975992Z",
            "createdBy": {
                "id": "37244623-9df1-44df-846c-e11b37e7400f",
                "displayName": "Grady Archie",
                "userPrincipalName": "GradyA@contoso.com",
                "mail": "GradyA@constoso.com",
                "user": {
                    "id": "37244623-9df1-44df-846c-e11b37e7400f",
                    "displayName": "Grady Archie",
                    "userPrincipalName": "GradyA@contosocom",
                    "mail": "GradyA@contoso.com"
                }
            },
            "approval@odata.context": "https://graph.microsoft.com/beta/$metadata#users('22075847-329a-4195-8bcf-2775ee97f0a8')/appConsentRequestsForApproval('b3c380a0-9180-445c-b20e-1d76e7b51df7')/userConsentRequests('e8b37cac-33a9-4be9-b728-87281944058f')/approval/$entity",
            "approval": null
        },
        {
            "id": "2689fcfd-cb87-4e36-a51f-5720fd88429d",
            "reason": "I wish to beta test this app.",
            "status": "InProgress",
            "createdDateTime": "2020-12-21T21:11:25.3493113Z",
            "createdBy": {
                "id": "eda30546-2cec-4bb2-bd89-ff04aaf135a7",
                "displayName": "Adele Vance",
                "userPrincipalName": "AdeleV@contoso.com",
                "mail": "AdeleV@contoso.com",
                "user": {
                    "id": "eda30546-2cec-4bb2-bd89-ff04aaf135a7",
                    "displayName": "Adele Vance",
                    "userPrincipalName": "AdeleV@contoso.com",
                    "mail": "AdeleV@contoso.com"
                }
            },
            "approval@odata.context": "https://graph.microsoft.com/beta/$metadata#users('22075847-329a-4195-8bcf-2775ee97f0a8')/appConsentRequestsForApproval('b3c380a0-9180-445c-b20e-1d76e7b51df7')/userConsentRequests('2689fcfd-cb87-4e36-a51f-5720fd88429d')/approval/$entity",
            "approval": null
        }
    ]
}
```
