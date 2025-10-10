---
description: 이 변수를 사용하면 AMCV 쿠키의 기본 수명 간격을 무시할 수 있습니다.
keywords: ID 서비스
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 100%

---

# cookieLifetime{#cookielifetime}

이 변수를 사용하면 AMCV 쿠키의 기본 수명 간격을 무시할 수 있습니다.

기본적으로, [!DNL Experience Cloud] ID 서비스 쿠키는 24개월 후에 만료됩니다. 시간 간격을 초 단위로 설정합니다.

**구문:** `cookieLifetime: *`수명(초)`*`

**코드 샘플**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example changes expiration period to 12-months. 
   cookieLifetime:31536000 
});
```
