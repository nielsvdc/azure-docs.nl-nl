---
title: Web-Api's aanroepen vanuit een desktop-app-micro soft Identity platform | Azure
description: Meer informatie over het bouwen van een bureau blad-app die web-Api's aanroept
services: active-directory
author: jmprieur
manager: CelesteDG
ms.service: active-directory
ms.subservice: develop
ms.topic: conceptual
ms.workload: identity
ms.date: 10/30/2019
ms.author: jmprieur
ms.custom: aaddev
ms.openlocfilehash: 274dc731b69686a67a9ac5dba25a5d9c98581652
ms.sourcegitcommit: 6109f1d9f0acd8e5d1c1775bc9aa7c61ca076c45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94444041"
---
# <a name="desktop-app-that-calls-web-apis-call-a-web-api"></a>Bureau blad-app die web-Api's aanroept: een web-API aanroepen

Nu u een token hebt, kunt u een beveiligde web-API aanroepen.

## <a name="call-a-web-api"></a>Een web-API aanroepen

# <a name="net"></a>[.NET](#tab/dotnet)

[!INCLUDE [Call web API in .NET](../../../includes/active-directory-develop-scenarios-call-apis-dotnet.md)]

<!--
More includes will come later for Python and Java
-->
# <a name="python"></a>[Python](#tab/python)

```Python
endpoint = "url to the API"
http_headers = {'Authorization': 'Bearer ' + result['access_token'],
                'Accept': 'application/json',
                'Content-Type': 'application/json'}
data = requests.get(endpoint, headers=http_headers, stream=False).json()
```

# <a name="java"></a>[Java](#tab/java)

```Java
HttpURLConnection conn = (HttpURLConnection) url.openConnection();

// Set the appropriate header fields in the request header.
conn.setRequestProperty("Authorization", "Bearer " + accessToken);
conn.setRequestProperty("Accept", "application/json");

String response = HttpClientHelper.getResponseStringFromConn(conn);

int responseCode = conn.getResponseCode();
if(responseCode != HttpURLConnection.HTTP_OK) {
    throw new IOException(response);
}

JSONObject responseObject = HttpClientHelper.processResponse(responseCode, response);
```

# <a name="macos"></a>[macOS](#tab/macOS)

## <a name="call-a-web-api-in-msal-for-ios-and-macos"></a>Een web-API aanroepen in MSAL voor iOS en macOS

De methoden voor het verkrijgen van tokens retour neren een `MSALResult` object. `MSALResult` beschrijft een `accessToken` eigenschap die kan worden gebruikt om een web-API aan te roepen. Voeg een toegangs token toe aan de HTTP-autorisatie-header voordat u de aanroep gaat gebruiken om toegang te krijgen tot de beveiligde web-API.

Doel-C:

```objc
NSMutableURLRequest *urlRequest = [NSMutableURLRequest new];
urlRequest.URL = [NSURL URLWithString:"https://contoso.api.com"];
urlRequest.HTTPMethod = @"GET";
urlRequest.allHTTPHeaderFields = @{ @"Authorization" : [NSString stringWithFormat:@"Bearer %@", accessToken] };

NSURLSessionDataTask *task =
[[NSURLSession sharedSession] dataTaskWithRequest:urlRequest
     completionHandler:^(NSData * _Nullable data, NSURLResponse * _Nullable response, NSError * _Nullable error) {}];
[task resume];
```

Swift

```swift
let urlRequest = NSMutableURLRequest()
urlRequest.url = URL(string: "https://contoso.api.com")!
urlRequest.httpMethod = "GET"
urlRequest.allHTTPHeaderFields = [ "Authorization" : "Bearer \(accessToken)" ]

let task = URLSession.shared.dataTask(with: urlRequest as URLRequest) { (data: Data?, response: URLResponse?, error: Error?) in }
task.resume()
```

## <a name="call-several-apis-incremental-consent-and-conditional-access"></a>Meerdere Api's aanroepen: stapsgewijze toestemming en voorwaardelijke toegang

Als u meerdere Api's voor dezelfde gebruiker wilt aanroepen, moet u na het ophalen van een token voor de eerste API bellen `AcquireTokenSilent` . U ontvangt een token voor de andere Api's de meeste tijd op de achtergrond.

```csharp
var result = await app.AcquireTokenXX("scopeApi1")
                      .ExecuteAsync();

result = await app.AcquireTokenSilent("scopeApi2")
                  .ExecuteAsync();
```

Interactie is vereist wanneer:

- De gebruiker heeft toestemming gegeven voor de eerste API, maar nu moet worden gestemd op meer bereiken. Dit soort toestemming wordt incrementele toestemming genoemd.
- De eerste API heeft geen multi-factor Authentication nodig, maar de volgende.

```csharp
var result = await app.AcquireTokenXX("scopeApi1")
                      .ExecuteAsync();

try
{
 result = await app.AcquireTokenSilent("scopeApi2")
                  .ExecuteAsync();
}
catch(MsalUiRequiredException ex)
{
 result = await app.AcquireTokenInteractive("scopeApi2")
                  .WithClaims(ex.Claims)
                  .ExecuteAsync();
}
```
---

## <a name="next-steps"></a>Volgende stappen

Ga naar het volgende artikel in dit scenario en [Ga naar productie](scenario-desktop-production.md).
