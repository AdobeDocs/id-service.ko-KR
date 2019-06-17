---
description: AMCV 쿠키에 "Secure" 속성을 추가하는 선택적 부울 플래그입니다.
keywords: ID 서비스
seo-description: AMCV 쿠키에 "Secure" 속성을 추가하는 선택적 부울 플래그입니다.
seo-title: secureCookie
title: secureCookie
uuid: 995 D 19 F 6-9 C 9 D -4493-9 C 9 C -545 B 0 B 5696 B 0
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# secureCookie{#securecookie}

AMCV 쿠키에 &quot;Secure&quot; 속성을 추가하는 선택적 부울 플래그입니다.

이 구성 속성은 `visitorAPI` 버전 3.3.0에서 사용 가능합니다.

>[!NOTE]
>
>`SecureCookie` 구성은 비보안 도메인에서 작동하지 않으며 비보안 프로토콜을 사용하는 방문에 대한 MID 값을 받지 않을 수 있습니다. 모든 페이지 및 하위 도메인에서 항상 보안 프로토콜을 사용 중인 경우에만 `secureCookie` 구성을 `true`로 설정해야 합니다.

**구문:**`secureCookie: true | false` (기본값)

**코드 샘플**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```
