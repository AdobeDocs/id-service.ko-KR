---
description: Experience Cloud ID 서비스가 ID 동기화 iFrame을 로드하는 방식을 제어하는 선택적 부울 플래그입니다.
keywords: ID 서비스
seo-description: Experience Cloud ID 서비스가 ID 동기화 iFrame을 로드하는 방식을 제어하는 선택적 부울 플래그입니다.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
translation-type: ht
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Experience Cloud ID 서비스가 ID 동기화 iFrame을 로드하는 방식을 제어하는 선택적 부울 플래그입니다.

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

