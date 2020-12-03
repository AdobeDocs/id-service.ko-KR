---
description: Experience Cloud ID 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.
keywords: ID Service
seo-description: Experience Cloud ID 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.
seo-title: 2019 릴리스 노트
title: 2019 릴리스 노트
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 8ece066545f4ca4a7bd1eca67c8f02dcd2a88369
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 100%

---


# Experience Cloud 릴리스 노트 - 2019 {#release-notes}

Experience Cloud ID 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.

## 버전 4.4.1

ECID Launch 확장에 미디어 분석에 대한 사전 옵트인 승인 확인란을 추가합니다.

**수정 사항**

* ECID 시작 확장 preOptInApprovals 입력 문자열 구문 분석 문제.
* trackingServer를 사용 중인 경우 성능 저하.

## 버전 4.4 {#version-4point4}

**새로운 기능**

[setCustomerIDs에 대한 SHA256 해시 지원](/help/reference/hashing-support.md). ECID(Experience Cloud ID 서비스)는 고객 ID 또는 이메일 주소에서 전달하고 해시된 ID 밖으로 전달할 수 있는 SHA-256 해시 알고리즘을 지원합니다.

**수정 사항, 향상된 기능, 개선 사항**

* `cookieDomain`에 대한 구성을 업데이트했습니다. 이제 ECID 라이브러리는 `initConfig`에서 빈 문자열 `cookieDomain`을 필터링하고 getDomain 메서드에서 반환된 최상위 수준의 쿠키 도메인을 사용합니다.
* `getVisitorValues`에서 `localVisitor`와 관련된 버그를 수정했습니다.
* `getVisitorValue` 메서드에서 반환된 Safari 브라우저의 MCOPTOUT 값에 대한 불일치 문제가 발생한 버그를 수정했습니다.
* 이벤트에서 구독을 해지하기 위해 `optIn.off`를 추가하여 옵트인 라이브러리를 업데이트했습니다.
* `setTimeout`이 일부 고객 사이트에서 CSP(Content Security Policy)를 위반한 setTimeout 함수와 관련된 버그를 수정했습니다.

## 버전 4.3 {#version-4point3}

**ITP 2.1 지원**. 추적 서버가 퍼스트 파티 CNAME에 설정된 경우 새 쿠키(s_ecid)가 ECID 값으로 배치됩니다. ECID 라이브러리는 이 값을 참조하여 7일 이상 ID를 유지합니다. [Safari ITP 환경의 ECID 라이브러리 메서드](/help/reference/ecid-library-methods.md)를 참조하십시오.

**secureCookie 구성에 대한 버그 수정**.

## 버전 4.1

새로운 API 변경 사항별로 `publishDestinations`을(를) 업데이트합니다. 이 업데이트를 통해 페이지의 레퍼러 정보가 ID 동기화 중에 노출될 수 있습니다.

## 버전 4.2

ECID 옵트인 객체를 통해 사용할 수 있는 IAB TCF의 Audience Manager 플러그인에 대한 지원

**수정 사항**

* IAB + OptIn이 신규 고객 확보를 위한 MID를 얻지 못했습니다.
* DTM의 옵트인 dotOptInApply 구성에 대한 버그를 수정했습니다.
* ECID 옵트아웃은 ID 동기화를 사용하지 않습니다.

## 버전 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**옵트인 서비스**&#x200B;입니다. 옵트인은 Experience Cloud 라이브러리에서 방문자 웹 페이지에 쿠키를 생성할 수 있는지 여부를 제어할 수 있는 ECID(Experience Cloud ID)의 확장 프로그램입니다. [Experience Platform Launch](https://docs.adobelaunch.com/)를 사용하면 Analytics, Target, Audience Manager 등을 활성화하여 Experience Cloud 솔루션에 대한 방문자 옵트인 동의 수집을 간소화하거나 동의 관리 시스템에 옵트인할 Experience Cloud 솔루션을 모두 선택할 수 있습니다.

## 버전 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| 항목 | 설명 |
|---|---|
| 문자열을 전달한 경우 `disableIdSyncs` 플래그가 작동하지 않습니다. | 수정되었습니다. `getInstance` 함수의 `disableidSyncs` 매개 변수에 설정된 값이 이제 적용됩니다. |
| 타사 iFrame에서 ECID를 받지 못함 | Safari Mobil의 ECID 및 작동하지 않는 다양한 iFrame의 ECID를 수정했습니다. |
