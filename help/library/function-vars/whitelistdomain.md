---
description: 이러한 구성을 사용하면 iFrame 및 상위 페이지에 구현된 ID 서비스 코드의 다른 인스턴스가 서로 통신할 수 있습니다. 상위 페이지/도메인을 제어할 수 있거나 제어할 수 없고 제어하는 도메인의 iFrame에서 ID 서비스 코드가 로드되는 2개의 특정 사용 사례와 관련된 문제를 해결하는 데 도움이 되도록 설계되었습니다. VisitorAPI.js 코드 버전 2.2 이상에서 사용할 수 있습니다.
keywords: ID 서비스
title: whitelistParentDomain 및 whitelistIframeDomains
exl-id: 0ed1da79-7129-4f5f-b7ad-901348a13866
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 98%

---

# whitelistParentDomain 및 whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

이러한 구성을 사용하면 iFrame 및 상위 페이지에 구현된 ID 서비스 코드의 다른 인스턴스가 서로 통신할 수 있습니다. 상위 페이지/도메인을 제어할 수 있거나 제어할 수 없고 제어하는 도메인의 iFrame에서 ID 서비스 코드가 로드되는 2개의 특정 사용 사례와 관련된 문제를 해결하는 데 도움이 되도록 설계되었습니다. VisitorAPI.js 코드 버전 2.2 이상에서 사용할 수 있습니다.

내용:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local"> 구문 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> 코드 샘플 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> 사용 사례 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> 구성 안전 및 보안 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> 지원되는 방문자 API 메서드 </a> </li> 
</ul>

## 구문 {#section-f645198bbaba4fba8961acb6e88d1470}

이 코드를 사용하는 경우 두 구성 요소가 모두 필요합니다.

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 구성 구문 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistParentDomain: "<span class="varname"> 상위 페이지의 도메인 이름 </span>" </span> </p> </td> 
   <td colname="col2"> <p>문자열로 전달된 단일 도메인 이름을 허용합니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistIframeDomains: [ <span class="varname"> "iFrame 도메인","iFrame 도메인","iFrame 도메인" </span>] </span> </p> </td> 
   <td colname="col2"> <p>배열로 전달된 하나 이상의 iFrame 도메인 이름을 허용합니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

## 코드 샘플 {#section-09d0049fe88a473baa69d404c50bf8ae}

구성된 [!UICONTROL ID 서비스] 코드는 이 예제와 유사할 수 있습니다.

```js
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
 ... 
 //Add parent page domain name and iFrame domain names 
 whitelistParentDomain: "parentpageA.com", 
 whitelistIframeDomains: ["iFrameDomain1.com","iFrameDomain2.com"], 
 ... 
 } 
);
```

## 사용 사례 {#section-fc2eeb93546b406fae3b102dbcd11de7}

이러한 구성은 브라우저가 서드파티 쿠키를 차단하거나 다음 조건 중 하나가 적용되는 경우 ID 서비스 쿠키를 설정하고 방문자 ID를 할당하는 문제를 해결하는 데 도움이 됩니다.

* 상위 페이지/도메인을 제어하거나 제어하지 않습니다.
* ID 서비스 코드가 상위 페이지에 설치되어 있지 않지만 iFrame에서 구현됩니다.

>[!TIP]
>
>iFrame에서 [비디오 하트비트](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=ko-KR)를 사용하여 비디오를 제공할 때 이러한 구성을 구현할 수도 있습니다. 비디오 하트비트가 올바르게 작동하려면 ID 서비스 ID(MID)가 필요합니다.

**사용 사례 1: 브라우저가 서드파티 쿠키를 차단하며 ID 서비스가 iFrame 및 상위 페이지에 구현됨**

<table id="table_B479AA96DBE64685A253A6DF98D81B31"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 사용 사례 요소 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>조건</b> </p> </td> 
   <td colname="col2"> <p>이 사용 사례에는 다음 조건이 포함됩니다. </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">회사 A는 홈 페이지에서 ID 서비스를 구현합니다. </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">회사 A는 홈 페이지의 iFrame에서 ID 서비스를 구현합니다. </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">회사 A는 상위 페이지와 iFrame을 소유하며 두 위치에서 ID 서비스를 구현했습니다. </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">고객은 서드파티 쿠키를 차단하는 브라우저에서 상위 페이지를 로드합니다. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>결과</b> </p> </td> 
   <td colname="col2"> <p>해당 조건에서 ID 서비스는: </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">상위 페이지에서 올바르게 작동합니다. AMCV 쿠키를 요청 및 설정하고 사이트 방문자에게 고유 ID를 할당합니다. </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">iFrame에서 작동하지 않습니다. 이는 브라우저가 iFrame을 서드파티 도메인으로 보고 ID 서비스가 AMCV 쿠키를 설정하지 못하도록 하기 때문입니다. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>솔루션</b> </p> </td> 
   <td colname="col2"> <p>이러한 화이트리스트 구성을 사용하여 iFrame에서 ID 서비스 <span class="codeph">Visitor.getInstance</span> 함수를 수정합니다. 코드에서 상위 및 하위 도메인을 지정합니다. 이러한 구성을 사용하여 iFrame의 ID 서비스 코드가 상위 페이지의 ID 서비스 코드에서 방문자 ID를 확인할 수 있습니다. </p> <p>iFrame의 ID 서비스 코드가 응답 상위 페이지를 수신하지 못하면 이러한 구성은 로컬 방문자 ID를 생성합니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

