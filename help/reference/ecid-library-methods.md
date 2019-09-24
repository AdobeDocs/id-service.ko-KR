---
title: Safari ITP 환경의 ECID 라이브러리 메서드
seo-title: Safari ITP 환경의 ECID 라이브러리 메서드
description: Adobe ECID(ID 서비스) 라이브러리에 대한 문서입니다.
seo-description: Adobe ECID(ID 서비스) 라이브러리에 대한 문서입니다.
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Safari ITP 환경의 ECID 라이브러리 메서드

Safari는 ITP를 통해 교차 도메인 추적을 강화하므로 Adobe는 소비자 개인 정보 및 선택 사항뿐만 아니라 고객을 지원하는 라이브러리에 대한 모범 사례를 유지 관리해야 합니다.

2019년 2월 21일, Apple은 ITP(Intelligent Tracking Prevention)에 대한 최신 업데이트를 발표했습니다. 타사 쿠키에 중점을 둔 이전 버전과 달리, 이 버전은 자사 쿠키에 대한 새로운 추적 방지 조치를 제공합니다. document.cookie API를 통해 설정된 모든 자사의 영구 쿠키는 "클라이언트측" 쿠키라고 하며, 만료가 7일로 제한됩니다. 이전 버전의 ITP에 명시된 대로 타사 쿠키는 계속 차단됩니다. For more details on ITP 2.1 and the impact of Adobe solutions, read [Safari ITP 2.1 Impact on Adobe Experience Cloud and Experience Platform Customers](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Safari ITP용 Adobe ECID FAQ

**ECID(Experience Cloud ID 라이브러리)가 고객의 자사 도메인에 설정한 AMCV 쿠키가 ITP 2.1의 영향을 받는 이유는 무엇입니까?**

AMCV 쿠키는 현재 document.cookie API를 사용하며 "클라이언트측"을 통해 설정됩니다. Safari는 고객의 서버에서 설정된 쿠키를 선호합니다.

**CNAME 추적 서버를 통해 설정된 쿠키가 Safari에서 추적하는 데 더 나은 옵션인 이유는 무엇입니까?**

ITP 규칙은 개발자에게 다시 제어 권한을 제공하는 데 중점을 둡니다. CNAME 인증서를 통한 구현은 JavaScript만을 통해서는 수행할 수 없습니다. Adobe의 CNAME 인증 프로그램(서버측 추적)은 ITP를 따르며, 여러 해 동안 Adobe 전략의 일부로서 Adobe 전략의 일부가 되었습니다. ECID 라이브러리는 ECID 라이브러리 기능을 CNAME 구현으로 이동하는 데 중점을 둔 메서드를 전달합니다.

**다른 Analytics 방문자 추적 메서드를 CNAME에서 사용할 때 Adobe가 ECID에 중점을 두는 이유는 무엇입니까?**

ECID 라이브러리, AMCV 쿠키 및 ECID(MID라고도 함)는 모든 Adobe 솔루션을 하나의 ID에 통합하는 메서드로 시작되었습니다. 이 ID는 Adobe 제품 로드맵에서 우선 순위 쿠키 수준 ID가 되며, Adobe Experience Platform의 기본 쿠키 ID입니다.

**CNAME은 고객이 다중 도메인 추적을 사용하도록 지원합니까?**

이전에 CNAME에 있던 동일한 규칙 및 조건이 여전히 있습니다. 경우에 따라 CNAME은 다중 도메인 시나리오에서 도움이 될 수 있습니다. 사용자가 다른 도메인을 방문하기 전에 식별될 수 있는 기본 시작 사이트가 있는 경우 CNAME은 타사 쿠키를 수락하지 않는 브라우저(예: Safari)에서 다중 도메인 추적을 활성화할 수 있습니다. 그러나 CNAME이 일부 시나리오의 다중 도메인에 도움이 될 수 있지만 ECID가 CNAME 구현으로 이동하는 이유는 다중 도메인 추적이 아닌 지속적인 방문자 식별을 위한 것입니다. CNAME 및 다중 도메인에 대한 자세한 내용은 [데이터 수집 CNAME 및 도메인 간 추적](/help/reference/analytics-reference/cname.md)을 참조하십시오.

추가 ITP 변경 사항이 릴리스되면 추가된 FAQ가 여기에 추가됩니다. For more inquiries, please visit [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics).

## ITP 관련 변경 사항, 메서드 및 구성

Safari에서 추적을 위해 추가 메서드가 생성되면 이 페이지에 참조로 추가됩니다.

>[!NOTE]아래 모든 문서에서 *ECID* = *MID* = *MCID*.

ITP 및 ECID 라이브러리 사용과 관련된 작업은 아래를 참조하십시오.

## ECID 라이브러리 및 CNAME 추적을 사용하여 방문자 ID 만료를 연장합니다.

ITP 2.1은 클라이언트측 쿠키를 작성하는 기능을 제한하여 고객에게 정확한 방문자 추적 정보를 제공하는 기능에 손상을 줍니다. 따라서 방문자의 ECID(Experience Cloud ID)를 자사 쿠키에 저장하도록 Adobe의 CNAME 추적 서버가 변경되었습니다.

이 변경 사항은 자사 컨텍스트에서 Analytics CNAME을 사용하는 ECID 고객에게만 유용합니다. 현재 CNAME을 사용하고 있지 않은 Analytics 고객이거나 비 Analytics 고객이더라도 CNAME 레코드 대상입니다. CNAME 등록 프로세스를 시작하려면 고객 지원 센터 또는 계정 담당자에게 [문의하십시오](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html).

이 변경 사항을 사용하려면 ECID 라이브러리 v. 4.3.0 이상으로 업그레이드하십시오.

**디자인**

demdex.net에 ID를 요청하고 ECID를 검색하면 추적 서버가 ECID 라이브러리에 설정된 경우 고객의 도메인에 대한 ID 요청이 수행됩니다. 이 종단점은 쿼리 문자열에서 ecid 매개 변수를 읽고 ECID 및 만료 날짜만 향후 2년으로 구성하는 새로운 [쿠키](/help/introduction/cookies.md)를 설정합니다. 이 종단점이 이 방식으로 호출될 때마다 `s_ecid` 쿠키는 해당 호출 시간으로부터 2년으로 만기 날짜가 다시 작성됩니다. 이 쿠키의 값을 검색할 수 있도록 ECID 라이브러리를 v 4.3.0으로 업데이트해야 합니다.

이러한 새로운 `s_ecid` 쿠키는 AMCV 쿠키와 동일한 옵트아웃 상태를 따릅니다. ecid를 `s_ecid` 쿠키에서 읽으면 demdex는 항상 해당 ID의 최신 옵트아웃 상태를 검색하도록 즉시 호출되고 AMCV 쿠키에 저장됩니다.

또한 소비자가 이 [방법을](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html)통해 Analytics 추적을 옵트아웃한 경우 이 `s_ecid` 쿠키가 삭제됩니다.

trackingServer 또는 trackingServerSecure를 사용하여 라이브러리를 초기화할 때 추적 서버 이름을 VisitorJS 라이브러리에 제공해야 합니다. 이 옵션은 Analytics 구성의 trackingServer 구성과 일치해야 합니다.

이 메서드를 사용하지 않도록 선택하는 경우 discardtrackingServerECID 구성을 ECID 라이브러리 구현에 추가하십시오. 이 구성이 true로 설정되면 방문자 라이브러리는 자사 추적 서버에서 설정한 MID를 읽지 않습니다.

![](assets/itp-proposal-v1.png)

## 상호 도메인 추적(회사의 여러 도메인 내)에 appendVisitorIDsTo 메서드 사용

이 기능을 사용하면 브라우저에서 타사 쿠키를 차단할 때 도메인에서 방문자의 ECID를 공유할 수 있습니다. 이 기능을 사용하기 위해 ID 서비스를 구현했을 것이며, 소스 및 대상 도메인을 소유해야 합니다. VisitorAPI.js 버전 1.7.0 이상(그러나 버전 1.10.0에는 없음)에서 사용 가능합니다.

**디자인**

* 방문자가 다른 도메인으로 이동할 때 Visitor.appendVisitorIDsTo(url)는 ECID가 추가된 URL을 질의 매개 변수로 반환합니다.

   이 URL을 사용하여 원래 도메인에서 대상 도메인으로 리디렉션합니다.

* 대상 도메인의 ID 서비스 코드는 Adobe에 해당 방문자의 ID 요청을 전송하는 대신 URL에서 ECID를 추출합니다.

   이 요청에는 타사 쿠키 ID가 포함되어 있으며, 이 경우에는 사용할 수 없습니다.

* 대상 페이지의 ID 서비스 코드는 전달한 ECID를 사용하여 방문자를 추적합니다.

   >[!NOTE]
   >대상 페이지에 이미 이전 방문의 ECID가 있는 경우, 기존 쿠키를 겹쳐쓸 것인지 여부는 이 구성 overwriteCrossDomainMCIDAndAID에 의해 제어됩니다. 이 구성에 대한 자세한 내용은 [overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md)를 참조하십시오.
   >
   >이 메서드에 대한 자세한 내용은 [appendVisitorIDsTo(도메인 간 추적)](/help/library/get-set/appendvisitorid.md) 참조 페이지를 참조하십시오.
