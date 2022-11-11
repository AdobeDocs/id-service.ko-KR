---
description: Experience Cloud ID 서비스의 표준 및 비표준 구현 방법을 비교합니다.
keywords: ID 서비스
title: 구현 방법
exl-id: 0fe40a3c-bdcd-4290-bcd7-25344ff108d6
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 100%

---

# 구현 방법

[!DNL Experience Platform Launch]를 사용하는 표준 [!DNL Experience Cloud ID Service] 구현 방법 또는 비표준 방법을 선택할 수 있습니다.

>[!IMPORTANT]
>
>[ID 서비스 요구 사항](../reference/requirements.md)을 읽고 이해한 후에 이러한 절차를 시작하십시오.

## 표준 구현 {#section-ea1e5270f2184f85a2e85214a6ac60cb}

Adobe는 [[!DNL Experience Platform tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ko)를 사용하여 ID 서비스를 구현할 것을 권장합니다. 이 방법을 사용하면 다른 [!DNL Experience Cloud] 솔루션과 통합하고 구현 워크플로를 간소화하며 자동으로 올바른 코드 배치 및 순서를 확보할 수 있습니다.

## 비표준 구현 {#section-2c4f2db1f9704315a7cccab6d2e07113}

이 안내서의 절차 및 코드 샘플은 [!DNL Experience Cloud] ID 서비스를 수동 또는 비표준 방식으로 설정하는 데 도움이 될 수 있습니다. 이러한 구현은 대개 기술적으로 어렵고 복잡합니다. 부족한 엔지니어링 리소스가 필요하거나 Adobe 컨설턴트와 계약된 지원 시간을 소비할 수 있습니다.
