---
description: Experience Cloud ID 서비스가 타사의 demdex.net 쿠키를 반환하지 않도록 방지하는 선택적 부울 플래그입니다.
keywords: ID 서비스
seo-description: Experience Cloud ID 서비스가 타사의 demdex.net 쿠키를 반환하지 않도록 방지하는 선택적 부울 플래그입니다.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7 ED 5 AA 16-44 CA -4702-878 A -1 A 208 CA 95270
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCookies{#disablethirdpartycookies}를 참조하십시오

Experience Cloud ID 서비스가 타사의 demdex.net 쿠키를 반환하지 않도록 방지하는 선택적 부울 플래그입니다.

>[!NOTE]
>
>이 구성은 v 3.0 2018 년 1 월 18 일 릴리스에서 `idSyncDisable3rdPartySyncing``disableThirdPartyCookies` 이름이 변경되었습니다.

**구문:**`disableThirdPartyCookies: true|false` (기본값은 `false`.) v `VisitorAPI.js` 1.5.3 이상.

이 경우 `disableThirdPartyCookies: true`ID 서비스는 타사, demdex. net 쿠키를 반환하지 않습니다 ( [쿠키 및 Experience Cloud ID 서비스](../../mcvid-introduction/mcvid-cookies.md) 참조). 사이트 방문자의 브라우저에 이 쿠키가 이미 있는 경우 ID 서비스에서 새 Experience Cloud ID(MID)를 만들거나 기존 ID를 반환하는 데 이 쿠키를 사용하지 않습니다. 대신 ID 서비스는 퍼스트 파티 쿠키에 새로운 무작위 MID를 만듭니다. 활성화되면 ID 서비스로 데이터를 수집하고 다른 Experience Cloud 솔루션에서 공유할 수 있습니다.

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

