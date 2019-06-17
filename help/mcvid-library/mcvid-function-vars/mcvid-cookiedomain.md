---
description: URL의 마지막 두 부분이 3자 이상인 다중 부분의 최상위 도메인에서 필수입니다.
keywords: ID 서비스
seo-description: URL의 마지막 두 부분이 3자 이상인 다중 부분의 최상위 도메인에서 필수입니다.
seo-title: cookieDomain
title: cookieDomain
uuid: A 57 E 5477-C 07 B -4 D 54-8 AEA -8 E 8 B 152 F 1423
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# cookieDomain{#cookiedomain}

URL의 마지막 두 부분이 3자 이상인 다중 부분의 최상위 도메인에서 필수입니다.

**구문:**` cookieDomain: " *`URL`*"` ( `www` 접두사가 필요하지 않습니다.)

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
