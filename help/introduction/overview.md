---
description: Adobe Experience Cloud에서 Experience Cloud ID 서비스의 역할입니다.
seo-description: Experience Cloud ID 서비스(이전 방문자 ID 서비스 또는 Marketing Cloud ID 서비스)를 사용하면 고객 특성 및 대상과 같은 Experience Cloud 서비스에 대한 공통 ID 프레임워크를 사용할 수 있습니다.
seo-title: Experience Cloud ID 서비스 개요
title: Experience Cloud ID 서비스 개요
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '615'
ht-degree: 100%

---

# Experience Cloud ID 서비스 개요

[!UICONTROL Experience Cloud ID 서비스]를 통해 Experience Cloud ID 서비스의 고객 속성 및 대상과 같은 Experience Cloud 핵심 서비스의 솔루션에 대한 공통된 ID 프레임워크를 사용할 수 있습니다.

>[!NOTE]
>
> ID 서비스에 대한 참조를 약어 또는 이전 이름(예: ECID, Marketing Cloud ID Service(MID) 및 방문자 ID 서비스)으로 볼 수 있습니다. [!UICONTROL Experience Cloud ID 서비스]와 관련 있습니다. 또한 [!UICONTROL Experience Platform ID 서비스]가 표시될 수 있습니다. 명확히 하려면 다음을 확인하십시오.

* [!UICONTROL Experience Platform ID 서비스]: ID를 연결하는 서비스입니다. 사람 기반의 경험 관리를 위한 장치 연결 서비스입니다.
* [!UICONTROL Experience Cloud ID 서비스] (ECID): 사이트 방문자에게 할당된 고유한 영구 ID입니다. Platform ID 서비스에서 사용할 수 있는 특정 엔티티입니다.

조직이 ID 서비스를 구현하면 이 ID를 사용하여 다른 Experience Cloud 솔루션에서 동일한 사이트 방문자와 해당 데이터를 식별할 수 있습니다.

![](assets/ecid-new.png)

또한 ID 서비스는 다른 솔루션별 ID(예: Analytics AID)를 대체할 수 있습니다. 그리고 [고객 ID 및 인증 상태](/help/reference/authenticated-state.md) 기능을 통해 ID 서비스를 사용하면 자신의 고객 ID를 Experience Cloud에 전달할 수 있습니다. 그러나 ID 서비스는 이미 구독한 솔루션에서만 작동한다는 점을 명심하십시오. 등록하지 않은 경우 다른 제품에 대한 액세스를 제공하지 않습니다.

나아가 ID 서비스는 현재 및 미래의 수 많은 Experience Cloud 기능, 개선 사항 및 서비스의 필수 구성 요소입니다. 현재 ID 서비스는 [Analytics](http://www.adobe.com/kr/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/kr/marketing-cloud/data-management-platform.html) 및 [Target](http://www.adobe.com/kr/marketing-cloud/testing-targeting.html)을 지원합니다. Adobe Experience Cloud 장치 Co-op에 참여하려는 경우에도 ID 서비스가 필요합니다. ID 서비스를 구현하지 않았다면 지금이 바로 마이그레이션 전략을 시작할 적기입니다. ID 서비스의 중요성과 역할에 대한 자세한 내용은 [Experience Cloud Identity 서비스가 나의 레이더가 되어야 하는 이유](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)를 참조하십시오.

## 기능 요약

ID 서비스를 요약하자면 다음과 같습니다.

* 프로필과 ID를 연결하는 데 사용할 수 있는 일반 키 또는 ID를 만듭니다.
* 여러 솔루션에서 장치를 고유하게 식별합니다.
* 동일한 도메인에서 추적할 수 있도록 고객 도메인에 자사 쿠키를 설정합니다. 자세한 내용은 [쿠키 및 Experience Cloud ID 서비스](https://docs.adobe.com/content/help/ko-KR/id-service/using/intro/cookies.html)에 대한 문서를 참조하십시오.
* Experience Cloud 고객 및 파트너로부터 별칭 및 ID 매핑을 받습니다.
* Experience Cloud에서 ID 동기화를 관리합니다.
* 광고 기술 에코 시스템에서 다른 타사와 ID 동기화를 지원합니다.

## ID 서비스 요구 사항

솔루션 및 기타 Adobe 코드 라이브러리는 ID 서비스를 사용하기 전에 [특정 요구 사항](/help/reference/requirements.md)을 충족해야 합니다.

* [쿠키 및 Experience Cloud Identity 서비스](cookies.md): 이 ID 서비스는 조직 ID, Experience Cloud AMCV 쿠키 및 demdex 쿠키를 사용하여 사이트 방문자에 대한 고유하고 영구적인 식별자를 만들어 저장합니다. 이러한 쿠키를 사용하면 ID 서비스에서 다른 도메인의 방문자를 추적하고 다른 Experience Cloud 솔루션 간에 데이터 공유를 사용할 수 있습니다.
* [Experience Cloud Identity 서비스에서 ID를 요청하고 설정하는 방법](id-request.md): ID 요청 및 응답 프로세스에 대한 개요입니다. 이러한 예제에서는 개별 사이트, 여러 다른 사이트 및 자체 조직 ID가 있는 다른 Experience Cloud 고객이 관리하는 사이트에 대한 ID 지정을 다룹니다.
* [ID 동기화 및 일치율 이해](match-rates.md): Adobe Media Optimizer 및 ID 서비스를 비롯한 Experience Cloud Identity 서비스의 ID 동기화 프로세스 및 일치율에 대한 개요입니다.
