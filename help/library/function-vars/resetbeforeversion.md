---
description: 이 구성을 사용하면 업데이트할 ID 서비스 버전에 따라 고립되었거나 오래된 ECID(Experience Cloud ID)를 지울 수 있습니다.
keywords: ID 서비스
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# resetBeforeVersion{#resetbeforeversion}

이 구성을 사용하면 업데이트할 ID 서비스 버전에 따라 고립되었거나 오래된 ECID(Experience Cloud ID)를 지울 수 있습니다.

ID 서비스 버전을 `resetBeforeVersion` 변수 값으로 제공하면 오래된 ECID가 클라이언트 측 ID에서 지워집니다.

세션 시간 제한과 같은 일부 조건으로 인해 ID 서비스가 서버측 ID를 성공적으로 가져오지 않고 클라이언트측 ID가 생성될 수 있습니다. 이 경우 도메인 간에 추적하거나 다른 솔루션과 적절히 동기화할 수 없는 상태에서 고립 클라이언트측 ID가 ID 서비스에 의해 추적됩니다. 이 동작은 현재 AMCV 쿠키의 버전을 `resetBeforeVersion`의 값과 비교합니다. 쿠키가 존재하지 않거나 쿠키 버전이 `resetBeforeVersion`의 최신 릴리스 버전보다 오래된 경우 AMCV 쿠키가 제거되고 ID 서비스가 새고 고친 ECID를 요청합니다.

브라우저에 타사 Demdex 쿠키가 있는 방문자의 경우 ECID를 확인하여 Demdex 쿠키에서 UUID를 사용해 ECID가 올바르게 생성되었는지 확인합니다. 그렇게 확인해서 참으로 판명되면 새 ECID는 동일하며 방문자는 새 방문자로 간주됩니다. 어떤 이유로 지워지는 ECID가 Demdex 쿠키를 사용하여 생성되지 않았거나 Demdex 쿠키가 없는 경우 방문자는 새 ECID를 받고 새 방문자로 간주됩니다.

**구문:** `resetBeforeVersion = "3.3"`

**코드 샘플**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Marketing Cloud organization ID here", { 
  
    //Same as s.trackingServer 
    trackingServer: "Insert tracking server here ", 
  
    //Same as s.trackingServerSecure 
    trackingServerSecure: "Insert secure tracking server here", 
  
    //For CNAME support only. Exclude these variables if you're not using CNAME 
    marketingCloudServer: "Insert tracking server here", 
    marketingCloudServerSecure: "Insert secure tracking server here", 
  
    //Changing the version 
    resetBeforeVersion: "3.3" 
});
```
