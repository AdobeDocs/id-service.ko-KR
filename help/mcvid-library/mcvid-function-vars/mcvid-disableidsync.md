---
description: ID 동기화를 비활성화하는 선택적 부울 플래그입니다.
keywords: ID 서비스
seo-description: ID 동기화를 비활성화하는 선택적 부울 플래그입니다.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8 BEA 1 DE 8-53 C 8-4 A 15-BCF 5-F 0869763 A 32 E
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableIdSyncs{#disableidsyncs}

ID 동기화를 비활성화하는 선택적 부울 플래그입니다.

>[!NOTE]
>
>이 구성은 v 3.0 2018 년 1 월 18 일 릴리스에서 `idSyncDisableSyncs``disableIdSyncs` 이름이 변경되었습니다.

**구문:**`disableIdSyncs: true|false` (기본값은 `false`.)

**코드 샘플**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

