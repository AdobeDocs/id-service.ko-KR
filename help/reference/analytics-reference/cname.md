---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: 데이터 수집 CNAME 및 도메인 간 추적
title: 데이터 수집 CNAME 및 도메인 간 추적
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 9fe63cf3983a2ed6642837b02a3c3441ef745d70

---


# 데이터 수집 CNAME 및 도메인 간 추적{#data-collection-cnames-and-cross-domain-tracking}

고객이 다른 도메인을 방문하기 전에 식별될 수 있는 기본 시작 사이트가 있는 경우 CNAME은 서드 파티 쿠키를 수락하지 않는 브라우저(예: Safari)에서 도메인 간 추적을 활성화할 수 있습니다.

타사 쿠키를 허용하는 브라우저의 경우, 쿠키는 방문자 ID에 대한 요청 중에 데이터 수집 서버에서 설정합니다. 이 쿠키를 사용하면 방문자 ID 서비스가 동일한 Experience Cloud 조직 ID를 사용하여 구성된 모든 도메인에서 동일한 Experience Cloud 방문자 ID를 반환할 수 있습니다.

타사 쿠키를 거부하는 브라우저에서는 각 도메인에 대해 새 Experience Cloud 방문자 ID가 할당됩니다.

demdex.net 쿠키를 사용하면 방문자 ID 서비스가 Analytics의 s_vi 쿠키와 동일한 수준의 도메인 간 추적을 제공할 수 있습니다. 이 쿠키는 일부 브라우저에서 수락되고 도메인 간에 사용되지만 다른 브라우저에서는 거부됩니다.

## Data Collection CNAMEs {#section-48fd186d376a48079769d12c4bd9f317}

When the Analytics cookie was set by the data collection server, many customers have configured data collection server CNAME records as part of a [first-party cookie implementation](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.html) to avoid issues with browsers that reject third-party cookies. 이 프로세스에서는 방문자 ID 쿠키가 퍼스트 파티 쿠키로 설정되도록 데이터 수집 서버 도메인을 웹 사이트 도메인과 일치하도록 구성합니다.

방문자 ID 서비스는 JavaScript를 사용하여 현재 웹 사이트의 도메인에서 직접 방문자 쿠키를 설정하므로 퍼스트 파티 쿠키를 설정하는 데 더 이상 이 구성이 필요하지 않습니다.

단일 웹 속성(단일 도메인)을 갖는 고객은 데이터 수집 CNAME 외부로 마이그레이션하고 대신 기본 데이터 수집 호스트 이름(`omtrdc.net` 또는 `2o7.net`)을 사용할 수 있습니다.

그러나 데이터 수집에 CNAME을 사용하면 기본 랜딩 도메인과 서드 파티 쿠키를 수락하지 않는 브라우저의 다른 도메인 간 방문자를 추적할 수 있습니다. 여러 웹 속성(여러 도메인)을 가진 고객은 데이터 수집 CNAME을 유지 관리함으로써 혜택을 받을 수 있습니다. 다음 섹션에서는 도메인 간 방문자 추적이 작동하는 방식을 설명합니다.

## 도메인 간 추적 {#section-78925af798e24917b9abed79de290ad9}

방문자 ID 서비스는 사용자의 개인 정보 및 브라우저 설정이 허용하는 경우 도메인(하지만 동일한 소유 회사 내)에서 방문자를 추적하기 위해 demdex.net을 도메인으로 사용합니다.

CNAME은 추가적인 크로스 도메인 이점을 제공하지 않습니다. 예를 들어 `mymainsite.com`에 기본 사이트가 있다고 합니다. 보안 데이터 수집 서버(`smetrics.mymainsite.com`)를 가리키도록 CNAME 레코드를 구성했습니다.

사용자가 `mymainsite.com`을 방문하면 데이터 수집 서버에 의해 ID 서비스 쿠키가 설정됩니다. 데이터 수집 서버 도메인이 웹 사이트 도메인과 일치하기 때문에 가능한 것으로, 이를 가리켜 *자사 컨텍스트*&#x200B;에서의 쿠키 사용 또는 *자사 쿠키*&#x200B;라고 합니다.

다른 사이트에서도 이와 동일한 데이터 수집 서버를 사용하는 경우(예를 들어 `myothersiteA.com` 및 `myothersiteB.com`) 방문자가 나중에 이러한 사이트를 방문하면 `mymainsite.com` 방문 중에 설정된 쿠키가 HTTP 요청을 통해 데이터 수집 서버로 전송됩니다(브라우저는 도메인이 현재 웹 사이트 도메인과 일치하지 않더라도 해당 도메인에 대한 모든 HTTP 요청과 모든 쿠키를 전송함). CNAME을 사용하더라도 타사 컨텍스트에서 쿠키 *또는*&#x200B;타사 쿠키만 **&#x200B;사용한다고 합니다. 각 고유 도메인에 대해 CNAME을 사용하는 것이 좋습니다.

*참고: Safari는 설정된 방법에 관계없이 타사 컨텍스트에서 모든 쿠키를 차단합니다.*

## Experience Cloud Identity 서비스로 CNAME 지원 설정 {#section-25d4feb686d944e3a877d7aad8dbdf9a}

데이터 수집 서버 CNAME 지원은 `visitor.marketingCloudServerSecure` 변수를 설정하여 사용할 수 있습니다.
