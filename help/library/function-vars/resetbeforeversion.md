---
description: 이 구성을 사용하면 업데이트할 ID 서비스 버전에 따라 고립되었거나 오래된 ECID(Experience Cloud ID)를 지울 수 있습니다.
keywords: ID 서비스
seo-description: 이 구성을 사용하면 업데이트할 ID 서비스 버전에 따라 고립되었거나 오래된 ECID(Experience Cloud ID)를 지울 수 있습니다.
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# resetBeforeVersion{#resetbeforeversion}

이 구성을 사용하면 업데이트할 ID 서비스 버전에 따라 고립되었거나 오래된 ECID(Experience Cloud ID)를 지울 수 있습니다.

ID 서비스 버전을 `resetBeforeVersion` 변수 값으로 제공하면 오래된 ECID가 클라이언트 측 ID에서 지워집니다.

세션 시간 초과와 같은 일부 조건으로 인해 ID 서비스가 서버 측 ID를 가져오지 않고 클라이언트 측 ID가 생성될 수 있습니다. 이 경우에는 도메인 간에 추적되거나 다른 솔루션과 제대로 동기화되지 않고 ID 서비스에서 고립된 클라이언트 측 ID를 추적합니다. 이 동작은 현재 AMCV 쿠키의 버전을 `resetBeforeVersion`의 값과 비교합니다. 쿠키가 존재하지 않거나 쿠키 버전이 `resetBeforeVersion`의 최신 릴리스 버전보다 오래된 경우 AMCV 쿠키가 제거되고 ID 서비스가 새고 고친 ECID를 요청합니다.

브라우저에 타사 Demdex 쿠키가 있는 방문자의 경우 ECID를 확인하여 Demdex 쿠키에서 UUID를 사용해 ECID가 올바르게 생성되었는지 확인합니다. 확인 결과가 true이면 새 ECID가 동일한 것이므로 방문자가 새로운 방문자로 간주됩니다. 어떤 이유로 지워진 ECID가 Demdex 쿠키를 사용하여 생성되지 않은 경우 또는 Demdex 쿠키가 없는 경우 방문자는 새 ECID를 받게 되며 새로운 방문자로 간주됩니다.

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

