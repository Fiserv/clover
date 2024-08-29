---
title: "Retrieve an API key (PAKMS)"
slug: "getapikey"
excerpt: "Retrieve the public API key associated with the specific merchant and developer app. The merchant UUID (mId) and app UUID are pulled from the authtoken used. If `AutoActivateOnGet` is `true`, an API key is generated (if one does not exist)."
hidden: false
createdAt: "Fri Feb 07 2020 12:12:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 30 2024 00:05:02 GMT+0000 (Coordinated Universal Time)"
---
Using this endpoint retrieves a Public Access Key Management Service (PAKMS) key. This key is required to identify the merchant who is tokenizing their customers' cards.

To generate a PAKMS key, send a GET request to the `/v1/pakms/apikey` endpoint. Set the `authorization: Bearer `header value as an [OAuth-generated](doc:oauth-intro) `auth_token` for a test merchant with [specific permissions](doc:ecommerce-app-permissions).
