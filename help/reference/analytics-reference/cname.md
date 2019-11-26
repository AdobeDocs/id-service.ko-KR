---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: 데이터 수집 CNAME 및 도메인 간 추적
title: 데이터 수집 CNAME 및 도메인 간 추적
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 989b5f537848a7506a96e2eac17409f8b0307217

---


# 데이터 수집 및 ID{#data-collection-and-identity}

Analytics에서는 방문자를 ID로 지정하는 데 사용할 수 있는 세 가지 방법이 있습니다.

- 방문자 ID [서비스 사용](https://docs.adobe.com/content/help/en/id-service/using/home.md)
- 이전 Analytics [방문자 ID 사용](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-overview.md)
- 고유한 ID 제공

## Using the Visitor ID Service{#using-the-visitor-id-service}

방문자 ID 서비스는 방문자를 식별하는 권장 방법입니다. 두 가지 구성 요소를 기반으로 합니다.

- 자사 ID - 자사 웹 사이트의 방문자를 측정하는 데 사용할 수 있는 퍼스트 파티 ID입니다. 이 ID는 첫 번째 partry id에 저장됩니다. 이 ID는 클라이언트측 쿠키와 서버측 쿠키(CNAME 포함) 모두에 저장됩니다.
- 타사 ID(선택 사항) - 여러 도메인(예: example.com 및 example.net)에서 방문자를 측정하는 데 사용할 수 있는 demdex.net에 저장되는 별도의 타사 ID

Analytics는 타사 ID가 활성화되지 않는 한 퍼스트 파티 ID를 사용하며, 브라우저에서 이를 사용할 수 있습니다. 타사 ID는 고객이 Analytics에서 다른 고객과 데이터를 결합할 수 없도록 사전 고객으로 지정되어 있습니다.

## 기존 분석 도메인

Adobe 방문자 ID 서비스를 시작하기 전에 많은 고객이 기본 분석 도메인을 사용하여 ID 쿠키를 설정했습니다. 여기에는 CNAME `omtrdc.net`도메인 `2o7.net` 또는 CNAME 도메인이 포함됩니다. `omtrdc.net`, `2o7.net`경우에 따라서는 타사 쿠키를 저장하는 데 CNAME 도메인을 사용하기도 했습니다. 이러한 방식으로 설정된 쿠키는 고객이 다른 고객의 데이터와 데이터를 결합할 수 없도록 단일 고객으로 제한되었습니다. 고객이 소유하고 있는 사이트(예: example.com, example.co.jp)에서 사용자를 추적하려는 경우 타사 CNAMED 도메인(친숙한 타사 도메인)이라고도 함)이 사용되었습니다. 이 방법 또는 CNAME을 사용하여 친숙한 타사 도메인을 지원하는 방법은 더 강력하고 개인 정보 인식 방문자 ID 서비스를 허용하기 위해 더 이상 사용되지 않습니다. 고객은 가능한 한 빨리 도메인당 CNAME을 사용하는 방문자 ID 서비스로 이동해야 합니다.

## 자신의 ID 제공

고객이 선택하는 경우 Adobe의 ID 시스템을 모두 패싱하고 [사용자 지정 방문자 ID를 제공하여 자체적으로 구현할 수 있습니다](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md). 이 길을 선택하시면 알아두어야 할 사항이 몇 가지 있습니다.

- 옵트아웃 및 적절한 개인 정보 보호 컨트롤을 구현해야 합니다.
- 이 ID는 Analytics에만 적용됩니다.
- 귀하는 해당 ID를 유지할 책임이 있습니다.

## 데이터 수집 CNAMES

방문자 ID 서비스와 함께 CNAME을 사용하는 것이 좋습니다. 이렇게 하면 퍼스트 파티 방문자 ID가 HTTP 쿠키를 사용하여 지속되므로 쿠키의 지속성이 향상됩니다.

## OPTOUT

Adobe는 고객에게 옵트아웃 신호를 Adobe 시스템과 공유하기 위한 API를 제공하여 고객이 추적을 거부할 수 있도록 합니다. Adobe는 고객이 사용자 선택을 지원하기 위해 적절한 제어를 구현할 수 있는 방법에 대한 자세한 지침을 제공합니다.동의 [받기 전까지 쿠키가](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md) 실행되지 [](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md) 않도록 하는 옵트아웃 API 또는 옵션

## Experience Cloud Identity 서비스로 CNAME 지원 설정 {#section-25d4feb686d944e3a877d7aad8dbdf9a}

데이터 수집 서버 CNAME 지원은 CNAME을 [설정하고](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) Experience Cloud Identity Service에서 `visitor.marketingCloudServerSecure` 변수를 설정하고 AppMeasurement `s.trackingServerSecure` 에서 설정하여활성화됩니다.
