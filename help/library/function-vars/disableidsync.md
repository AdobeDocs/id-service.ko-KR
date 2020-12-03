---
description: ID 동기화를 비활성화하는 선택적 부울 플래그입니다.
keywords: ID Service
seo-description: ID 동기화를 비활성화하는 선택적 부울 플래그입니다.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 100%

---


# disableIdSyncs{#disableidsyncs}

ID 동기화를 비활성화하는 선택적 부울 플래그입니다.

>[!NOTE]
>
>이 구성은 `idSyncDisableSyncs`이며, 2018년 1월 18일 v3.0 릴리스에서 이름이 `disableIdSyncs`로 변경되었습니다.

**구문:** `disableIdSyncs: true|false` (기본값은 `false`임)

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

