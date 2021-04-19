---
description: URL의 마지막 두 부분이 3자 이상인 다중 부분의 최상위 도메인에서 필수입니다.
keywords: ID 서비스
seo-description: URL의 마지막 두 부분이 3자 이상인 다중 부분의 최상위 도메인에서 필수입니다.
seo-title: cookieDomain
title: cookieDomain
uuid: a57e5477-c07b-4d54-8aea-8e8b152f1423
exl-id: 280416ad-372a-4a59-a938-0f49c0ce300f
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '76'
ht-degree: 100%

---

# cookieDomain{#cookiedomain}

URL의 마지막 두 부분이 3자 이상인 다중 부분의 최상위 도메인에서 필수입니다.

**구문:** ` cookieDomain: " *`URL`*"` (`www` 접두어는 필수 아님)

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
