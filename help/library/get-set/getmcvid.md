---
description: getMarketingCloudVisitorID는 ECID를 반환합니다.
keywords: 방문자 ID 서비스
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
TQID: https://experienceleague.adobe.com/Ltpdq4dlGbJ8h0vAZBD52Pq7gLaurxSDYqETkLqQfDw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 118
ht-degree: 52%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID는 ECID를 반환합니다.

**구문:** `var *`변수 이름`* = visitor.getMarketingCloudVisitorID()`

이 메서드는 일반적으로 방문자 ID를 읽어야 하는 사용자 지정 솔루션에 사용됩니다. 표준 구현에서는 사용되지 않습니다. `getMarketingCloudVisitorID`은(는) 콜백 함수에서도 작동하여 Analytics ID를 읽은 후 시스템 또는 애플리케이션으로 가져옵니다.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the ECID 
}; 
 
//get the ECID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>Analytics 고객인 경우 Analytics ID도 확인한 후 함수로 보내십시오. 예를 들어 숨겨진 양식 요소의 방문자 ID를 데이터 삽입 API를 사용하는 서버측 애플리케이션에 전달할 때 두 식별자를 모두 원할 수 있습니다. 이 경우 ECID 및 Analytics 방문자 ID를 수집한 후 반환해야 합니다. [Analytics 방문자 ID 가져오기](../../library/get-set/getanalyticsvisitorid.md)를 참조하십시오.

