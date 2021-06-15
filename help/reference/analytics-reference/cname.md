---
description: '고객이 다른 도메인을 방문하기 전에 식별될 수 있는 기본 시작 사이트가 있는 경우 CNAME은 서드파티 쿠키를 수락하지 않는 브라우저(예: Safari)에서 도메인 간 추적을 활성화할 수 있습니다.'
keywords: 작업 순서;ID 서비스
title: CNAME 구현 개요
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '221'
ht-degree: 100%

---


# CNAME 구현 개요{#cname-implementation-overview}

CNAME 구현을 통해 내 도메인과 일치시킬 수 있도록 Adobe가 사용하는 컬렉션 도메인을 맞춤화할 수 있습니다. 이를 통해 Adobe는 JavaScript를 사용하는 클라이언트측 대신 서버측에서 자사 쿠키를 설정할 수 있습니다. 과거에는 이들 서버측 자사 쿠키가 Apple의 ITP(Intelligent Tracking Prevention) 정책에 따라 부과되는 제한을 받지 않았습니다. 그러나 2020년 11월에 이루어진 [!DNL Apple] 업데이트를 통해 이러한 제한 사항이 CNAME을 통해 설정된 쿠키에도 적용되기 시작했습니다. 현재는 CNAME을 통해 서버측에서 설정된 쿠키와 JavaScript를 통해 클라이언트측에서 설정된 쿠키 모두 ITP에서 7일 또는 24시간 만료로 제한됩니다. ITP 정책에 대한 자세한 내용은 이 [!DNL Apple] 문서 [Tracking Prevention](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)을 참조하십시오.

CNAME 구현은 쿠키 수명 측면에서는 어떠한 이점도 제공하지 않지만, 추적기로 분류되는 도메인으로 데이터가 전송되는 것을 방지하는 광고 차단기 및 보다 덜 보편적인 브라우저와 같은 다른 이점이 있을 수 있습니다. 이러한 경우 CNAME을 사용하면 이들 도구를 사용하는 사용자의 데이터 수집이 중단되는 것을 방지할 수 있습니다.