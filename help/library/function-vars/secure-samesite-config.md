---
description: Google AMP 페이지에서 AMCV 쿠키를 지원하는 데 사용할 수 있는 ECID 내의 구성입니다.
keywords: 방문자 ID 서비스
title: 보안 및 SameSite 구성
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
TQID: https://experienceleague.adobe.com/qT9et54-InwTH7usPnjGN8mdBeMMrqK-qjxGOwqsXBA
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 151
ht-degree: 54%

---

# 보안 및 SameSite 구성

이 구성을 통해 Google AMP 페이지에서 쿠키에 대한 설정을 변경하고 [AMCV 쿠키](../../introduction/cookies.md)를 지원할 수 있습니다.

Adobe 방문자 방문자 ID 서비스는 ECID 쿠키를 브라우저 기본 설정인 `SameSite = Lax`(으)로 설정하는데, Google AMP 페이지와 같은 iframe에서 페이지가 로드되는 경우 액세스할 수 없습니다. ECID 쿠키에 액세스하려면 아래 구성을 사용하여 SameSite 설정을 `SameSite = None`으로 업데이트하십시오.

>[!NOTE]
>
>`SameSite = None`을 적용할 때는 HTTPS 연결을 통해서만 데이터를 전달할 수 있도록 쿠키를 `Secure`로 설정해야 합니다.

**구현**:

태그를 사용하는 경우 [!UICONTROL Experience Cloud ID Service] 태그 확장을 버전 5.1.0으로 업그레이드하고 `secureCookie: true` 및 `sameSiteCookie: none`을(를) 구성하십시오.

태그를 사용하지 않는 경우 최신 Visitor 5.1.0 라이브러리로 업데이트하고 Visitor 인스턴스를 초기화할 때 아래 구성을 따르십시오.

**코드 샘플**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```

