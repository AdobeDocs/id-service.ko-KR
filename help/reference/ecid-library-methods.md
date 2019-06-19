---
title: Safari ITP World의 ECID 라이브러리 메서드
seo-title: Safari ITP World의 ECID 라이브러리 메서드
description: Adobe ECID (ID 서비스) 라이브러리에 대한 설명서.
seo-description: Adobe ECID (ID 서비스) 라이브러리에 대한 설명서.
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Safari ITP World의 ECID 라이브러리 메서드

Safari는 ITP를 통해 크로스 도메인 추적을 강화하므로 Adobe는 고객을 지원하는 라이브러리, 소비자 개인 정보 보호 및 선택의 모범 사례를 유지 관리해야 합니다.

2019 년 2 월 21 일 Apple는 ITP (Intelligent Tracking Prevention) 에 대한 최신 업데이트를 발표했습니다. 타사 쿠키에 중점을 둔 이전 버전과 달리, 이 버전은 퍼스트 파티 쿠키에 대한 새로운 추적 방지 측정을 제공합니다. &quot; 클라이언트측 &quot;쿠키라고도 하는 document. cookie API를 통해 설정된 모든 퍼스트 파티 영구 쿠키는 7 일에 만료됩니다. 이전 버전의 ITP에 명시된 바와 같이 타사 쿠키는 계속 차단됩니다. ITP 2.1에 대한 자세한 내용과 Adobe 솔루션의 파급력에 대한 자세한 내용은 [Adobe Experience Cloud 및 Experience Platform 고객을 위한 Safari ITP 2.1를 읽어](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac)보시기 바랍니다.

## Safari ITP 용 Adobe ECID FAQ

**고객의 퍼스트 파티 도메인에 있는 Experience Cloud ID 라이브러리 (ECID) 가 ITP 2.1에 의해 영향을 받는 AMCV 쿠키가 설정되는 이유는 무엇입니까?**

현재 AMCV 쿠키는 document. cookie API에 의존하고 있으며 &quot;클라이언트측&quot; 를 통해 설정됩니다. Safari는 고객의 서버에서 설정된 쿠키를 선호합니다.

**Safari에서 추적을 위해 CNAME 추적 서버를 통해 쿠키가 설정된 이유는 무엇입니까?**

ITP의 규칙은 개발자에게 제어를 제공하는 데 중점을 둡니다. CNAME 인증서를 통한 구현은 JavaScript를 통해서만 수행할 수 있습니다. Adobe의 CNAME 인증 프로그램 (서버측 추적) 는 ITP와 관련이 있으며 수년간 Adobe 전략의 일부로 사용되고 있습니다. ECID 라이브러리는 ECID 라이브러리 기능을 CNAME 구현으로 이동하는 데 초점을 둔 메서드를 출시합니다.

**다른 Analytics 방문자 추적 방법이 CNAME와 함께 사용되는 경우 Adobe가 ECID 라이브러리에 주력하는 이유는 무엇입니까?**

ECID 라이브러리, AMCV 쿠키 및 ECID (aka mid) 는 하나의 ID 아래에 모든 Adobe 솔루션을 통합하는 방법으로 시작되었습니다. 이 ID는 Adobe 제품 로드맵에서 우선 순위 쿠키 수준 ID가 되며 Adobe Experience Platform의 기본 쿠키 ID 입니다.

**CNAME에서 고객이 다중 도메인 추적을 활성화하는 데 도움이 됩니까?**

이전에 CNAME를 사용하여 존재했던 동일한 규칙과 경고가 여전히 존재합니다. 경우에 따라 CNAME는 다중 도메인 시나리오에서 도움을 줄 수 있습니다. 사용자가 다른 도메인을 방문하기 전에 식별될 수 있는 기본 시작 사이트가 있는 경우 CNAME는 타사 쿠키를 수락하지 않는 브라우저에서 다중 도메인 추적을 활성화할 수 있습니다. 하지만 CNAME는 일부 시나리오에서 여러 도메인을 지원하는 데 도움이 되지만 ECID를 CNAME 구현으로 변환하는 것은 다중 도메인 추적이 아닌 지속적인 방문자 식별을 위한 것입니다. CNAME 및 다중 도메인에 대한 자세한 내용은 [데이터 수집 CNAME 및 도메인 간 추적을 참조하십시오](/help/reference/analytics-reference/cname.md).

추가 ITP 변경 사항이 릴리스되면 더 많은 FAQ가 여기에 추가됩니다. 자세한 내용은 [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics)를 참조하십시오.

## ITP 관련 변경 사항, 메서드 및 구성

Safari 내에서 추적을 위해 추가 메서드가 만들어지면 이 페이지에 대한 참조로 추가됩니다.

>[!NOTE]*ecid* = *mid* = *MCID* (아래 모든 문서)

ITP 및 ECID 라이브러리 사용과 관련된 노력에 대해서는 아래를 참조하십시오.

