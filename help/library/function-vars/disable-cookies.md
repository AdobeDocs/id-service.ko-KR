---
description: Experience Cloud Identity 서비스가 타사의 demdex.net 쿠키를 반환하지 않도록 방지하는 선택적 부울 플래그입니다.
keywords: ID 서비스
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 145
ht-degree: 97%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Experience Cloud Identity 서비스가 타사의 demdex.net 쿠키를 반환하지 않도록 방지하는 선택적 부울 플래그입니다.

>[!NOTE]
>
>이 구성은 `idSyncDisable3rdPartySyncing`이며, 2018년 1월 18일 v3.0 릴리스에서 이름이 `disableThirdPartyCookies`로 변경되었습니다.

**구문:** `disableThirdPartyCookies: true|false` (기본값은 `false`임) `VisitorAPI.js` v3.0.0 이상용

`disableThirdPartyCookies: true`에서 ID 서비스는 타사, demdex.net 쿠키([쿠키 및 Experience Cloud Identity 서비스](../../introduction/cookies.md) 참조)를 반환하지 않습니다. 사이트 방문자가 이미 이 쿠키를 브라우저에 가지고 있는 경우 ID 서비스는 새 Experience Cloud ID(MID)를 생성하거나 기존 ID를 반환하는 데 이 쿠키를 사용하지 않습니다. 대신 ID 서비스는 자사 쿠키에 새로운 임의의 MID를 생성합니다. 활성화되면 ID 서비스로 데이터를 수집하고 여러 Experience Cloud 솔루션에서 공유할 수 있습니다.

**코드 샘플**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

