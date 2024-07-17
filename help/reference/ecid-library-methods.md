---
title: Safari ITP 환경의 ECID 라이브러리 메서드
description: Adobe ECID(ID 서비스) 라이브러리에 대한 문서입니다.
exl-id: ac1d1ee1-2b5f-457a-a694-60bb4c960ae7
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 100%

---

# Safari ITP 환경의 ECID 라이브러리 메서드

>[!NOTE]
>
>Big Sur OS 릴리스의 일부로 2020년 11월 12일에 릴리스된 ITP의 최신 변경 사항을 반영하도록 업데이트되었습니다.

Safari는 ITP를 통해 교차 도메인 추적을 강화하므로 Adobe는 소비자 개인정보 및 선택 사항뿐만 아니라 고객을 지원하는 라이브러리에 대한 모범 사례를 유지 관리해야 합니다.

2020년 11월 10일 현재, &quot;클라이언트측&quot; 쿠키라고도 하는 document.cookie API를 통해 설정된 모든 자사 영구 쿠키와 Safari 및 모바일 iOS 브라우저에서 자사 CNAME 구현을 통해 설정된 쿠키의 만료 기한이 7일로 제한됩니다. 이전 버전의 ITP에 명시된 대로 서드파티 쿠키는 계속 차단됩니다. ITP 2.1 및 Adobe 솔루션이 미치는 영향에 대한 자세한 내용은 [Safari ITP 2.1이 Adobe Experience Cloud 및 Experience Platform 고객에게 미치는 영향](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac)을 참조하십시오.

## ITP 관련 변경 사항, 메서드 및 구성

Safari에서 추적을 위해 추가 메서드가 생성되면 이 페이지에 참조로 추가됩니다.

>[!NOTE]
>
>*아래 모든 문서에서 ECID* = *MID* = *MCID*.

ITP 및 ECID 라이브러리 사용과 관련된 작업은 아래를 참조하십시오.

## ITP 및 Apple의 WebKit을 사용한 현재 ECID 라이브러리 동작

ITP 2.1은 클라이언트측 쿠키를 작성하는 기능을 제한하여 고객에게 정확한 방문자 추적 정보를 제공하는 기능에 손상을 줍니다. 따라서 방문자의 ECID(Experience Cloud ID)를 자사 쿠키에 저장하도록 Adobe의 CNAME 추적 서버가 변경되었습니다.

이 변경 사항은 자사 컨텍스트에서 Analytics CNAME을 사용하는 ECID 고객에게만 유용합니다. 현재 CNAME을 사용하고 있지 않은 Analytics 고객이거나 비 Analytics 고객이더라도 CNAME 레코드 대상입니다. [CNAME](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-first-party.html?lang=ko-KR) 등록 프로세스를 시작하려면 고객 지원 센터 또는 계정 담당자에게 문의하십시오.

이 변경 사항을 사용하려면 ECID 라이브러리 v. 4.3.0 이상으로 업그레이드하십시오.

다음은 ECID 라이브러리가 ITP 2.1과 Big Sur 릴리스의 일부로 Apple에서 변경한 최신 변경 사항에서 작동하는 방식에 대한 개요입니다.

**디자인**

demdex.net에 ID를 요청하고 ECID를 검색하면 추적 서버가 ECID 라이브러리에 설정된 경우 고객의 도메인에 대한 ID 요청이 수행됩니다. 이 종단점은 쿼리 문자열에서 ecid 매개 변수를 읽고 ECID 및 만료 날짜만 향후 2년으로 구성하는 새로운 [쿠키](/help/introduction/cookies.md)를 설정합니다. 이 종단점이 이 방식으로 호출될 때마다 `s_ecid` 쿠키는 해당 호출 시간으로부터 2년으로 만기 날짜가 다시 작성됩니다. 이 쿠키의 값을 검색할 수 있도록 ECID 라이브러리를 v 4.3.0으로 업데이트해야 합니다.

>[!IMPORTANT]
>
>Big Sur 업데이트의 일부로서, `s_ecid`CNAME을 통해 설정된 쿠키도 만료 기한인 7일간 유지됩니다.

이러한 새로운 `s_ecid` 쿠키는 AMCV 쿠키와 동일한 옵트아웃 상태를 따릅니다. ecid를 `s_ecid` 쿠키에서 읽으면 demdex는 항상 해당 ID의 최신 옵트아웃 상태를 검색하도록 즉시 호출되고 AMCV 쿠키에 저장됩니다.

또한 소비자가 이 [방법](https://experienceleague.adobe.com/docs/analytics/implementation/js/opt-out.html?lang=ko-KR)을 통해 Analytics 추적을 옵트아웃한 경우 이 `s_ecid` 쿠키가 삭제됩니다.

`trackingServer`또는 `trackingServerSecure`을 사용하여 라이브러리를 초기화할 때 추적 서버 이름을 VisitorJS 라이브러리에 제공해야 합니다. 이 옵션은 `trackingServer`Analytics 구성의 구성과 일치해야 합니다.

이 메서드를 사용하지 않도록 선택하는 경우 다음 구성을 ECID 라이브러리 구현에 추가하십시오. `discardtrackingServerECID` 이 구성이 true로 설정되면 방문자 라이브러리는 자사 추적 서버에서 설정한 MID를 읽지 않습니다.

![](assets/itp-proposal-v1.png)

## 상호 도메인 추적(회사의 여러 도메인 내)에 appendVisitorIDsTo 메서드 사용

이 기능을 사용하면 브라우저에서 서드파티 쿠키를 차단할 때 도메인에서 방문자의 ECID를 공유할 수 있습니다. 이 기능을 사용하기 위해 ID 서비스를 구현했을 것이며, 소스 및 대상 도메인을 소유해야 합니다. VisitorAPI.js 버전 1.7.0 이상(그러나 버전 1.10.0에는 없음)에서 사용 가능합니다.

**디자인**

* 방문자가 다른 도메인으로 이동할 때 Visitor.appendVisitorIDsTo(url)는 ECID가 추가된 URL을 질의 매개 변수로 반환합니다.

  이 URL을 사용하여 원래 도메인에서 대상 도메인으로 리디렉션합니다.

* 대상 도메인의 ID 서비스 코드는 Adobe에 해당 방문자의 ID 요청을 전송하는 대신 URL에서 ECID를 추출합니다.

  이 요청에는 서드파티 쿠키 ID가 포함되어 있으며, 이 경우에는 사용할 수 없습니다.

* 대상 페이지의 ID 서비스 코드는 전달한 ECID를 사용하여 방문자를 추적합니다.

  >[!NOTE]
  >대상 페이지에 이미 이전 방문의 ECID가 있는 경우, 기존 쿠키를 겹쳐 쓸 것인지 여부는 이 구성 overwriteCrossDomainMCIDAndAID에 의해 제어됩니다. 이 구성에 대한 자세한 내용은 [overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md)를 참조하십시오.
  >
  >이 메서드에 대한 자세한 내용은 [appendVisitorIDsTo(도메인 간 추적)](/help/library/get-set/appendvisitorid.md) 참조 페이지를 참조하십시오.
