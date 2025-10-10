---
description: URL의 마지막 두 부분이 3자 이상인 다중 부분의 최상위 도메인에서 필수입니다.
keywords: ID 서비스
title: cookieDomain
exl-id: 280416ad-372a-4a59-a938-0f49c0ce300f
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 100%

---

# cookieDomain{#cookiedomain}

URL의 마지막 두 부분이 3자 이상인 다중 부분의 최상위 도메인에서 필수입니다.

**구문:** `cookieDomain: "*`URL`*"` (`www` 접두어는 필수 아님)

**사용 사례**

* 필수 여부: `www.example.com.uk`
* 필요하지 않습니다: `www.example.co.uk`

**코드 샘플**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   cookieDomain:"example.com.uk" 
});
```