## ECID 라이브러리 및 CNAME 추적을 사용하여 방문자 ID 만료 확장

ITP 2.1는 클라이언트측 쿠키를 작성할 수 있는 기능을 제공하므로 고객에게 정확한 방문자 추적 정보를 제공할 수 있습니다. 이와 같이, Adobe의 CNAME 추적 서버에서 방문자의 Experience Cloud ID (ECID) 를 자사 쿠키에 저장하기 위해 변경 사항이 도입되고 있습니다.

이 변경 사항은 퍼스트 파티 컨텍스트에서 Analytics CNAME를 사용하는 ECID 고객에게만 유용합니다. 현재 CNAME를 사용하고 있지 않거나 Analytics 이외의 고객을 사용하고 있는 Analytics 고객은 여전히 CNAME 레코드를 사용할 수 있습니다. CNAME 등록 프로세스를 시작하려면 [고객 지원 센터 또는 계정 담당자에게](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html)문의하십시오.

이 변경 사항을 적용하려면 ECID 라이브러리 v. 4.3.0 +로 업그레이드하십시오.

**디자인**

demdex. net에 ID 요청이 수행되고 ECID가 검색되면 추적 서버가 ECID 라이브러리에서 설정되면 고객의 도메인에 ID 요청이 수행됩니다. 이 끝점은 쿼리 문자열에서 ECID 매개 변수를 읽고, 향후 2 년 동안 ECID 및 만료 날짜만 구성하는 새 [쿠키를](/help/introduction/cookies.md) 설정합니다. 이 방법으로 이 종점이 호출될 때마다 `s_ecid` 쿠키는 해당 호출 시점으로부터 2 년 동안 만료 날짜로 다시 작성됩니다. 이 쿠키의 값을 검색할 수 있도록 Ecid 라이브러리를 v 4.3.0로 업데이트해야 합니다.

이 새 `s_ecid` 쿠키는 AMCV 쿠키와 동일한 옵트아웃 상태를 따릅니다. `s_ecid` 쿠키에서 ECID를 읽은 경우 demdex는 항상 해당 ID에 대한 최신 옵트아웃 상태를 검색하기 위해 호출되며 AMCV 쿠키에 저장됩니다.

또한 소비자가 이 [방법을](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html)통해 Analytics 추적을 옵트아웃했다면 `s_ecid` 이 쿠키는 삭제됩니다.

Trackingserver 또는 trackingserversecure를 사용하여 라이브러리를 초기화하는 경우 visitorjs 라이브러리에 추적 서버 이름을 제공해야 합니다. 이것은 Analytics 구성의 trackingserver 구성과 일치해야 합니다.

이 방법을 활용하지 않도록 선택한 경우 ECID 라이브러리 구현에 다음 구성을 추가하십시오. Discardtrackingserverecid를 삭제합니다. 이 구성을 true로 설정하면 방문자 라이브러리는 퍼스트 파티 추적 서버에 의해 설정된 MID를 읽지 않습니다.

![](assets/itp-proposal-v1.png)

## Appendvisitoridto 메서드를 사용하여 도메인 간 추적을 위한 방법 (회사 여러 도메인 내)

브라우저에서 타사 쿠키를 차단할 때 이 함수를 사용하면 도메인 간에 방문자의 ECID를 공유할 수 있습니다. 이 기능을 사용하기 위해 ID 서비스를 구현했을 것이며, 소스 및 대상 도메인을 소유해야 합니다. Visitorapi. js 버전 1.7.0 이상에서 사용할 수 있습니다 (버전 1.10.0 에서는 제외).

**디자인**

* 방문자가 다른 도메인으로 찾아가면 visitor. appendvisitoridsto (URL) 는 쿼리 매개 변수로 추가된 ECID가 포함된 URL를 반환합니다.

   이 URL를 사용하여 원래 도메인에서 대상 도메인으로 리디렉션합니다.

* 대상 도메인의 ID 서비스 코드는 해당 방문자의 ID에 대한 요청을 Adobe에 보내지 않고 URL에서 ECID를 추출합니다.

   이 요청에는 타사 쿠키 ID가 포함되어 있으며, 이 경우에는 사용할 수 없습니다.

* 대상 페이지의 ID 서비스 코드는 전달된 ECID를 사용하여 방문자를 추적합니다.

   >[!NOTE]
   >대상 페이지에 이미 이전 방문의 ECID가 있는 경우 기존 쿠키를 덮어쓰기로 결정한 경우 이 구성 overwritecrossdomainmciaid에 의해 제어됩니다. 이 구성에 대한 자세한 내용은 [Overwritecrossdomainmandaid](/help/library/function-vars/overwrite-visitor-id.md)를 참조하십시오.
   >
   >이 방법에 대한 자세한 내용은 [Appendvisitoridsto (Cross Domain Tracking)](/help/library/get-set/appendvisitorid.md) 참조 페이지를 참조하십시오.
