---
description: '고객이 다른 도메인을 방문하기 전에 식별될 수 있는 기본 시작 사이트가 있는 경우 CNAME은 서드파티 쿠키를 수락하지 않는 브라우저(예: Safari)에서 도메인 간 추적을 활성화할 수 있습니다.'
keywords: 작업 순서;ID 서비스
title: CNAME 구현 개요
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: 61f9f1888430ff0fdbb90a8cf6561bf23d204a45
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# CNAME 구현 개요{#cname-implementation-overview}

CNAME 구현을 통해 내 도메인과 일치시킬 수 있도록 Adobe가 사용하는 컬렉션 도메인을 맞춤화할 수 있습니다. 이러한 도메인을 자사 수집 도메인이라고도 합니다. 이러한 구현을 통해 Adobe은 JavaScript를 사용하여 클라이언트 측 대신 서버 측에서 자사 쿠키를 설정할 수 있습니다. 과거에는 이들 서버측 자사 쿠키가 Apple의 ITP(Intelligent Tracking Prevention) 정책에 따라 부과되는 제한을 받지 않았습니다. 그러나 2020년 11월에 이루어진 [!DNL Apple] 업데이트를 통해 이러한 제한 사항이 CNAME을 통해 설정된 쿠키에도 적용되기 시작했습니다. 현재, CNAME을 통해 서버 측에 설정된 쿠키와 Javascript를 통해 클라이언트 측에 설정된 쿠키는 모두 ITP에서 7일 또는 24시간 만료로 제한됩니다. ITP 정책에 대한 자세한 내용은 이 [!DNL Apple] 문서 [Tracking Prevention](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)을 참조하십시오.

CNAME 구현은 쿠키 라이프타임 측면에서는 이점이 없지만 다음과 같은 몇 가지 다른 이점이 있을 수 있습니다. 이러한 이점은 광고 차단기와 덜 일반적인 브라우저로 데이터가 추적기로 분류되는 도메인으로 전송되지 않도록 하는 것입니다. 이러한 경우 CNAME을 사용하면 이러한 도구를 사용하는 사용자에게 데이터 수집이 중단되지 않을 수 있습니다.

또한 CNAME 구현을 통해 다음을 지정할 수 있습니다 **[!UICONTROL 사용자 지정 RDC 유형 선택]** 는 사용자의 히트가 처음에 라우팅되는 위치를 제어합니다. 대부분의 고객은 사용자 지정 RDC 유형을 사용하지 않습니다.
