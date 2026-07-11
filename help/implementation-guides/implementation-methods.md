---
description: 방문자 ID 서비스의 표준 및 비표준 구현 방법을 비교합니다.
keywords: 방문자 ID 서비스
title: 구현 방법
exl-id: 0fe40a3c-bdcd-4290-bcd7-25344ff108d6
TQID: https://experienceleague.adobe.com/VcMKVPqOHJHqwX4CTYHeeQnqrEzwLLJ9xn2-e1vDr-k
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 151
ht-degree: 33%

---

# 구현 방법

태그를 사용하는 표준 방문자 ID 서비스 구현 방법 또는 비표준 방법을 선택할 수 있습니다.

>[!IMPORTANT]
>
>이러한 절차를 시작하기 전에 [방문자 ID 서비스 요구 사항](../reference/requirements.md)을 읽고 이해하십시오.

## 표준 구현 {#section-ea1e5270f2184f85a2e85214a6ac60cb}

Adobe에서는 [태그](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ko-KR)를 사용하여 방문자 ID 서비스를 구현하는 것이 좋습니다. 이 방법을 사용하면 다른 CX 엔터프라이즈 솔루션과 통합하고 구현 워크플로를 간소화하며 자동으로 올바른 코드 배치 및 순서를 확보할 수 있습니다.

## 비표준 구현 {#section-2c4f2db1f9704315a7cccab6d2e07113}

이 안내서의 절차 및 코드 샘플은 방문자 ID 서비스를 수동 또는 비표준 방식으로 설정하는 데 도움이 될 수 있습니다. 이러한 구현은 대개 기술적으로 어렵고 복잡합니다. 부족한 엔지니어링 리소스가 필요하거나 Adobe 컨설턴트와 계약된 지원 시간을 소비할 수 있습니다.

