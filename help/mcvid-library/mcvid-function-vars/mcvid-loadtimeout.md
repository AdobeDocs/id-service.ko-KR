---
description: '시간 제한을 밀리초로 설정합니다. 다른 솔루션(예: Analytics, Audience Manager, Target 등)에 ID 서비스에서 응답을 기다리는 시간을 알려주는 데 사용됩니다.'
keywords: ID 서비스
seo-description: '시간 제한을 밀리초로 설정합니다. 다른 솔루션(예: Analytics, Audience Manager, Target 등)에 ID 서비스에서 응답을 기다리는 시간을 알려주는 데 사용됩니다.'
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# loadTimeout{#loadtimeout}

시간 제한을 밀리초로 설정합니다. 다른 솔루션(예: Analytics, Audience Manager, Target 등)에 ID 서비스에서 응답을 기다리는 시간을 알려주는 데 사용됩니다.

**구문:** ` loadTimeout: *`간격(밀리 초)`*`

기본값은 30,000밀리초(30초)입니다. 기본값을 변경하지 *않는* 것이 좋습니다.

>[!NOTE]
>
>ID 서비스 호출은 페이지의 다른 비 Adobe 코드와 관련해서 비동기식으로 수행됩니다. 따라서 시간 초과 간격을 늘리거나 줄여도 페이지에서 컨텐츠가 렌더링되는 속도는 변경되지 않습니다. 그렇지만 시간 초과 간격이 길면 일반적인 네트워크 모니터링 도구에 의해 측정된 페이지 로드 시간에 영향을 줄 수 있지만 렌더링 시간은 영향을 받지 않습니다.

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

