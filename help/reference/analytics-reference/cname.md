---
description: 'null'
keywords: 작업 순서; ID 서비스
seo-description: 'null'
seo-title: 데이터 수집 CNAME 및 도메인 간 추적
title: 데이터 수집 CNAME 및 도메인 간 추적
uuid: BA 42 C 822-B 677-4139-B 1 ED -4 D 98 D 3320 FD 0
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# 데이터 수집 CNAME 및 도메인 간 추적{#data-collection-cnames-and-cross-domain-tracking}

고객이 다른 도메인을 방문하기 전에 식별될 수 있는 기본 시작 사이트가 있는 경우 CNAME은 서드 파티 쿠키를 수락하지 않는 브라우저(예: Safari)에서 도메인 간 추적을 활성화할 수 있습니다.

타사 쿠키를 수락하는 브라우저에서 쿠키는 방문자 ID에 대한 요청 동안 데이터 수집 서버에 의해 설정됩니다. 이 쿠키를 사용하면 방문자 ID 서비스에서는 동일한 Experience Cloud 조직 ID를 사용하여 구성된 모든 도메인에 동일한 Experience Cloud 방문자 ID를 반환할 수 있습니다.

타사 쿠키를 거부하는 브라우저에서는 새 Experience Cloud 방문자 ID가 각 도메인에 대해 지정됩니다.

demdex.net 쿠키를 사용하여 방문자 ID 서비스는 Analytics의 s_vi 쿠키와 동일한 수준의 도메인 간 추적을 제공합니다. Analytics에서 쿠키는 일부 브라우저에서 수락되고 도메인 간에 사용되지만 다른 브라우저에서는 거부됩니다.

## 데이터 수집 CNAME {#section-48fd186d376a48079769d12c4bd9f317}

데이터 수집 서버에서 Analytics 쿠키를 설정한 경우 많은 고객은 서드 파티 쿠키를 거부하는 브라우저 문제를 피하기 위해 데이터 수집 서버 CNAME 레코드를 [퍼스트 파티 쿠키 구현](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/)의 일부로 구성했습니다. 이 프로세스는 데이터 수집 서버 도메인을 사용자 웹 사이트의 도메인과 일치하게 구성하여 방문자 ID 쿠키가 퍼스트 파티 쿠키로 설정되도록 합니다.

방문자 ID 서비스는 JavaScript를 사용하여 현재 웹 사이트의 도메인에서 직접 방문자 쿠키를 설정하므로 퍼스트 파티 쿠키를 설정하는 데 이 구성이 더 이상 필요하지 않습니다.

단일 웹 속성(단일 도메인)을 갖는 고객은 데이터 수집 CNAME 외부로 마이그레이션하고 대신 기본 데이터 수집 호스트 이름(`omtrdc.net` 또는 `2o7.net`)을 사용할 수 있습니다.

그렇지만 데이터 수집에 대해 CNAME을 사용하면 브라우저에서 기본 랜딩 도메인과 서드 파티 쿠키를 수락하지 않는 다른 도메인 사이에서 방문자를 추적할 수 있다는 추가적인 이점이 있습니다. 여러 웹 속성(다중 도메인)을 갖는 고객은 데이터 수집 CNAME을 유지 관리하여 혜택을 얻을 수 있습니다. 다음 섹션에서는 도메인 간 방문자 추적 기능이 작동하는 방식을 설명합니다.

## CNAME이 도메인 간 추적을 가능하게 하는 방식 {#section-78925af798e24917b9abed79de290ad9}

Apple Safari 및 일부 다른 브라우저의 서드 파티 컨텍스트에서 퍼스트 파티 쿠키를 사용하는 방식 때문에, CNAME을 사용하면 기본 도메인과 동일한 추적 서버를 사용하는 추가 도메인 사이에서 고객을 추적할 수 있습니다.

예를 들어 `mymainsite.com`에 기본 사이트가 있다고 합니다. You configured the CNAME record to point to your secure data collection server: `smetrics.mymainsite.com`.

사용자가 `mymainsite.com`을 방문하면 데이터 수집 서버에 의해 ID 서비스 쿠키가 설정됩니다. This is allowed since the domain of the data collection server matches the domain of the website, and is what is known as using a cookie in a *first-party context*, or just a *first-party cookie*.

If you are also using this same data collection server on other sites (for example, `myothersiteA.com`, and `myothersiteB.com`), and a visitor later visits these sites, the cookie that was set during the visit to `mymainsite.com` is sent in the HTTPS request to the data collection server (remember that browsers send all cookies for a domain with all HTTPS requests to that domain, even if the domain doesn&#39;t match the domain of the current website). This is what is known as using a cookie in a *third-party context*, or just a *third-party cookie*, and it enables the same visitor ID to be used on these other domains. 브라우저는 타사 컨텍스트에서 퍼스트 파티 쿠키와 다르게 쿠키를 처리합니다.

*참고: Safari는 서드 파티 컨텍스트에서 쿠키 설정 방법에 관계없이 모든 쿠키를 차단합니다.*

따라서 도메인 간 방문자 식별을 위해서는 수집 도메인이 사람들이 흔히 방문하는 도메인이 되어야 합니다. If there is no *common* domain to use for the data collection domain, there is no cross-domain benefit to maintaining a CNAME for the data collection domain. 처음에 기본 시작 사이트를 방문하지 않으면 방문자는 보조 사이트 및 기본 사이트에서 다르게 식별됩니다.

## Experience Cloud ID 서비스로 CNAME 지원 설정 {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Data collection server CNAME support is enabled by setting the `visitor.marketingCloudServerSecure` variables.
