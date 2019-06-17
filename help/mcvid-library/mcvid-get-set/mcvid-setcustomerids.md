---
description: setCustomerIDs는 고객 ID 및 해당 인증 상태를 정의하는 1개 이상의 키-값 쌍을 설정합니다.
keywords: ID 서비스
seo-description: setCustomerIDs는 고객 ID 및 해당 인증 상태를 정의하는 1개 이상의 키-값 쌍을 설정합니다.
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4 F 960 F 98-CEC 2-4 DB 6-84 EA -0259 E 2128 EA 2
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# setCustomerIDs{#setcustomerids}

setCustomerIDs는 고객 ID 및 해당 인증 상태를 정의하는 1개 이상의 키-값 쌍을 설정합니다.

**구문:** `visitor.setCustomerIDs()`

아래 코드 샘플에 표시된 것처럼 단일 또는 다중 ID를 설정할 수 있습니다. 자세한 내용 및 예제에 대해서는 [고객 ID 및 인증 상태](../../mcvid-reference/mcvid-authenticated-state.md)를 참조하십시오.

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
//Multiple IDs with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```

