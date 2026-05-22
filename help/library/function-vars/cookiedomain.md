---
description: URL의 마지막 두 부분이 3자 이상인 다중 부분의 최상위 도메인에서 필수입니다.
keywords: ID 서비스
title: cookieDomain
exl-id: 280416ad-372a-4a59-a938-0f49c0ce300f
TQID: https://experienceleague.adobe.com/V-Aej2Eh52NBXQfeUTHQHEs6Q72mzpI5HptURu6FTUM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 62
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

