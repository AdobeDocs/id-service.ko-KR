---
description: ID 서비스에서 Analytics 사용과 관련된 기능 및 문제에 대한 FAQ입니다.
keywords: ID 서비스
seo-description: ID 서비스에서 Analytics 사용과 관련된 기능 및 문제에 대한 FAQ입니다.
seo-title: Analytics 및 ID 서비스 FAQ
title: Analytics 및 ID 서비스 FAQ
uuid: 35 ED 79 A 9-ECCC -4 B 54-8451-606 F 091 C 73 B 7
translation-type: tm+mt
source-git-commit: 4dc668afd37cd1d6f9104adb1b102f1dd4c5746e

---


# Analytics 및 ID 서비스 FAQ{#analytics-and-id-service-faqs}

ID 서비스에서 Analytics 사용과 관련된 기능 및 문제에 대한 FAQ입니다.

## 추적 서버 {#section-9a2ad7842e364c869e1650480d17f8ef}

**내 추적 서버 정보를 어떻게 찾을 수 있습니까?**

올바르게 구성된 모든 AppMeasurement 코드에는 추적 서버 정보가 포함되어 있습니다.

하지만 고객이 Analytics AppMeasurement 파일을 별도의 파일로 나눌 수 있는 경우도 있습니다. 예를 들어 고객이 구성 변수를 한 파일에 지정하고, 플러그인에 두 번째 파일을 사용한 다음, AppMeasurement 코드를 세 번째 파일에 지정할 수 있습니다. 이 방법은 권장하지 않습니다.

