---
description: '시간 제한 간격(밀리초)을 설정합니다. ID 서비스의 응답을 기다리는 시간을 다른 솔루션(예: Analytics, Audience Manager, Target 등)에 알려주는 데 사용됩니다.'
keywords: ID 서비스
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 69%

---

# loadTimeout{#loadtimeout}

시간 제한 간격(밀리초)을 설정합니다. ID 서비스의 응답을 기다리는 시간을 다른 솔루션(예: Analytics, Audience Manager, Target 등)에 알려주는 데 사용됩니다.

**구문:** `loadTimeout: *`간격(밀리 초)`*`

기본값은 30,000밀리초(30초)입니다. 기본값을 변경하지 *않는* 것이 좋습니다.

>[!NOTE]
>
>ID 서비스 호출은 페이지의 다른 비 Adobe 코드와 관련해서 비동기식으로 수행됩니다. 따라서 시간 제한 간격을 늘리거나 줄여도 페이지에서 콘텐츠를 렌더링하는 속도는 변경되지 않습니다. 그러나 시간 제한 간격이 길면 일반적인 네트워크 모니터링 도구로 측정한 페이지 로드 시간에 영향을 미칠 수 있지만 렌더링 시간은 영향을 받지 않습니다.

**코드 샘플**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```
