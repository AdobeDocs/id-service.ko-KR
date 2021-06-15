---
description: Experience Cloud Identity 서비스가 타사의 demdex.net 쿠키를 반환하지 않도록 방지하는 선택적 부울 플래그입니다.
keywords: ID 서비스
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '139'
ht-degree: 100%

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
