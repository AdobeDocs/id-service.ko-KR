---
description: ID 동기화를 비활성화하는 선택적 부울 플래그입니다.
keywords: ID 서비스
title: disableIdSyncs
exl-id: 96d42133-6040-4da3-9315-fd94318b33aa
TQID: https://experienceleague.adobe.com/ltW03vCXP9-8G7kJ8KwKOwAOgrsxkTxSoGzImR7dax0
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 39
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

