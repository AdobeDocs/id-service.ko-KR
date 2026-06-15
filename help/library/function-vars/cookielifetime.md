---
description: 이 변수를 사용하면 AMCV 쿠키의 기본 수명 간격을 무시할 수 있습니다.
keywords: ID 서비스
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
TQID: https://experienceleague.adobe.com/EBAkG9W3VE4p7Xd5NkegOtFDNo6qBOKrKRaBUYwwJog
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 51
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

