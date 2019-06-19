---
description: 2017년 Experience Cloud ID 서비스의 기능 릴리스, 업데이트 또는 변경 사항입니다.
keywords: ID 서비스
seo-description: 2017년 Experience Cloud ID 서비스의 기능 릴리스, 업데이트 또는 변경 사항입니다.
seo-title: 2017 릴리스 노트
title: 2017 릴리스 노트
uuid: 79452 DF 0-49 DB -42 B 8-96 FE -01 AA 7629 FBB 5
translation-type: tm+mt
source-git-commit: 4dc668afd37cd1d6f9104adb1b102f1dd4c5746e

---


# 2017 릴리스 노트 {#release-notes}

2017년 Experience Cloud ID 서비스의 기능 릴리스, 업데이트 또는 변경 사항입니다.

이러한 변경 사항은 [Experience Cloud 릴리스 노트](https://marketing.adobe.com/resources/help/en_US/whatsnew/)에도 캡처되어 있습니다. 이전 ID 서비스 릴리스 정보에 대해서는 [이전 릴리스 정보](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html) 또는 이 페이지 맨 아래에 있는 링크를 참조하십시오.

>[!NOTE]
>
>2017 년 3 월, 4 월, 5 월 및 10 월에 고객용 릴리스 노트나 코드가 변경되지는 않습니다. 이러한 달은 ID 서비스 코드가 v2.1에서 변경되지 않고 그대로 유지되었습니다.

## 버전 2.5 {#section-27b441509124493f80984ed09bd9e88b}

2017년 9월

<!--
<p>
<note type="important">
ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release.
</note> </p>
-->

<table id="table_FD24C06C7B3547C3A7673C46B1852A35"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 기능 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> getVisitorValues</span> </p> </td> 
   <td colname="col2"> <p>Analytics에 대한 식별자, 즉 ID 서비스, 데이터 컬렉션 옵트아웃, 지리적 위치 및 메타데이터 "blob" 콘텐츠를 기본적으로 반환하는 비동기 API입니다. 또한 선택적 <span class="codeph">visitor.FIELDS</span> 열거와 함께 반환할 ID를 제어할 수 있습니다. 자세한 내용은 <a href="../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**버그 수정 및 기타 변경**

* 해당 브라우저에서 뒤로 버튼을 클릭할 때 ID 서비스가 오류를 발생시키는 Chrome 관련 버그가 수정되었습니다.
* 이제 ID 서비스는 이벤트 호출 응답의 지역 ID가 변경되면 ID 동기화를 다시 시작합니다.
* 새 설명서, [컨텐츠 보안 정책 및 Experience Cloud ID 서비스](/help/mcvid-reference/mcvid-csp.md#concept-968c423a7392479db0a0d821ae9783e3)가 추가되었습니다. 이 설명서는 ID 서비스에서 사용하는 Adobe 도메인에 대한 호출을 화이트리스트에 작성하는 방법을 설명합니다.

## 버전 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

2017년 8월

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 기능 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>ID 서비스에서 Adobe Experience Cloud Device Co-op로 데이터를 전송하거나 전송하지 않는지 여부를 결정하는 선택적 부울 구성입니다. <a href="../mcvid-library/mcvid-function-vars/mcvid-coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local">isCoopSafe</a>를 참조하십시오. </p> </td> 
  </tr> 
 </tbody> 
</table>

**개정된 설명서**

다른 [FAQ](/help/mcvid-faq-intro/mcvid-faq-intro.md)[!DNL Experience Cloud] 를 참조하십시오.

## 버전 2.3 {#section-ae7b1cb1e52e4ca5a46b453a3ba1f571}

2017년 7월

<table id="table_1448040D09B94A74883A694FCF91EB33"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 기능 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> sdidParamExpiry</span> </p> </td> 
   <td colname="col2"> <p>이 기능을 <span class="codeph">Visitor.getInstance</span> 함수에 추가하면, 해당 ID를 한 페이지에서 다른 페이지로 전달할 때 기본 SDID(Supplemental Data ID) 만료일 간격을 무시할 수 있습니다. <span class="codeph">sdidParamExpiry</span>는 <span class="codeph">appendSupplimentalDataTo</span> 도우미 함수와 함께 사용합니다. <a href="../mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local">sdidParamExpiry</a>를 참조하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>이 기능은 주로 A4T 고객이 단일 페이지 사이트/화면 또는 앱에서 ID 작업 관련 문제를 해결할 수 있도록 설계되었습니다. 자세한 내용은 <a href="../mcvid-library/mcvid-get-set/mcvid-resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local"> resetState</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**버그 수정 및 기타 변경**

* ID 서비스와 Target이 Internet Explorer에서 함께 작동하지 못하게 하는 VisitorAPI.js v2.2의 버그를 수정했습니다.
* ID 서비스에서 대상 게시 iFrame에 데이터를 보내는 방법을 개선하는 데 도움이 되도록 코드를 수정했습니다. 이렇게 하면 CPU 사용량이 줄어듭니다.

## 버전 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

릴리스 날짜: 2017 년 6 월

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 기능 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain 및 whitelistIframeDomains </a> </p> </td> 
   <td colname="col2"> <p>이러한 구성을 사용하면 iFrame 및 상위 페이지에 구현된 ID 서비스 코드의 다른 인스턴스가 서로 정보를 교환할 수 있습니다. 이러한 구성은 상위 페이지/도메인을 제어할 수 있거나 제어할 수 없고 사용자가 제어하는 도메인의 iFrame에서 ID 서비스 코드가 로드되는 2가지 특정 사용 사례의 문제를 해결하는 데 도움이 되도록 설계되어 있으며,  </p> </td> 
  </tr> 
 </tbody> 
</table>

## 5월 설명서 업데이트 {#section-1d36b91bb7a140ce8a145251ffac9f2f}

<table id="table_CD031A716A694E8FA89695C9B614BC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 주제 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-faq-intro/mcvid-faq.md" format="dita" scope="local"> FAQ </a> </p> </td> 
   <td colname="col2"> <p><span class="keyword">Analytics</span> 섹션이 추적 서버 정보를 찾는 방법에 대한 정보로 업데이트되었습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

## 4월 설명서 업데이트 {#section-df3e5a85448c4001a6791517520ae06e}

<table id="table_ADC2636240654C69B8B6A45849024540"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 주제 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> audienceManagerServer 및 audienceManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p><span class="codeph">demdex.net</span> 도메인에 대한 호출을 설명하는 <span class="keyword">Audience Manager</span> 설명서에 대한 링크가 추가되었습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md" format="dita" scope="local"> ID 동기화 및 일치율 이해하기</a>를 참조하십시오  </p> </td> 
   <td colname="col2"> <p><span class="keyword">Media Optimizer</span> 섹션이 <span class="codeph">cm.eversttech.net</span>에 대한 호출을 설명하는 내용으로 수정되었습니다. ID 서비스에서 <span class="keyword">Media Optimizer</span>를 사용하여 수행하는 자동 ID 동기화입니다. 이 기능은 2017년 1월에 출시되었습니다. 아래의 <a href="../mcvid-release-notes/mcvid-notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local">버전 2.0</a>을 참조하십시오. </p> </td> 
  </tr> 
 </tbody> 
</table>

## 버전 2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

릴리스 날짜: 2017 년 2 월

**기능**

<table id="table_1F7E1CF091604D22B1D9F3F1AE4DB2D7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 기능 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> ID 서비스 API 속성, <span class="codeph">idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>이 속성은 ID 동기화를 위해 <span class="keyword">Audience Manager</span>에서 사용하는 컨테이너 ID를 설정합니다. <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-idsyncontainerid.html" format="https" scope="external"> idSyncContainerID</a>를 참조하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ID 서비스 API 메서드, <span class="codeph"> appendSupplementalDataIDTo( <span class="varname"> URL </span>, <span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>이 공개 메서드는 <span class="wintitle">Supplemental Data ID</span>(SDID)를 쿼리 문자열 매개 변수로서 리디렉션 URL에 추가합니다. <a href="../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local"> Appendappenentaldataidto</a>를 참조하십시오. (MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**수정 사항**

ID 서비스에서 AMCV 쿠키에 저장된 ID를 사용하지 않고 ID에 대한 중복 서버 호출을 수행했던 버그를 수정했습니다. (MCID-296)

**새 설명서**

[다른 Experience Cloud 솔루션 및 서비스에서 DNS 프리페치 사용 `Learn how to use DNS prefetch to help reduce page load times.`](https://marketing.adobe.com/resources/help/en_US/mcloud/dns-prefetch.html)

## 버전 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

2017년 1월

>[!IMPORTANT]
>
>ID 서비스 코드 v 2.0는 기본적으로 ID를 Adobe Media Optimizer와 자동으로 동기화합니다. 즉, 이 페이지에서 제어되는 기존 `cm.eversttech.net`[!DNL Media Optimizer] 도메인인 페이지 호출이 표시됩니다 [!DNL Adobe]. [ID 동기화 및 일치율 이해](../mcvid-introduction/mcvid-match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab)를 참조하십시오.

**수정 사항 및 향상된 기능**

* AppMeasurement가 Analytics에 대한 호출을 추적할 수 없는 버그를 수정했습니다. (MCID-254, MCID-256, MCID-286).
* 방문자가 광고 차단기를 활성화하고 해당 차단기가 demdex.net 도메인을 제외하도록 구성된 경우 ID 서비스가 바로 실패하지 않는 버그를 수정했습니다. 대부분의 광고 차단 도구가 demdex.net 도메인을 차단하지 않기 때문에 이 버그는 거의 발생하지 않습니다. (MCID-233)
* 고객 웹사이트에서 ID 서비스 코드와 사용자 정의 스크립트 간 상호 작용에 의해 발생한 버그를 수정했습니다. 이 문제로 인해 Internet Explorer 9에 웹 페이지가 로드되지 않았습니다. (MCID-206)

## 이전 연도 {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

이전 ID 서비스 릴리스 노트입니다.
