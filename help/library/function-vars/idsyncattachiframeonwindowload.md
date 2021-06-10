---
description: Experience Cloud Identity 서비스가 ID 동기화 iFrame을 로드하는 방식을 제어하는 선택적 부울 플래그입니다.
keywords: ID 서비스
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Experience Cloud Identity 서비스가 ID 동기화 iFrame을 로드하는 방식을 제어하는 선택적 부울 플래그입니다.

**구문:** ` `idSyncAttachIframeOnWindowLoad= true|false`` (기본값은 `false`임)

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
