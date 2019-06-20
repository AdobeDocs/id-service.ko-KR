---
description: 서버 예제 구성과 필요한 마이그레이션 단계를 포함합니다.
keywords: ID 서비스
seo-description: 서버 예제 구성과 필요한 마이그레이션 단계를 포함합니다.
seo-title: Experience Cloud ID 서비스 마이그레이션 시나리오
title: Experience Cloud ID 서비스 마이그레이션 시나리오
uuid: 9 E 229045-6508-48 C 4-AE 39-9537 B 4941853
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Experience Cloud ID 서비스 마이그레이션 시나리오 {#experience-cloud-id-service-migration-scenarios}

서버 예제 구성과 필요한 마이그레이션 단계를 포함합니다.

## 단일 웹 속성 {#section-6ccfea84628d46c99507cb124e7f5445}

* **고객**: 예제 Company Inc.
* **Experience Cloud 사용 여부**: 아니요
* **웹 속성**: example.com
* **데이터 수집 서버**: metrics.example.com, smetrics.example.com
* **Analytics JavaScript 파일**: 모든 사이트 페이지에 대한 단일 파일

먼저 이 고객이 Experience Cloud를 사용하도록 설정해야 합니다( [요구 사항](../../reference/requirements.md)). 또한 단일 JavaScript 파일이 있으므로 이 고객에게는 유예 기간이 필요하지 않습니다. 이 고객은 또한 방문자 마이그레이션을 설정한 다음 데이터 수집 CNAME이 필요하지 않으므로 이 CNAME 외부로 마이그레이션합니다.

## 여러 JavaScript 파일, 하드 코딩된 이미지 태그 {#section-a665f6ee202940449198e4e7a5dcac54}

* **고객**: 또 다른 예제 Company Inc.
* **Experience Cloud 사용**: 예
* **웹 속성**: anotherexample.com
* **데이터 수집 서버**: anotherexampleco.112.2o7.net
* **Analytics JavaScript 파일**: 여러 JavaScript 파일. 하나는 기본 사이트를 위한 파일이고 다른 파일은 별도의 CMS에 유지 관리되는 지원 섹션을 위한 파일입니다.
* **기타 데이터 수집 방법**: 한 사이트 섹션의 하드 코딩된 이미지 태그

먼저 이 고객이 해당 Adobe Experience Cloud 조직 ID를 찾아야 합니다( [요구 사항](../../reference/requirements.md)). 다음으로, 여러 JavaScript 파일을 사용하고 있으므로 마이그레이션 유예 기간을 구성해야 합니다. This customer will also set up visitor migration and then migrate from `*.2o7.net` to `*.sc.omtrdc.net`.

이 고객이 [!DNL Experience Cloud] ID 서비스 롤아웃을 준비하는 동안 최신 Analytics JavaScript 코드로 업데이트하면 대신 JavaScript를 사용하도록 하드 코딩된 이미지 태그도 모두 업데이트됩니다.

## 여러 웹 속성, 여러 JavaScript 파일 및 Flash 기반 비디오 플레이어 {#section-34647995ff3740b999fdee22d885e515}

* **고객**: 적절한 고객 LLC
* **Experience Cloud 사용**: 예
* **웹 속성**: mymainsite.com, myothersiteA.com, myothersiteB.com
* **데이터 수집 서버**: metrics.mymainsite.com, smetrics.mymainsite.com
* **Analytics JavaScript 파일**: 여러 JavaScript 파일. 웹 속성별로 파일이 하나씩 있습니다.
* **기타 데이터 수집 방법**: Flash 기반 비디오 플레이어

먼저 이 고객이 해당 Adobe Experience Cloud 조직 ID를 찾아야 합니다( [요구 사항](../../reference/requirements.md)). 다음으로, 여러 JavaScript 파일을 사용하고 있으므로 마이그레이션 유예 기간을 구성해야 합니다. 이 고객은 기본 도메인과 하위 도메인 간 방문자를 추적하므로 방문자 ID 서비스에서 해당 데이터 수집 CNAME을 계속 사용하게 됩니다.

이 고객이 [!DNL Experience Cloud] ID 서비스 롤아웃을 준비하는 동안 최신 Analytics JavaScript 코드로 업데이트하면 Flash 기반 비디오 플레이어도 최신 버전의 AppMeasurement for Flash로 업데이트됩니다.
