---
description: AMCV 쿠키에 "Secure" 속성을 추가하는 선택적 부울 플래그입니다.
keywords: ID 서비스
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
TQID: https://experienceleague.adobe.com/UBhpXY4BvJiEDp6Adje--6ng-4W12RCWun2CpMFD3kU
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 93
ht-degree: 100%

---

# secureCookie{#securecookie}

AMCV 쿠키에 &quot;Secure&quot; 속성을 추가하는 선택적 부울 플래그입니다.

이 구성 속성은 `visitorAPI` 버전 3.3.0에서 사용 가능합니다.

>[!NOTE]
>
>`SecureCookie` 구성은 비보안 도메인에서 작동하지 않으며, 비보안 프로토콜을 사용하는 방문의 경우 MID 값을 수신할 수 없습니다. 모든 페이지 및 하위 도메인에서 항상 보안 프로토콜을 사용 중인 경우에만 `secureCookie` 구성을 `true`로 설정해야 합니다.

**구문:** `secureCookie: true | false` (기본값)

**코드 샘플**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

