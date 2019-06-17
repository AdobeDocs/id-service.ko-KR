---
description: Experience Cloud ID 서비스가 ID 동기화 iFrame을 로드하는 방식을 제어하는 선택적 부울 플래그입니다.
keywords: ID 서비스
seo-description: Experience Cloud ID 서비스가 ID 동기화 iFrame을 로드하는 방식을 제어하는 선택적 부울 플래그입니다.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa 2 c 2 fa 4-2 cab -4 e 08-8 d 35-729 a 6 c 3 e 459 a
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Experience Cloud ID 서비스가 ID 동기화 iFrame을 로드하는 방식을 제어하는 선택적 부울 플래그입니다.

**구문:**` `Idsyncattachiframeonwindowload = true | false &quot; `false`(기본값은

`idSyncAttachIframeOnWindowLoad: true`이면 ID 서비스가 창 로드 시 ID 동기화 iFrame을 로드합니다. 기본적으로 ID 서비스는 창 로드 대신 가능한 한 빨리 ID 동기화 iFrame을 로드합니다.

**코드 샘플**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```

