---
description: Experience Cloud Identity 서비스가 타사의 demdex.net 쿠키를 반환하지 않도록 방지하는 선택적 부울 플래그입니다.
keywords: ID Service
seo-description: Experience Cloud Identity 서비스가 타사의 demdex.net 쿠키를 반환하지 않도록 방지하는 선택적 부울 플래그입니다.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 60%

---


# disableThirdPartyCookies{#disablethirdpartycookies}를 참조하십시오

Experience Cloud Identity 서비스가 타사의 demdex.net 쿠키를 반환하지 않도록 방지하는 선택적 부울 플래그입니다.

>[!NOTE]
>
>이 구성은 `idSyncDisable3rdPartySyncing`이며, 2018년 1월 18일 v3.0 릴리스에서 이름이 `disableThirdPartyCookies`로 변경되었습니다.

**구문:** `disableThirdPartyCookies: true|false` (기본값은 `false`임) `VisitorAPI.js` v3.0.0 이상용

`disableThirdPartyCookies: true`에서 ID 서비스는 타사, demdex.net 쿠키([쿠키 및 Experience Cloud Identity 서비스](../../introduction/cookies.md) 참조)를 반환하지 않습니다. 사이트 방문자의 브라우저에 이미 이 쿠키가 있는 경우 ID 서비스는 이를 사용하여 새 Experience Cloud ID(MID)를 만들거나 기존 ID를 반환하지 않습니다. 대신 ID 서비스는 자사 쿠키에 새로운 임의 MID를 만듭니다. 활성화되면 ID 서비스를 사용하여 데이터를 수집하고 다른 Experience Cloud 솔루션에서 공유할 수 있습니다.

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

