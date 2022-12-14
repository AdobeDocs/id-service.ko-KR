---
description: Experience Cloud ID 서비스는 Experience Cloud 응용 프로그램 및 서비스에 대한 공통 ID 프레임워크를 활성화합니다. 이 서비스는 ECID(Experience Cloud ID)라고 하는 고유한 영구 ID를 사이트 방문자에게 할당하여 작동합니다.
keywords: ID 서비스; ID 서비스 Experience Cloud ID 서비스
title: Experience Cloud ID 서비스
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 48%

---

# Adobe Experience Cloud ID 서비스 {#experience-cloud-id-service}

Experience Cloud ID 서비스는 Experience Cloud 응용 프로그램 및 서비스에 대한 공통 ID 프레임워크를 활성화합니다. 이 서비스는 ECID(Experience Cloud ID)라고 하는 고유한 영구 ID를 사이트 방문자에게 할당하여 작동합니다.

## ID의 주요 엔티티 이해

Adobe이 방문자를 고유하게 식별하고 ID 정보를 해결하는 데 어떻게 도움이 되는지 더 잘 이해하려면 아래 분류를 수행하십시오.

* **Experience Cloud ID 서비스**: Experience Cloud Identity 서비스 **는 ECID(Experience Cloud ID) 설정을 담당합니다**. 자세한 내용은 [Experience Cloud ID 서비스 개요](./introduction/overview.md).
* **Experience Cloud ID(ECID)**: ECID는 사용자와 장치를 식별하기 위해 Adobe Experience Platform 및 Adobe Experience Cloud 애플리케이션에서 사용하는 공유 ID 네임스페이스입니다. ECID에 대한 자세한 내용은 [ECID 개요](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html).
* **Experience Platform ID 서비스**: Experience Platform ID 서비스는 장치 및 시스템 전반에서 ID를 브리징하여 고객 및 고객 행동에 대한 포괄적인 보기를 제공합니다. 자세한 내용은 [Experience Platform ID 서비스 개요](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html).

<!-- The Adobe Experience Cloud Identity Service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud. It can replace ID generation code for Experience Cloud solutions and services. -->

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>시작하기</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> 개요 </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local">Experience Cloud ID 서비스 요구 사항</a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lank=ko-KR" format="html" scope="external"> Platform 태그를 사용한 표준 구현 </a> </li> 
     </ul> </p> <p><b>Experience Cloud ID Javascript 라이브러리</b> </p> <p>Experience Cloud ID 서비스에 대한 JavaScript는 <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a>에 있습니다. </p> <p> <b>새 항목 또는 중요 항목</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> 옵트인 서비스</a>입니다 </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> FAQ </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
     <!-- 
     <p> <b>Announcements:</b> </p> 
     <p> <p>Important:  ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release. </p> </p> 
     --> </td> 
   <td colname="col2"> <p> <b>릴리스 정보</b> </p> <p><b>버전 4.4</b> 2019년 7월 17일 릴리스에는 고객 ID 또는 이메일 주소에서 전달하고 해시된 ID 밖으로 전달할 수 있는 <a href="reference/hashing-support.md" format="dita" scope="local">SHA-256 해시 알고리즘</a>에 대한 지원이 포함되어 있습니다.</p><p><b>버전 4.0</b> 2019년 2월 12일 릴리스에는 사이트를 방문할 때 사용자의 디바이스 또는 브라우저에 쿠키 배치 가능 여부를 식별하는 데 사용되는 <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">옵트인 서비스</a>가 포함되어 있습니다. </p> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> 새 기능 및 수정 사항에 대해서는 최신 <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=ko-KR" format="https" scope="external">Experience Cloud 릴리스 정보</a>를 참조하십시오. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">이전 릴리스에 대해서는 <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=en" format="html" scope="external">이전 릴리스 정보</a>를 참조하십시오. </li> 
     </ul> </p> <p> <b>Experience Cloud 리소스</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="https://www.adobe.com/kr/privacy.html" format="http" scope="external"> Adobe 개인정보 보호 센터</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="https://experienceleague.adobe.com/docs/home.html?lang=ko-KR" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/kr/learning.html?promoid=KAUDK" scope="external" format="http"> Adobe 교육 및 튜토리얼</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://helpx.adobe.com/kr/support/experience-cloud.html" scope="external" format="https"> 제품 설명서 홈</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
