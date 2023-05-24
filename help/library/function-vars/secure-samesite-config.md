---
description: Google AMP 페이지에서 AMCV 쿠키를 지원하는 데 사용할 수 있는 ECID 내의 구성입니다.
keywords: ID 서비스
title: 보안 및 SameSite 구성
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 100%

---

# 보안 및 SameSite 구성

이 구성을 통해 Google AMP 페이지에서 쿠키에 대한 설정을 변경하고 [AMCV 쿠키](../../introduction/cookies.md)를 지원할 수 있습니다.

Adobe 방문자 ID 서비스는 ECID 쿠키를 브라우저 기본 설정인 `SameSite = Lax`로 설정하는데, Google AMP 페이지와 같은 iframe에서 페이지가 로드되는 경우 액세스할 수 없습니다. ECID 쿠키에 액세스하려면 아래 구성을 사용하여 SameSite 설정을 `SameSite = None`으로 업데이트하십시오.

>[!NOTE]
>
>`SameSite = None`을 적용할 때는 HTTPS 연결을 통해서만 데이터를 전달할 수 있도록 쿠키를 `Secure`로 설정해야 합니다.

**구현**:

Adobe Experience Platform Launch를 사용 중인 경우, Experience Cloud ID 확장 기능을 버전 5.1.0으로 업그레이드하고 `secureCookie: true` 및 `sameSiteCookie: none`을 구성하십시오.

Experience Platform Launch를 사용하지 않는다면 최신 Visitor 5.1.0 라이브러리로 업데이트하고 Visitor 인스턴스를 초기화할 때 아래 구성을 따르십시오.

**코드 샘플**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
