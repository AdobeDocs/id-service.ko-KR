---
description: Adobe Experience Cloud에서 Experience Cloud ID 서비스의 역할입니다.
title: Experience Cloud ID 서비스 개요
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 36%

---

# Experience Cloud ID 서비스 개요

Experience Cloud ID 서비스를 통해 Experience Cloud 응용 프로그램 서비스의 공통 ID 프레임워크를 사용할 수 있습니다. Experience Cloud ID 서비스를 사용하여 [Experience Cloud ID(ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html).

ECID는 Adobe Experience Platform 및 Experience Cloud 애플리케이션에서 방문자 동작을 추적하고 각 장치에 여러 세션 간에 유지할 수 있는 고유한 식별자가 있도록 하는 공유 ID 네임스페이스입니다.

>[!TIP]
>
>Experience Cloud Identity 서비스, Experience Platform Identity 서비스 및 ECID는 3입니다 **different** 엔티티.

Experience Cloud Identity 서비스는 다른 애플리케이션별 ID를 대체하고 [고객 ID 및 인증 상태](/help/reference/authenticated-state.md) 고유한 고객 ID를 Experience Cloud에 전달할 수 있는 기능입니다.

>[!NOTE]
>
>Experience Cloud ID 서비스는 사용자가 구독한 Experience Cloud 응용 프로그램 서비스에서만 작동하며 구독하지 않은 경우 다른 응용 프로그램 서비스에 대한 액세스 권한을 제공하지 않습니다.

Experience Cloud ID 서비스는 다음 응용 프로그램을 지원합니다.

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

나아가 ID 서비스는 현재 및 미래의 수 많은 Experience Cloud 기능, 개선 사항 및 서비스의 필수 구성 요소입니다. 현재 ID 서비스는 [Analytics](http://www.adobe.com/kr/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/kr/marketing-cloud/data-management-platform.html) 및 [Target](http://www.adobe.com/kr/marketing-cloud/testing-targeting.html)을 지원합니다. ID 서비스를 구현하지 않았다면 지금이 바로 마이그레이션 전략을 시작할 적기입니다.

## 기능 요약

요약하면 Experience Cloud Identity 서비스는 다음과 같은 이점을 제공합니다.

* 여러 애플리케이션에서 장치에서 방문자를 고유하게 식별합니다.
* 동일한 도메인에서 추적할 수 있도록 고객 도메인에 자사 쿠키를 설정합니다. 자세한 내용은 [쿠키 및 Experience Cloud ID 서비스](./cookies.md)에 대한 문서를 참조하십시오.
* Experience Cloud 고객 및 파트너로부터 별칭 및 ID 매핑을 받습니다.
* Experience Cloud에서 ID 동기화를 관리합니다.
* 광고 기술 에코 시스템에서 다른 서드파티와 ID 동기화를 지원합니다.

## Experience Cloud ID 서비스 요구 사항

솔루션 및 기타 Adobe 코드 라이브러리가 충족되어야 합니다 [특정 요구 사항](/help/reference/requirements.md) id 서비스를 사용하려면 먼저 하십시오.

* [쿠키 및 Experience Cloud Identity 서비스](cookies.md): Experience Cloud Identity 서비스 Identity 서비스는 조직 ID, Experience Cloud AMCV 쿠키 및 demdex 쿠키를 사용하여 사이트 방문자에 대한 고유하고 영구적인 식별자를 만들어 저장합니다. 이러한 쿠키를 사용하면 Identity 서비스에서 다른 도메인의 방문자를 추적하고 다른 Experience Cloud 솔루션 간에 데이터 공유를 사용할 수 있습니다.
* [Experience Cloud ID 서비스에서 ID를 요청하고 설정하는 방법](id-request.md): ID 요청 및 응답 프로세스에 대한 개요입니다. 이러한 예제에서는 개별 사이트, 여러 다른 사이트 및 자체 조직 ID가 있는 다른 Experience Cloud 고객이 관리하는 사이트에 대한 ID 지정을 다룹니다.
* [ID 동기화 및 일치율 이해하기](match-rates.md): Adobe Media Optimizer 및 Identity 서비스를 비롯한 Experience Cloud Identity 서비스의 ID 동기화 프로세스 및 일치율에 대한 개요입니다.
