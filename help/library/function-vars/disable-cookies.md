---
description: Experience Platform Identity Service가 타사 demdex. net 쿠키를 반환하지 않는 옵션, 부울 플래그.
keywords: ID 서비스
seo-description: Experience Platform Identity Service가 타사 demdex. net 쿠키를 반환하지 않는 옵션, 부울 플래그.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# disableThirdPartyCookies{#disablethirdpartycookies}를 참조하십시오

Experience Platform Identity Service가 타사 demdex. net 쿠키를 반환하지 않는 옵션, 부울 플래그.

>[!NOTE]
>
>이 구성은 `idSyncDisable3rdPartySyncing`이며, 2018년 1월 18일 v3.0 릴리스에서 이름이 `disableThirdPartyCookies`로 변경되었습니다.

**구문:** `disableThirdPartyCookies: true|false` (기본값은 `false`임) `VisitorAPI.js` v1.5.3 이상용

When `disableThirdPartyCookies: true`, the ID service does not return the third-party, demdex.net cookie (see [Cookies and the Experience Platform Identity Service](../../introduction/cookies.md) ). 사이트 방문자의 브라우저에 이 쿠키가 이미 있는 경우 ID 서비스에서 새 Experience Cloud ID(MID)를 만들거나 기존 ID를 반환하는 데 이 쿠키를 사용하지 않습니다. 대신 ID 서비스는 퍼스트 파티 쿠키에 새로운 무작위 MID를 만듭니다. 활성화되면 ID 서비스로 데이터를 수집하고 다른 Experience Cloud 솔루션에서 공유할 수 있습니다.

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

