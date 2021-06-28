---
description: 이 섹션을 검토하여 Experience Cloud ID 서비스에 필요한 올바른 솔루션, 서비스 및 쿠키 버전을 사용 중인지 확인하십시오.
keywords: ID 서비스
title: Experience Cloud ID 서비스 요구 사항
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '730'
ht-degree: 100%

---

# Experience Cloud ID 서비스 요구 사항 {#requirements-for-the-experience-cloud-id-service}

이 섹션을 검토하여 Experience Cloud ID 서비스에 필요한 올바른 솔루션, 서비스 및 쿠키 버전을 사용 중인지 확인하십시오.

## 구현의 성공 및 지원을 위한 요구 사항 {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

지원되는 성공적인 구현은 코드 요구 사항을 충족하며 [!DNL Adobe] 도움말에 표시된 지침을 따릅니다. 지원되지 않는 구현으로 인해 예기치 않은 결과가 발생하고, 고객 지원 센터 및 엔지니어링 팀이 ID 서비스의 문제를 해결하거나 해결하는 데 도움을 주지 못지 못할 수 있습니다.

<table id="table_2216C44AA66248DCAA13BF64BDF2D88A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 구현 유형 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> 표준</a> </p> </td> 
   <td colname="col2"> <p>DTM(Dynamic Tag Management)을 사용한 표준 구현의 경우, 다음을 수행해야 합니다. </p> 
    <ul id="ul_59CDE179566844B494F3068FF6333809"> 
     <li id="li_CCCB6AFC08EE405F94C42216D3CE50AC"> 페이지의 <span class="codeph">&lt;head&gt;</span> 섹션에 포함 헤드 코드를 넣습니다. </li> 
     <li id="li_13962F2CB1764091A84863BE499675A2"><span class="codeph">&lt;/body&gt;</span> 태그를 닫기 전에 포함 바닥글 코드를 넣습니다. </li> 
    </ul> <p>다음과 같은 경우에는 표준 구현이 지원되지 않습니다. </p> 
    <ul id="ul_3B62559317ED4C7AA548C3B8DBA281F7"> 
     <li id="li_1F16C6D412944197BEA56BC24730782C"> 이러한 DTM 포함 코드를 마크업 및/또는 페이지 코드의 다른 곳에 배치합니다. </li> 
     <li id="li_05615C01F3A947BBBD41046E68377224"> 비동기 메서드, 호출/콜백 메서드 또는 래퍼를 사용하여 DTM 코드를 추가, 추가 또는 로드할 수 있습니다. </li> 
     <li id="li_B2137DFF627B473FA876580449026D2B">동일한 페이지에 임베드 코드의 여러 인스턴스를 포함할 수 있습니다. </li> 
    </ul> <p><a href="https://experienceleague.adobe.com/docs/dtm/using/client-side/deployment.html?lang=ko-KR" format="https" scope="external">포함 코드 및 호스트 옵션</a>도 참조하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113" format="dita" scope="local"> 비표준 구현 </a> </p> </td> 
   <td colname="col2"> <p>비표준 또는 수동 구현의 경우 이 안내서의 절차에 따라 ID 서비스를 설정해야 합니다. 위의 DTM 지침과 마찬가지로, 부적절한 코드 배치 및 로딩으로 인해 지원되지 않는 구현이 수행될 수 있습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Experience Cloud 요구 사항: 조직 ID {#section-a02f537129a64ffbb690d5738d360c26}

ID 서비스를 사용하려면 회사에 [!DNL Experience Cloud]가 활성화되고 조직 ID가 있어야 합니다. 회사의 [!DNL Experience Cloud] 상태를 잘 모르고 조직 ID를 찾아야 하는 경우에는 다음 목록을 확인합니다.

>[!IMPORTANT]
>
>조직 ID는 대/소문자를 구분하므로 제공된 그대로 정확히 사용해야 합니다.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud 상태 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>활성화됨</b> </p> </td> 
   <td colname="col2"> <p>회사가 <span class="keyword">Experience Cloud</span>에 대해 활성화되어 있지만 사용자에게 조직 ID가 없는 경우 <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=ko-KR" format="https" scope="external">조직 ID</a>(<i>조직 ID 찾기</i> 섹션까지 스크롤)를 참조하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>확실하지 않음</b> </p> </td> 
   <td colname="col2"> <p> 회사의 <span class="keyword">Experience Cloud</span> 상태를 잘 모를 경우 회사 구성원이 Adobe ID를 사용하여 <a href="https://experiencecloud.adobe.com" format="https" scope="external">marketing.adobe.com</a>에 로그인할 수 있는지를 Adobe 계정 관리자에게 문의하십시오. 로그인할 수 있으면 해당 기능이 사용 가능하게 설정되어 있고 관리자가 사용자의 조직 ID를 볼 수 있는 것입니다. 조직 ID를 찾으려면 <a href="https://docs.adobe.com/help/ko-KR/core-services/interface/experience-cloud.html" format="https" scope="external">Experience Cloud 관리</a>에서 "관리 페이지" 섹션을 참조하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>활성화되지 않음</b> </p> </td> 
   <td colname="col2"> <p> 회사에 Experience Cloud가 활성화되지 않은 경우 <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=ko-KR" format="https" scope="external">핵심 서비스 - 솔루션 활성화</a>를 참조하여 시작하십시오. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analytics 요구 사항: RDC(지역 데이터 수집) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

모든 추적 서버가 RDC로 변환되었으므로 Analytics 추적 서버를 변경할 필요가 없습니다. [추가 정보...](https://experienceleague.adobe.com/docs/analytics/admin/data-collection/regional-data-collection/regional-data-collection.html?lang=ko-KR)

## 코드 라이브러리 및 버전 요구 사항 {#section-ad7542a4317d430fa79fc6b095beb84d}

다음 섹션에는 [!DNL Experience Cloud] ID 서비스 사용에 필요한 최소 코드 버전이 나와 있습니다.

>[!TIP]
>
>필요한 최소 코드 버전보다 최신 코드 버전을 사용하는 것이 좋습니다.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud 솔루션 </th> 
   <th colname="col3" class="entry"> 코드 라이브러리 </th> 
   <th colname="col4" class="entry"> 버전 요구 사항 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b><span class="keyword"></span> Experience Cloud ID 서비스</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 이상 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p><a href="https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=ko-KR" format="https" scope="external">JavaScript용 AppMeasurement</a>를 참조하십시오. </p> </td> 
   <td colname="col4"> <p>1.6.4 이상 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>참고:<span class="keyword"> Analytics</span> s_code 버전 H.27은 ID 서비스 버전 1.6.0 릴리스에서 더 이상 지원되지 않습니다. 코드를 AppMeasurement 최신 버전으로 업그레이드하십시오. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>비디오 하트비트 </p> <p><a href="https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=ko-KR" format="https" scope="external">JavaScript용 비디오 하트비트 2.x</a>를 참조하십시오. </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=ko-KR" format="https" scope="external">DIL(데이터 통합 라이브러리)</a>를 참조하십시오. </p> </td> 
   <td colname="col4"> <p>5.0 </p></td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p><a href="https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/mbox-implement/mbox-technical.html?lang=ko-KR" format="https" scope="external">mbox 코드</a>를 참조하십시오. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p><a href="https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/at-js/how-atjs-works.html?lang=ko-KR" format="https" scope="external">at.js 구현</a>을 참조하십시오. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Android 및 iOS용 SDK 요구 사항 {#section-73b2446fba8e463888642c7d7dfd94f1}

최소한으로, ID 서비스에는 아래에 나열된 SDK 버전이 필요합니다.

* Android: 4.11.0
* iOS: 4.11.0

>[!TIP]
>
>필요한 최소 코드 버전보다 최신 코드 버전을 사용하는 것이 좋습니다.

ID 서비스에 대해 SDK 코드를 활성화해야 합니다. [Adobe Mobile Services](https://mobilemarketing.adobe.com/) 계정의 각 앱에 대한 최신 SDK 코드를 활성화하고 다운로드합니다. 다음도 참조하십시오.

* [SDK 방문자 ID 서비스 옵션 구성](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=ko-KR)
* [Android SDK 메서드](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=ko-KR)
* [iOS SKD 메서드](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=ko-KR)

>[!MORELIKETHIS]
>
>* [코드 라이브러리](../library/library.md#concept-ff27497375644a898d47984aefb21c97)