추적 서버 정보를 찾을 수 없는 경우 Analytics 인스턴스가 제대로 구성되지 않을 수 있습니다. 추적 서버 정보를 찾을 수 없는 경우 [고객 지원 센터](https://helpx.adobe.com/marketing-cloud/contact-support.html)에 문의하십시오.

**ID 서비스를 사용하고 있는데 추적 서버를 변경하면 어떻게 됩니까?**

이미 ID 서비스에서 식별한 사용자에게는 아무런 변화가 없습니다. ID 서비스로 마이그레이션되지 않았고 아직 Analytics 쿠키로 식별되는 기존 방문자는 삭제될 수 있습니다. 영향을 받는 사용자 수는 ID 서비스가 활성화된 기간에 따라 다릅니다. 예를 들어 ID 서비스가 1주 동안 활성화되었던 구현에는 6개월 동안 활성화되었던 구현보다 기존 사용자가 더 많이 있을 수 있는데, 이는 사이트를 재방문하는 사용자는 마이그레이션했을 수 있기 때문입니다.

## 구현 및 구성 {#section-6028f55d5b514ae6a631c6a79f42fb89}

**도메인 간에 방문자를 추적하기 위해 CNAME을 설정해야 합니까?**

고객이 다른 도메인을 방문하기 전에 식별될 수 있는 기본 시작 사이트가 있는 경우 CNAME은 서드 파티 쿠키를 수락하지 않는 브라우저(예: Safari)에서 도메인 간 추적을 활성화할 수 있습니다.

타사 쿠키를 허용하는 브라우저에서는 방문자 ID에 대한 검색 요청 중에 [demdex.net 도메인](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)에서 쿠키가 설정됩니다. 이 쿠키를 사용하면 ID 서비스에서는 동일한 조직 ID를 사용하여 구성된 모든 도메인에 동일한 Experience Cloud 방문자 ID를 반환할 수 있습니다. 타사 쿠키를 거부하는 브라우저에서는 새 Experience Cloud 방문자 ID가 각 도메인에 대해 지정됩니다.

CNAME이 구성되어 있어도 기본 시작 사이트를 먼저 방문하지 않으면 방문자는 보조 사이트 및 서드 파티 쿠키를 수락하지 않는 브라우저의 기본 사이트에서 다르게 식별됩니다.

**Analytics 요청에 Experience Cloud ID(MID) 매개 변수가 없는 이유는 무엇입니까?**

ID 서비스가 정보를 올바르게 반환하지만 `MID` 매개 변수가 표시되지 않으면 지원되는 버전의 AppMeasurement로 업그레이드했는지 확인하십시오.

**내 사이트에서 ID 서비스와 H 코드 및 AppMeasurement for JavaScript를 함께 사용할 수 있습니까?**

예. 단, 두 파일이 동일한 VisitorAPI.js 파일을 참조해야 합니다. 사이트 내에서 H 코드와 AppMeasurement for JavaScript 조합을 사용할 수 있습니다.

하지만 H 코드는 visitorAPI.js 코드 버전 1.6 이상에서 지원되지 않습니다. visitorAPI.js v 1.6 이상으로 업그레이드하려는 경우 H 코드를 더 이상 사용할 수 없습니다.

**유예 기간이란 무엇이며, 어떻게 구성합니까?**

ID [서비스 유예 기간을](../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) 확인하고 [고객 지원 센터에](https://helpx.adobe.com/marketing-cloud/contact-support.html)문의하십시오.

**ID 서비스를 사용하기 위해 RDC(실시간 데이터 수집)로 마이그레이션해야 하는 이유는 무엇입니까?**

RDC는 전체적인 성능상의 이점을 제공하며 Adobe의 최신 전역 네트워크를 활용하는 향후 기능을 위해 구현을 준비할 수 있다는 차원에서도 필요합니다. [Analytics 요구 사항: RDC(지역 데이터 수집)](../mcvid-reference/mcvid-requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)를 참조하십시오.

## 보고 {#section-123cd55a32e54a45a23beb140becfa8f}

**ID 서비스에서 Analytics를 사용할 때 가능한 불일치의 원인은 무엇입니까?**

ID 서비스 사용 시 나타나는 불일치의 가능한 원인은 다음과 같습니다.

* 이전 s_vi 쿠키를 계속 사용했습니다. 이로 인해 데이터 수집 불일치 문제가 발생합니다.
* 설문 조사에서 팝업으로 이동할 때 방문자를 이중으로 계산합니다.

## 쿠키 {#section-b7d5384fbedd47b09e1030211c39a3d1}

**ID 서비스에서 AMCV 쿠키를 설정할 수 없는 경우 Analytics가 어떻게 됩니까?**

새 방문자에 대한 Analytics 데이터에 영향을 주는 세 가지 잠재적 시나리오가 있습니다.

1. AMCV 쿠키가 성공적으로 설정되기 전에(30초 시간 제한 창 내에 있음) 최종 사용자가 페이지에서 나갑니다.

   페이지가 로드되기 전에 방문자가 페이지에서 나가면 Analytics 히트가 전송되지 않습니다. Analytics에서 이 시나리오의 데이터를 수신하지 않으며 해당 데이터가 페이지의 조기 종료로 손실되었는지 고려합니다. 외딴 지역을 포함한 테스트를 기반으로 했을 때 이 시나리오는 평균적으로 1% 미만의 트래픽을 나타낸다는 것을 발견했습니다. 이 시나리오는 MCID 서비스가 없어도 때때로 발생한다는 점을 주목해야 합니다. 이는 페이지 하단에 Analytics 데이터 수집 코드가 포함된 아티팩트입니다.

1. 느린 연결 또는 브라우저 &quot;회전&quot;으로 인해 30초 시간 제한 창 내에서 ID 서비스 또는 Analytics ID가 최종 사용자에게 지정되지 않습니다.

   ID 서비스와 Analytics ID가 모두 설정되지 않고 방문자에게 클라이언트측 ID가 지정됩니다. 이렇게 하면 Analytics 데이터를 캡처할 수 있지만 이후 페이지에서 Analytics ID가 설정되면 방문자의 프로필이 중단됩니다. 또한 클라이언트측 ID가 Audience Manager 또는 Analytics에 저장된 기존 방문자 프로필과 일치하지 않게 됩니다. 두 개의 별도 도메인이 동일한 보고서 세트에 전송되는 경우 이 클라이언트측 ID는 Analytics에 두 개의 다른 방문자로 표시됩니다.

1. 30초 시간 제한 창 내에서 ID 서비스 ID가 최종 사용자에게 지정되지 않지만, 표준 Analytics 추적 ID가 지정되고 유예 기간이 활성화되지 않습니다.

   시나리오 3은 클라이언트측 기반 ID가 사용되므로 시나리오 2와 결과가 동일합니다.

>[!TIP]
>
>기본 설정으로 Visitorapi. js 및 appmeasurement. js에 대한 최신 업데이트를 사용하면 위의 세 가지 불가능한 시나리오에서 심각하거나 눈에 띄는 영향을 방지할 수 있습니다.

>[!MORE_ like_ this]
>
>* [고객 지원](https://helpx.adobe.com/marketing-cloud/contact-support.html)에 문의하십시오
