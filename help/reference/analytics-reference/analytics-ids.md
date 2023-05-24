---
description: Experience Cloud ID 서비스는 이전 Analytics 방문자 ID 메서드를 대체합니다.
keywords: ID 서비스
title: Analytics 및 Experience Cloud ID 설정
exl-id: 7399ea16-d13e-452c-b8d9-8d0699566aa2
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 100%

---

# Analytics 및 Experience Cloud ID 설정{#setting-analytics-and-experience-cloud-ids}

Experience Cloud ID 서비스는 이전 Analytics 방문자 ID 메서드를 대체합니다.

ID 서비스가 구현되면 이 코드는 AppMeasurement 전에 실행됩니다. ID 서비스는 Experience Cloud 및 Analytics ID를 검색하므로 AppMeasurement가 로드될 때 이러한 값이 준비됩니다.

AppMeasurement가 로드되면 Experience Cloud 및 Analytics ID 값이 ID 서비스에서 요청되고 각 서버 호출과 함께 데이터 수집으로 전송됩니다. ID 서비스는 방문자 ID를 결정하고 이를 단순히 AppMeasurement로 전달하므로 AppMeasurement JavaScript 파일 이전에 각 페이지에 ID 서비스를 포함 및 구현해야 합니다.

## Analytics ID 프로세스 변경 {#section-79bb86ae63f546419bb1a7ef5e710462}

[!DNL Experience Cloud] ID 서비스로 마이그레이션할 때의 주된 변경 사항은 이제 데이터 수집 웹 서버에서 반환되는 HTTP 헤더가 아니라 JavaScript를 사용하여 ID 쿠키가 설정된다는 것입니다. 이 변경 사항을 이해하기 위해 다음 섹션에서는 이러한 두 가지 방법을 사용하여 쿠키를 설정하는 방법에 대해 설명합니다.

**HTTP 헤더**

웹 서버의 HTTP 응답은 브라우저에서 쿠키를 설정합니다. 다음은 `s_vi` 쿠키가 설정되는 방식입니다. `s_vi` 쿠키는 Analytics 방문자를 식별합니다. 설정된 쿠키는 해당 서버에 대한 모든 후속 HTTP 요청과 함께 전송됩니다.

Adobe 데이터 수집 서버로 요청이 전송되면 헤더에 `s_vi` 쿠키가 있는지 확인을 받습니다. 이 쿠키가 요청에 있으면 방문자 식별에 사용됩니다. 쿠키가 요청에 없으면 서버에서 고유한 [!DNL Experience Cloud] ID를 생성하여 HTTP 응답 헤더의 쿠키로 설정한 다음 요청과 함께 다시 전송합니다. 쿠키는 브라우저에 저장되고 이후 사이트를 방문하는 동안 데이터 수집 서버로 다시 전송됩니다. 이를 통해 방문자를 방문 간에 식별할 수 있습니다.

그러나 Apple Safari와 같은 일부 브라우저는 서드파티 쿠키를 허용하지 않습니다. 이러한 쿠키는 현재 웹 사이트 이외의 도메인에서 브라우저에 설정된 쿠키입니다. 또한 Safari는 방문자가 이전에 해당 도메인에 방문한 적이 없는 경우 서드파티 도메인에서 쿠키를 차단합니다. 예를 들어 `mysite.com`을 방문 중이고 데이터 수집 서버가 `mysite.omtrdc.net`인 경우 브라우저가 `mysite.omtrdc.net`의 HTTP 헤더에서 반환되는 쿠키를 거부할 수 있습니다.

이를 피하기 위해 많은 고객들은 데이터 수집 서버에 대해 CNAME 레코드를 구현했습니다. 이렇게 하는 것이 [자사 쿠키 구현](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-first-party.html?lang=ko-KR) 전략의 효과적인 부분일 수 있습니다. CNAME 레코드가 고객 도메인의 호스트 이름을 데이터 수집 서버에 매핑하도록 구성된 경우(예: `metrics.mysite.com`을 `mysite.omtrdc.net`으로 매핑) 데이터 수집 도메인이 웹 사이트의 도메인과 일치하므로 [!DNL Experience Cloud] ID 쿠키가 저장됩니다. 따라서 ID 서비스 쿠키가 저장될 가능성이 높아집니다. 그러나 CNAME 레코드를 구성하고 데이터 수집 서버에 대한 SSL 인증서를 유지해야 하므로 이로 인해 약간의 오버헤드가 발생합니다.

