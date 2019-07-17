---
description: Experience Cloud Identity Service의 표준 및 비표준 구현을 위한 지침과 코드 샘플입니다.
keywords: ID 서비스
seo-description: Experience Cloud Identity Service의 표준 및 비표준 구현을 위한 지침과 코드 샘플입니다.
seo-title: 구현 가이드
title: 구현 가이드
uuid: d41250e2-09f4-4a8b-8ade-54d43e9281c9
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# 구현 방법

Experience Cloud Identity Service의 표준 및 비표준 구현을 위한 지침과 코드 샘플입니다.

>[!IMPORTANT]
>
>[ID 서비스 요구 사항](../reference/requirements.md)을 읽고 이해한 후에 이러한 절차를 시작하십시오.

## 표준 구현 {#section-ea1e5270f2184f85a2e85214a6ac60cb}

표준 구현은 DTM([!DNL Dyanamic Tag Manager])을 사용하여 ID 서비스를 시작하고 다른 ID [!DNL Experience Cloud] 솔루션과 통합할 수 있습니다. ID 서비스를 구현할 때 DTM을 사용하는 것이 좋습니다. 시작하려면 [DTM을 사용한 표준 구현](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)을 참조하십시오.

## 비표준 구현 {#section-2c4f2db1f9704315a7cccab6d2e07113}

이러한 절차 및 코드 샘플은 [!DNL Experience Cloud] ID 서비스를 수동 또는 비표준 방식으로 설정하는 데 도움이 될 수 있습니다. 이러한 구현은 보통 기술적으로 어려운 작업이며 복잡합니다. 매우 드문 엔지니어링 리소스가 필요하거나 Adobe 컨설턴트와 계약된 지원 시간을 소모할 수도 있습니다.

>[!TIP]
>
>또는 DTM을 사용하여 ID 서비스를 구현하는 것이 좋습니다. DTM은 구현 작업 과정을 간소하게 하고 올바른 코드 배치 및 시퀀스를 자동으로 보장합니다. 또한 DTM을 사용하면 ID 서비스 및 이후의 다른 Experience Cloud 솔루션과의 통합에 권장되는 구현 경로가 확보됩니다.

