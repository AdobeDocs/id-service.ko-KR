---
description: Google AMP 페이지에서 AMCV 쿠키를 지원하는 데 사용할 수 있는 ECID 내의 구성.
keywords: ID 서비스
seo-description: Google AMP 페이지에서 AMCV 쿠키를 지원하는 데 사용할 수 있는 ECID 내의 구성.
seo-title: 보안 및 동일 사이트 구성
title: 보안 및 동일 사이트 구성
translation-type: tm+mt
source-git-commit: 702d20f3989f7749fb173496765d94c3a5af46dc
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 2%

---


# 보안 및 동일 사이트 구성

이 구성을 통해 Google AMP 페이지에서 쿠키 설정을 변경하고 [AMCV 쿠키](../../introduction/cookies.md)를 지원할 수 있습니다.

Adobe 방문자 ID 서비스는 ECID 쿠키를 브라우저 기본 설정 `SameSite = Lax`으로 설정합니다. 이 설정은 페이지가 Google AMP 페이지와 같은 iframe에 로드되면 액세스할 수 없습니다. ECID 쿠키에 액세스하려면 아래 구성을 사용하여 SameSite 설정을 `SameSite = None`으로 업데이트하십시오.

>[!NOTE]
>
>`SameSite = None`을(를) 적용할 때 HTTPS 연결을 통해서만 데이터를 전달할 수 있도록 쿠키를 `Secure`으로 설정해야 합니다.

**구현**:

Adobe Experience Platform Launch을 사용하는 경우 Experience Cloud ID 확장을 버전 5.1.0으로 업그레이드하고 `secureCookie: true` 및 `sameSiteCookie: none`을 구성합니다.

Experience Platform Launch을 사용하지 않는 경우 최신 방문자 5.1.0 라이브러리로 업데이트한 후 방문자 인스턴스를 초기화하는 동안 아래 구성을 따르십시오.

**코드 샘플**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