**사용 사례 2: 제어하지 않거나 ID 서비스를 사용하지 않는 상위 페이지에 포함된 iFrame에서 ID 요청**

<table id="table_1F21710F9D5F493BA6BA5974F2966DF4"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 사용 사례 요소 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>조건</b> </p> </td> 
   <td colname="col2"> <p>이 사용 사례에는 다음 조건이 포함됩니다. </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">회사 A는 ID 서비스를 사용하지 않습니다. </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">회사 A는 페이지에 iFrame을 로드합니다. 이 iFrame은 회사 B가 소유하고 회사 A가 아닌 별도의 도메인에 로드됩니다. </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">브라우저는 서드파티 쿠키를 차단합니다. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>결과</b> </p> </td> 
   <td colname="col2"> <p>해당 조건에서 ID 서비스는: </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">iFrame에서 작동하지 않습니다. 이는 브라우저가 iFrame을 서드파티 도메인으로 보고 ID 서비스가 AMCV 쿠키를 설정하지 못하도록 하기 때문입니다. </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">회사 A가 이 서비스를 사용하지 않으므로 상위 페이지에서 방문자 ID를 가져올 수 없습니다. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>솔루션</b> </p> </td> 
   <td colname="col2"> <p>이러한 화이트리스트 구성을 사용하여 iFrame에서 ID 서비스 <span class="codeph">Visitor.getInstance</span> 함수를 수정합니다. 코드에서 상위 및 하위 도메인을 지정합니다. 이러한 구성을 사용하여 iFrame의 ID 서비스 코드가 상위 페이지의 ID 서비스 코드에서 방문자 ID를 확인할 수 있습니다. </p> <p>iFrame의 ID 서비스 코드가 응답 상위 페이지를 수신하지 못하면 이러한 구성은 로컬 방문자 ID를 생성합니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

## 구성 안전 및 보안 {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

다음 이유로 이러한 구성을 안전하게 구현할 수 있습니다.

* 상위 도메인 및 iFrame 도메인에 구현된 ID 서비스는 동일한 조직 ID를 사용해야 합니다. 상위 또는 iFrame의 조직 ID가 다른 경우 이러한 허용 목록 구성이 작동하지 않습니다.
* 이러한 구성은 코드에 지정된 도메인 및 iFrame과만 통신합니다.
* iFrame과 상위 페이지 간의 통신은 특정 형식을 따릅니다. 상위 페이지의 ID 서비스가 예상 형식의 요청을 수신하지 못하면 이 공유 프로세스가 실패합니다.

## 지원되는 방문자 API 메서드 {#section-30c6a9f4dcdc4265a1149260b97cc057}

이러한 허용 목록 구성을 구현할 때 ID 서비스는 제한된 공개 API 메서드 집합을 지원합니다. 지원되는 방법은 위에서 설명한 사용 사례 시나리오에 따라 다릅니다.

<table id="table_0FF9E529FD1C43A8A3B2B0D789C8E83C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 사용 사례 </th> 
   <th colname="col2" class="entry"> 지원되는 메서드 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>사례 1</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_99FAC8608F4C4B39805EEAA6297DB771"> 
      <li id="li_B13F6C4119F44F17963794B1E2046B1F"> <span class="codeph"> getMarketingCloudID </span> </li> 
      <li id="li_9C1B5C00A17F467CAB7EFE5F0D040777"> <span class="codeph"> getAudienceManagerLocationHint </span> </li> 
      <li id="li_30D4608F4C3849659FCBA97D88A10F0C"> <span class="codeph"> getAudienceManagerBlob </span> </li> 
      <li id="li_BA359596C80147EEA89CABCE83F123CA"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_26774089B6854CD6A3216043B6EEA01B"> <span class="codeph"> getCustomerIDs </span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>사례 2</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_CCAD7E362E7F4DAB9D5C3E166EEE6BDD"> 
      <li id="li_1F0B006BAD044ECBA5604625DE411E84"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_C6022223C8314B9C923202207C7472EA"> <span class="codeph"> getMarketingCloudVisitorID </span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
