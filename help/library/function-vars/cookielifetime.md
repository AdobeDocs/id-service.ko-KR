---
description: 이 변수를 사용하면 AMCV 쿠키의 기본 수명 간격을 무시할 수 있습니다.
keywords: ID 서비스
seo-description: 이 변수를 사용하면 AMCV 쿠키의 기본 수명 간격을 무시할 수 있습니다.
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd945db3-429a-4625-ac3f-69ac259377a3
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# cookieLifetime{#cookielifetime}

이 변수를 사용하면 AMCV 쿠키의 기본 수명 간격을 무시할 수 있습니다.

기본적으로, [!DNL Experience Cloud] ID 서비스 쿠키는 24개월 후에 만료됩니다. 시간 간격을 초 단위로 설정합니다.

**구문:** ` cookieLifetime: *`수명(초)`*`

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

