---
description: Adobe Experience Cloud에서 Experience Cloud Identity Service의 역할입니다.
title: Experience Cloud Identity Service 개요
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 100%

---

# Experience Cloud Identity Service 개요

Experience Cloud Identity Service를 통해 Experience Cloud 애플리케이션 서비스에 대해 공통된 ID 프레임워크를 사용할 수 있습니다. Experience Cloud Identity Service를 사용하여 [Experience Cloud ID(ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html)를 설정할 수 있습니다.

ECID는 방문자 행동을 추적하고 각 디바이스에 여러 세션에서 지속될 수 있는 고유 식별자가 있는지 확인하기 위해 Adobe Experience Platform 및 Experience Cloud 애플리케이션에서 사용되는 공유 ID 네임스페이스입니다.

>[!TIP]
>
>Experience Cloud Identity Service, Experience Platform Identity Service 및 ECID는 세 가지 **서로 다른** 엔티티입니다.

Experience Cloud Identity Service는 다양한 애플리케이션별 ID를 대체하고 [고객 ID 및 인증 상태](/help/reference/authenticated-state.md) 기능을 사용하여 고객 ID를 Experience Cloud에 전달할 수 있도록 해 줍니다.

>[!NOTE]
>
>Experience Cloud Identity Service는 현재 구독 중인 Experience Cloud 애플리케이션 서비스에서만 작동하며, 구독하지 않는 경우 다른 애플리케이션 서비스에 대한 액세스를 제공하지 않습니다.

Experience Cloud Identity Service는 다음과 같은 애플리케이션을 지원합니다.

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

나아가 ID 서비스는 현재 및 미래의 수 많은 Experience Cloud 기능, 개선 사항 및 서비스의 필수 구성 요소입니다. 현재 ID 서비스는 [Analytics](http://www.adobe.com/kr/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/kr/marketing-cloud/data-management-platform.html) 및 [Target](http://www.adobe.com/kr/marketing-cloud/testing-targeting.html)을 지원합니다. ID 서비스를 구현하지 않았다면 지금이 바로 마이그레이션 전략을 시작할 적기입니다.

## 기능 요약

요약하자면, Experience Cloud Identity Service는 다음과 같은 기능을 제공합니다.

* 여러 애플리케이션에 걸쳐 디바이스에서 방문자를 고유하게 식별합니다.
* 동일한 도메인에서 추적할 수 있도록 고객 도메인에 자사 쿠키를 설정합니다. 자세한 내용은 [쿠키 및 Experience Cloud ID 서비스](./cookies.md)에 대한 문서를 참조하십시오.
* Experience Cloud 고객 및 파트너로부터 별칭 및 ID 매핑을 받습니다.
* Experience Cloud에서 ID 동기화를 관리합니다.
* 광고 기술 에코 시스템에서 다른 서드파티와 ID 동기화를 지원합니다.

## Experience Cloud Identity Service 요구 사항

Identity Service를 사용하려면 솔루션 및 기타 Adobe 코드 라이브러리가 [특정 요구 사항](/help/reference/requirements.md)을 충족해야 합니다.

* [쿠키 및 Experience Cloud Identity Service](cookies.md): Experience Cloud Identity Service Identity Service는 조직 ID, Experience Cloud AMCV 쿠키 및 demdex 쿠키를 사용하여 사이트 방문자에 대한 고유하고 영구적인 식별자를 만들어 저장합니다. 이들 쿠키를 사용하면 Identity Service에서 다른 도메인의 방문자를 추적하고 서로 다른 Experience Cloud 솔루션 간 데이터 공유 기능을 사용할 수 있습니다.
* [Experience Cloud ID 서비스에서 ID를 요청하고 설정하는 방법](id-request.md): ID 요청 및 응답 프로세스에 대한 개요입니다. 이러한 예제에서는 개별 사이트, 여러 다른 사이트 및 자체 조직 ID가 있는 다른 Experience Cloud 고객이 관리하는 사이트에 대한 ID 지정을 다룹니다.
* [ID 동기화 및 일치율 이해](match-rates.md): Adobe Media Optimizer 및 Identity Service를 비롯한 Experience Cloud Identity Service의 ID 동기화 프로세스 및 일치율에 대한 개요입니다.
