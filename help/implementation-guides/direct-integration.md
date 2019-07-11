---
description: 이 구현을 통해 고객은 JavaScript 또는 SDK 코드를 승인하거나 사용할 수 없는 장치에서 ID 서비스를 사용할 수 있습니다. 게임 콘솔, 스마트 TV 또는 기타 인터넷 지원 어플라이언스와 같은 장치가 여기에 포함됩니다. 구문, 코드 샘플 및 정의에 대해서는 이 섹션을 참조하십시오.
keywords: ID 서비스
seo-description: 이 구현을 통해 고객은 JavaScript 또는 SDK 코드를 승인하거나 사용할 수 없는 장치에서 ID 서비스를 사용할 수 있습니다. 게임 콘솔, 스마트 TV 또는 기타 인터넷 지원 어플라이언스와 같은 장치가 여기에 포함됩니다. 구문, 코드 샘플 및 정의에 대해서는 이 섹션을 참조하십시오.
seo-title: Experience Cloud ID 서비스와 직접 통합
title: Experience Cloud ID 서비스와 직접 통합
uuid: de502f7e-cffd-4130-b3ca-7d6b9a9caae9
translation-type: ht
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Experience Cloud ID 서비스와 직접 통합 {#direct-integration-with-the-experience-cloud-id-service}

이 구현을 통해 고객은 JavaScript 또는 SDK 코드를 승인하거나 사용할 수 없는 장치에서 ID 서비스를 사용할 수 있습니다. 게임 콘솔, 스마트 TV 또는 기타 인터넷 지원 어플라이언스와 같은 장치가 여기에 포함됩니다. 구문, 코드 샘플 및 정의에 대해서는 이 섹션을 참조하십시오.

## 구문 {#section-a4754afec5ad40b6be00d6f1011d68bb}

VisitorAPI.js 또는 SDK 코드 라이브러리를 사용할 수 없는 장치에서는 ID 서비스에 사용되는 DCS(Data Collection Server)를 직접 호출할 수 있습니다. 이렇게 하려면 `dpm.demdex.net`을 호출하고 아래 표시된 대로 요청 형식을 지정합니다. *기울임꼴*은 변수 자리 표시자를 나타냅니다.

![](assets/directSyntax.png)

이 구문 예제에서 `d_` 접두사는 호출 시 키-값 쌍을 시스템 수준 변수로 식별합니다. 상당수의 `d_` 매개 변수를 ID 서비스에 전달할 수 있지만, 위 코드에 표시된 대로 키-값 쌍에 초점을 맞추고 있습니다. 다른 변수에 대한 자세한 내용은 [DCS API 호출에 지원되는 특성]( https://marketing.adobe.com/resources/help/ko_KR/aam/dcs-keys.html)을 참조하십시오.

ID 서비스는 HTTP 및 HTTPS 호출을 지원합니다. 보안 페이지의 데이터를 전달하려면 HTTPS를 사용합니다.

## 샘플 요청 {#section-26302b8851704888b6f8e6b2071bcdb0}

요청은 아래 표시된 샘플과 유사하게 보일 수 있습니다. 긴 변수가 축소되었습니다.

![](assets/directExample.png)

## 샘플 응답 {#section-89bc103b3e9e4a8b98e74c32897b1200}

ID 서비스는 아래에 표시된 대로 JSON 개체에 데이터를 반환합니다. 응답이 다를 수 있습니다.

```js
{
     "d_mid":"12345",
     "dcs_region":"6",
     "id_sync_ttl":"604800",
     "d_blob":"wxyz5432"
}
```

## 정의된 요청 및 응답 매개 변수 {#section-4a9912b545364dc4acad4f1ea5ec641d}

**요청 매개 변수**

<table id="table_C8FFA89AB74E4E31A6926CDE5CD54217"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 매개 변수 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dpm.demdex.net</span> </p> </td> 
   <td colname="col2"> <p><span class="keyword">Adobe</span>에서 제어하는 기존 도메인입니다. <a href="https://marketing.adobe.com/resources/help/ko_KR/aam/demdex-calls.html" format="https" scope="external">Demdex 도메인에 대한 호출 이해</a>를 참조 하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_mid</span> </p> </td> 
   <td colname="col2"> <p>Experience Cloud 방문자 ID입니다. 자세한 내용은 <a href="../introduction/cookies.md" format="dita" scope="local"> 쿠키 및 ExExperience Cloud ID 서비스</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_orgid</span> </p> </td> 
   <td colname="col2"> <p>Experience Cloud 조직 ID입니다. 이 ID를 찾는 데 도움이 필요하면 <a href="../reference/requirements.md" format="dita" scope="local"> Experience Cloud ID 서비스 요구 사항</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cid</span> </p> </td> 
   <td colname="col2"> <p>DPID(데이터 제공자 ID), DPUUID(고유 사용자 ID) 및 <a href="../reference/authenticated-state.md" format="dita" scope="local"> 인증됨 상태 ID</a>를 ID 서비스에 전달하는 선택적 매개변수입니다. 코드 샘플에 표시된 대로 DPID와 DPUUID를 인쇄되지 않는 제어 문자 <span class="codeph">%01</span>로 구분합니다. </p> <p> <b>DPID 및 DPUUID</b> </p> <p><span class="codeph">d_cid</span> 매개 변수에서 관련된 각 DPID 및 DPUUID 조합을 동일한 <span class="codeph">d_cid</span> 매개 변수에 지정합니다. 이렇게 하면 단일 요청으로 여러 ID 세트를 반환할 수 있습니다. 또한 DPID, DPUUID 및 선택적 인증 플래그를 인쇄되지 않는 제어 문자 <span class="codeph">%01</span>로 구분합니다. 아래 예제에서 공급업체 및 사용자 ID는 <b>굵은</b> 텍스트로 강조 표시되어 있습니다. </p> 
    <ul id="ul_2E19D837296B40E9ACD096495CF711C5"> 
     <li id="li_5B94B057654440B99B989BA60E4ED053">구문: <span class="codeph">...d_cid=DPID%01DPUUID%01authentication state...</span> </li> 
     <li id="li_B07833EF51D54F088574B7B7F9FB841A">예: <span class="codeph">...d_cid=123%01456%011...</span> </li> 
    </ul> <p> <b>인증 상태</b> </p> <p><span class="codeph">d_cid</span> 매개 변수에서 선택적 ID입니다. 정수로 표시되며, 아래와 같이 인증 상태에 따라 사용자를 식별합니다. </p> 
    <ul id="ul_E2B36922B11C4AA2A9016B6E2DC9EDAA"> 
     <li id="li_31C018E3F9514B938C73EF40C436715F"> <span class="codeph"> 0</span>(알 수 없음) </li> 
     <li id="li_1F125C3879324C2F8EF4613C0ECB5F02"> <span class="codeph"> 1</span>(인증됨) </li> 
     <li id="li_EF6792D0115D407485079D5D7480D965"> <span class="codeph"> 2</span>(로그아웃됨) </li> 
    </ul> <p>인증 상태를 지정하려면 사용자 ID(UUID) 변수 다음에 이 플래그를 설정합니다. 인쇄되지 않는 제어 문자 <span class="codeph">%01</span>를 사용하여 UUID 및 인증 플래그를 구분합니다. 아래 예제에서 인증 ID는 <b>굵은</b> 텍스트로 강조 표시되어 있습니다. </p> <p>구문: <span class="codeph">...d_cid=DPID%01DPUUID%01authentication state</span> </p> <p>예 </p> 
    <ul id="ul_4C1054CE860A4D9C8DD85C2A8020C47F"> 
     <li id="li_AD4000BF3E0146C0BD37B1EC513EC314">알 수 없음: <span class="codeph">...d_cid=123%01456%010...</span> </li> 
     <li id="li_B037D424AADA4D41BF29381A9602AE61">인증됨: <span class="codeph">...d_cid=123%01456%011...</span> </li> 
     <li id="li_0410FCB9E60D4DD08E7898D814E1C3C9">로그아웃됨: <span class="codeph">...d_cid=123%01456%012...</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dcs_region</span> </p> </td> 
   <td colname="col2"> <p>ID 서비스는 지리적으로 분산되고 로드 분산된 시스템입니다. ID는 호출을 처리하는 데이터 센터의 영역을 식별합니다. <a href="https://marketing.adobe.com/resources/help/ko_KR/aam/dcs-regions.html" format="https" scope="external">DCS 영역 ID, 위치 및 호스트 이름</a>을 참조하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cb</span> </p> </td> 
   <td colname="col2"> <p> <i>(선택 사항)</i> 요청 본문에서 JavaScript 함수를 실행할 수 있는 콜백 매개 변수입니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_blob</span> </p> </td> 
   <td colname="col2"> <p>JavaScript 메타데이터의 암호화된 청크입니다. 크기 제한은 Blob을 512바이트 이하로 제한합니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_ver</span> </p> </td> 
   <td colname="col2"> <p>필수 여부. API 버전 번호를 설정합니다. <span class="codeph">d_ver=2</span>로 설정된 대로 둡니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

**응답 매개 변수**

일부 응답 매개 변수는 요청에 포함되며, 위 섹션에서 정의되어 있습니다.

<table id="table_58D0E8876DDC4A81B1F24F845E87EC18"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 매개 변수 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id_sync_ttl</span> </p> </td> 
   <td colname="col2"> <p>초 단위로 지정된 재동기화 간격입니다. 기본 간격은 604,800초(7일)입니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