**JavaScript**

JavaScript는 자사 도메인(현재 웹 사이트의 도메인)에 설정된 쿠키를 읽고 쓸 수 있습니다. [!DNL Experience Cloud] ID 서비스는 이 방법을 사용하여 모든 방문자 ID가 포함된 `AMCV_###@AdobeOrg` 쿠키를 설정하므로 방문자 ID 쿠키를 저장하기 위해 더 이상 추적 서버의 도메인이 웹 사이트의 도메인과 일치하지 않아도 됩니다. 대부분의 상황에서는 ID 서비스 쿠키를 설정하는 것이 더 좋습니다. CNAME 레코드 및 SSL 인증서의 오버헤드가 해소되기 때문입니다.

<!---However, there are a few situations where setting the cookie in the HTTP header is beneficial for cross-domain tracking, which is described in [Data Collection CNAMEs and Cross-Domain Tracking](../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d).-->

## 사용자 지정 분석 ID {#section-b6a7bd19e9ff432390010062450808f6}

`s.visitorID`를 사용하여 고객 ID를 설정하는 것은 Analytics에서 사용자를 식별하는 방법입니다. 그러나 ID 서비스를 사용하여 Analytics 데이터를 내보내거나 가져오는 통합은 방문자가 `s.visitorID`.

여기에는 공유 대상, Analytics for Target(A4T) 및 고객 속성이 포함되지만, 이에 제한되지 않습니다. 이러한 통합의 경우 사용자 지정 Analytics ID를 설정할 수 없습니다.

## Analytics 방문자 ID 순서 {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

방문자 ID 서비스를 배포한 후에는 Analytics에서 방문자를 식별하는 다음과 같은 5가지 방법이 있습니다(기본 설정 순서로 다음 표에 나열됨).

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 사용된 명령 </th> 
   <th colname="col2" class="entry"> 쿼리 매개 변수(수집 방법) </th> 
   <th colname="col3" class="entry"> 제공 시점 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=ko-KR" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>s.visitorID가 설정되어 있습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=ko-KR" format="http" scope="external"> aid (s_vi 쿠키)</a> </p> </td> 
   <td colname="col3"> <p><span class="keyword">Experience Cloud</span> ID 서비스를 배포하기 전에 방문자에게 기존의 s_vi 쿠키가 있었거나 또는 <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">유예 기간</a>을 구성했습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid(Experience Cloud 방문자 ID 서비스에 의해 설정된 AMCV_ 쿠키) </p> </td> 
   <td colname="col3"> <p>방문자의 브라우저가 자사 쿠키를 수락합니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/analytics-ids.html?lang=ko-KR" format="http" scope="external"> fid(H.25.3 이상의 폴백 쿠키 또는 AppMeasurement for JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>브라우저가 서드파티 쿠키를 허용하지 않으며 Analytics 추적 서버가 서드파티 추적 서버로 설정됩니다. </p> <p> <p>참고: <span class="codeph">fid</span>는 기존 식별자이며, 사용자 사이트에서 ID 서비스를 구현한 경우에는 사용되지 않습니다. 이 경우 자사 <a href="../../introduction/cookies.md" format="dita" scope="local">AMCV 쿠키</a>로 인해 <span class="codeph">fid</span>를 사용할 수 없으므로 이 fid가 필요하지 않습니다. fid는 기존 코드를 지원하기 위해 또한 여러 기록상의 이유로 인해 유지되고 있습니다. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/technotes/visitor-identification.html?lang=ko-KR" format="http" scope="external"> IP 주소, 사용자 에이전트, 게이트웨이 IP 주소</a> </p> </td> 
   <td colname="col3"> <p>방문자의 브라우저가 쿠키를 수락하지 않습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

많은 시나리오에서 한 번의 호출로 2~3개의 다른 ID가 표시될 수 있지만, Analytics에서는 해당 목록에 있는 첫 번째 ID를 공식적인 [!DNL Experience Cloud] ID로 사용합니다. 예를 들어, 사용자 지정 방문자 ID(&quot;vid&quot; 쿼리 매개 변수에 포함됨)를 설정하는 경우, 이 ID는 동일한 히트에 있을 수 있는 다른 ID보다 먼저 사용됩니다.

>[!MORELIKETHIS]
>
>* [Analytics ID 작업 순서](../../reference/analytics-reference/analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)

