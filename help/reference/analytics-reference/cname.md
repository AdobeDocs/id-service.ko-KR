---
description: '고객이 다른 도메인을 방문하기 전에 식별될 수 있는 기본 시작 사이트가 있는 경우 CNAME은 서드 파티 쿠키를 수락하지 않는 브라우저(예: Safari)에서 도메인 간 추적을 활성화할 수 있습니다.'
keywords: 작업 순서;ID 서비스
seo-description: '고객이 다른 도메인을 방문하기 전에 식별될 수 있는 기본 시작 사이트가 있는 경우 CNAME은 서드 파티 쿠키를 수락하지 않는 브라우저(예: Safari)에서 도메인 간 추적을 활성화할 수 있습니다.'
seo-title: CNAME 구현 개요
title: CNAME 구현 개요
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: ebeca9e285af71872c05d58ba252ca65bde24f3d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 28%

---


# CNAME 구현 개요{#cname-implementation-overview}

CNAME 구현을 통해 Adobe에서 사용하는 수집 도메인을 사용자 지정하여 자체 도메인과 일치하도록 할 수 있습니다. 이렇게 하면 Adobe이 JavaScript를 사용하여 클라이언트 측 대신 서버측에서 퍼스트 파티 쿠키를 설정할 수 있습니다. 이전에는 이러한 서버측 자사 쿠키는 Apple의 ITP(Intelligent Tracking Prevention) 정책에 따라 제한을 받지 않았습니다. 그러나 2020년 11월, [!DNL Apple]은 CNAME을 통해 설정된 쿠키에도 이러한 제한이 적용되도록 정책을 업데이트했습니다. 현재, CNAME을 통해 서버측에 설정된 쿠키와 Javascript를 통해 클라이언트측에 설정된 쿠키는 모두 ITP에서 7일 또는 24시간 만료로 제한됩니다. ITP 정책에 대한 자세한 내용은 추적 방지](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)에 대한 이 [!DNL Apple] 문서 [를 참조하십시오.

CNAME 구현은 쿠키 라이프타임 측면에서 어떠한 이점이 없지만 광고 차단기 및 덜 일반적인 브라우저와 같이 데이터를 추적기로 분류하는 도메인으로 전송하지 못하도록 하는 다른 이점이 있을 수 있습니다. 이러한 경우, CNAME을 사용하면 이러한 도구를 사용하는 사용자가 데이터 수집을 중단하지 못하도록 할 수 있습니다.