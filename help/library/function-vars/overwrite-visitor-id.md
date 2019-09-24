---
description: 이 속성은 한 도메인에서 다른 도메인으로 이동할 때 방문자의 Experience Cloud 및 Analytics ID를 덮어씁니다. ID를 덮어쓰려면 각 도메인에서 ID 서비스를 보유하고 구현해야 합니다. 이 코드로 사용자가 제어하지 않는 도메인에 ID를 덮어쓸 수 없습니다.
keywords: ID 서비스
seo-description: 이 속성은 한 도메인에서 다른 도메인으로 이동할 때 방문자의 Experience Cloud 및 Analytics ID를 덮어씁니다. ID를 덮어쓰려면 각 도메인에서 ID 서비스를 보유하고 구현해야 합니다. 이 코드로 사용자가 제어하지 않는 도메인에 ID를 덮어쓸 수 없습니다.
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}를 참조하십시오

이 속성은 한 도메인에서 다른 도메인으로 이동할 때 방문자의 Experience Cloud 및 Analytics ID를 덮어씁니다. ID를 덮어쓰려면 각 도메인에서 ID 서비스를 보유하고 구현해야 합니다. 이 코드로 사용자가 제어하지 않는 도메인에 ID를 덮어쓸 수 없습니다.

**구문:** `Visitor.overwriteCrossDomainMCIDAndAID: true|false`(기본값은 `false`임)

**코드 샘플**

JavaScript 코드는 다음 예와 비슷하게 보일 수 있습니다.

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**사용 사례**

사이트 방문자를 추적하기 위해 ID 서비스에서는 MID[!DNL Experience Cloud] ID(또는 MID)를 브라우저 쿠키에 작성합니다. 다음 표에는 다른 도메인의 ID 서비스에서 설정한 기존 MID를 덮어쓰려고 하는 일반적인 사용 사례가 나열 및 설명되어 있습니다.

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 사용 사례 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>다양한 도메인 랜딩 페이지에서 방문자 식별</b> </p> </td> 
   <td colname="col2"> <p>도메인 A와 B를 보유하고 있다고 가정해 보겠습니다. 이러한 경우 다음과 같은 상황에서 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>를 설정할 수 있습니다. </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">각 도메인에 자체 랜딩 페이지가 있는 경우 </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">방문자가 이미 이전에 도메인 B를 방문하여 설정된 쿠키(및 MID)를 보유하고 있는 경우 </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">방문자가 도메인 A에서 도메인 B로 오는 경우 일관되게 해당 방문자를 식별하려는 경우 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>랜딩 및 전환 페이지에서 방문자 식별</b> </p> </td> 
   <td colname="col2"> <p>도메인 A와 B를 보유하고 있다고 가정해 보겠습니다. 이러한 경우 다음과 같은 상황에서 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>를 설정할 수 있습니다. </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">도메인 A가 랜딩 페이지인 경우 </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">도메인 B가 별도의 전환, 예약 또는 기타 작업 과정 끝 페이지인 경우 </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">방문자가 이미 이전에 도메인 B를 방문하여 설정된 쿠키(및 MID)를 보유하고 있으며, 이러한 MID가 서버측 MID에 비해 바람직하지 않은 클라이언트측 MID임을 알고 있는 경우 </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">방문자가 도메인 A에서 도메인 B로 오는 경우 일관되게 해당 방문자를 식별하려는 경우 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>모바일 앱에서 웹 브라우저로 이동한 방문자 식별</b> </p> </td> 
   <td colname="col2"> <p>이러한 사용 사례는 다소 다릅니다. 여기에는 사용자가 모바일 앱에서 웹 사이트로 이동할 때 사용자를 식별하는 작업이 포함됩니다. 이 경우 방문자는 이미 모바일 앱을 통해 로컬로 설정된 MID가 있으며 웹 사이트의 쿠키에 설정된 다른 MID를 보유합니다. <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>를 설정하여 브라우저 쿠키에 설정된 MID를 모바일 앱에서 설정한 MID로 덮어쓸 수 있습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

