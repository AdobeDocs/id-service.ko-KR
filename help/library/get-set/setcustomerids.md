---
description: setCustomerIDs는 고객 ID 및 해당 인증 상태를 정의하는 1개 이상의 키-값 쌍을 설정합니다.
keywords: ID 서비스
seo-description: setCustomerIDs는 고객 ID 및 해당 인증 상태를 정의하는 1개 이상의 키-값 쌍을 설정합니다.
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4f960f98-cec2-4db6-84ea-0259e2128ea2
translation-type: ht
source-git-commit: 21fb12b817b7c8cd34e6022ca6c188229228d1df

---


# setCustomerIDs{#setcustomerids}

setCustomerIDs는 고객 ID 및 해당 인증 상태를 정의하는 1개 이상의 키-값 쌍을 설정합니다.

**구문:** `visitor.setCustomerIDs()`

아래 코드 샘플에 표시된 것처럼 단일 또는 다중 ID를 설정할 수 있습니다. 자세한 내용 및 예는 [고객 ID 및 인증 상태](../../reference/authenticated-state.md)를 참조하십시오.

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
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```

