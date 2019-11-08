---
description: Experience Cloud Identity Service의 표준 및 비표준 구현 방법
keywords: ID 서비스
seo-description: Experience Cloud Identity Service의 표준 및 비표준 구현 방법
seo-title: 구현 방법
title: 구현 방법
uuid: d41250e2-09f4-4a8b-8ade-54d43e9281c9
translation-type: tm+mt
source-git-commit: 6c1ff82104bc021d047bb066829328d5fd9eedbf

---


# 구현 방법

표준 [!DNL Experience Cloud ID Service] 구현 방법이나 비표준 방법을 사용하여 [!DNL Experience Platform Launch] 선택할 수 있습니다.

>[!IMPORTANT]
>
>[ID 서비스 요구 사항](../reference/requirements.md)을 읽고 이해한 후에 이러한 절차를 시작하십시오.

## 표준 구현 {#section-ea1e5270f2184f85a2e85214a6ac60cb}

ID 서비스를 구현하는 [!DNL Experience Platform Launch](https://docs.adobe.com/content/help/en/launch/using/implement/solutions/idservice-save.html) 데 사용하는 것이 좋습니다. 이 방법은 다른 [!DNL Experience Cloud] 솔루션과의 통합을 보장하고 구현 워크플로우를 간소화하며 올바른 코드 배치 및 순서를 자동으로 보장합니다.

## 비표준 구현 {#section-2c4f2db1f9704315a7cccab6d2e07113}

The procedures and code samples in this guide can help you set up the [!DNL Experience Cloud] ID service in a manual, or non-standard manner. 이러한 구현은 보통 기술적으로 어려운 작업이며 복잡합니다. 매우 드문 엔지니어링 리소스가 필요하거나 Adobe 컨설턴트와 계약된 지원 시간을 소모할 수도 있습니다.
