---
description: 'Experience Platform Identity Service는 Experience Cloud의 모든 솔루션에서 방문자를 식별하는 범용 영구 ID를 제공합니다. '
keywords: ID 서비스
seo-description: Adobe Experience Platform Identity Service (ID 서비스) 는 Experience Cloud의 모든 솔루션에서 방문자를 식별하는 범용 영구 ID를 제공합니다. 이 ID는 Analytics, Audience Manager, Target 및 기타 Experience Cloud 솔루션이나 기능과 같은 서비스에 대한 ID 생성 코드를 대체할 수 있습니다.
seo-title: Experience Platform Identity Service
title: Experience Platform Identity Service
uuid: b68194b5-e549-4f6f-bfaf-7744926aeaac
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Adobe Experience Platform Identity Service {#experience-cloud-id-service}

Adobe Experience Platform Identity Service (ID 서비스) 는 Experience Cloud의 모든 솔루션에서 방문자를 식별하는 범용 영구 ID를 제공합니다. 이 ID는 Analytics, Audience Manager, Target 및 기타 Experience Cloud 솔루션이나 기능과 같은 서비스에 대한 ID 생성 코드를 대체할 수 있습니다.

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>시작하기</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> 개요 </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> 경험 플랫폼 ID 서비스 요구 사항 </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> DTM을 사용한 표준 구현</a>을 참조하십시오  </li> 
     </ul> </p> <p><b>Experience Cloud ID Javascript 라이브러리</b> </p> <p>JavaScript for the Experience Platform Identity Service is located at: <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external"> https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>새 항목 또는 중요 항목</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> 옵트인 서비스</a>입니다 </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> FAQ </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
    <draft-comment> 
     <p> <b>공지:</b> </p> 
     <p> <p>중요: Internet Explorer 6, 7 및 8에 대한 ID 서비스는 더 이상 지원되지 않으며 이후 릴리스에서 중단됩니다. </p> </p> 
    </draft-comment> </td> 
   <td colname="col2"> <p> <b>릴리스 노트</b> </p> <p><b>버전 4.0</b> 2019년 2월 12일 릴리스에는 사이트를 방문할 때 사용자의 장치 또는 브라우저에 쿠키 배치 가능 여부를 식별하는 데 사용되는 <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">옵트인 서비스</a>가 포함되어 있습니다. </p> <p>2018년 1월 18일 릴리스에는 3.0.0 JavaScript 업데이트 및 API 메서드에 대한 업데이트가 포함되어 있습니다. 자세한 내용은 <a href="library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414" format="dita" scope="local"> disableIdSyncs</a> 및 <a href="library/function-vars/disable-cookies.md#reference-2dd2d60d12f34f0b98bbb5606b3734cc" format="dita" scope="local"> disableThirdPartyCookies</a>를 참조하십시오. </p> 
    <draft-comment> 
     <p>2017년 10월 릴리스에는 ID 서비스에 대한 코드 변경 또는 업데이트가 포함되어 있지 않습니다. ID 서비스 코드는 v2.5에서 그대로 유지됩니다. </p> 
    </draft-comment> 
    <draft-comment> 
     <p> 2017년 9월 릴리스는 ID 서비스 코드를 v2.5로 늘립니다. </p> 
    </draft-comment> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> 새 기능 및 수정 사항에 대해서는 최신 <a href="https://marketing.adobe.com/resources/help/en_US/whatsnew/" format="https" scope="external">Experience Cloud 릴리스 노트</a>를 참조하십시오. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">이전 릴리스에 대해서는 <a href="https://marketing-stage.adobe.com/resources/help/en_US/whatsnew/c_legacy_releases.html" format="html" scope="external">이전 릴리스 노트</a>를 참조하십시오. </li> 
     </ul> </p> <p> <b>Experience Cloud 리소스</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/privacy.html" format="http" scope="external"> Adobe 개인 정보 보호 센터</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="http://www.adobe.com/marketing-cloud.html" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/learning.html?promoid=KAUDK" scope="external" format="http"> Adobe 교육 및 자습서</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://marketing.adobe.com/resources/help/en_US/home/index.html" scope="external" format="https"> 제품 설명서 홈</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

