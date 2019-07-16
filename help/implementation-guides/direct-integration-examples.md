---
description: 이러한 예제에서는 직접 통합 및 Experience Cloud ID(MID)와 관련된 2가지 공통 사용 사례를 다룹니다. MID는 사이트 방문자의 고유한 영구 ID입니다.
keywords: ID 서비스
seo-description: 이러한 예제에서는 직접 통합 및 Experience Cloud ID(MID)와 관련된 2가지 공통 사용 사례를 다룹니다. MID는 사이트 방문자의 고유한 영구 ID입니다.
seo-title: 직접 통합 사용 사례
title: 직접 통합 사용 사례
uuid: 6de1eb8b-4783-4545-8a64-ab6b9ef93432
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# 직접 통합 사용 사례 {#direct-integration-use-cases}

이러한 예제에서는 직접 통합 및 Experience Cloud ID(MID)와 관련된 2가지 공통 사용 사례를 다룹니다. MID는 사이트 방문자의 고유한 영구 ID입니다.

>[!TIP]
>
>* [코드 구문 및 변수](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9)를 검토하고 이해한 후에 사용 사례로 이동합니다.
>* For more information about the MID, see [Cookies and the Experience Platform Identity Service](../introduction/cookies.md).
>



## 사용 사례 1: MID가 있지만 내 방문자 ID를 전달하고 인증 상태를 설정하려고 함 {#section-a67d89a343754d1286d03cf08d34b806}

<table id="table_DA8840FCB51541109FE6DF20430E8924"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 사용 사례 요소 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>조건</b> </p> </td> 
   <td colname="col2"> <p>이 사용 사례에서는 다음과 같이 가정합니다. </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">사이트 방문자에 대한 MID를 갖고 있습니다. 이 ID를 1234라고 하겠습니다. </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">고유한 ID로 이 방문자를 식별합니다. 이 ID를 9876라고 하겠습니다. </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">MID(1234)를 고유한 고유 ID(9876)에 연결하려고 합니다. </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>(선택 사항)</i> 이 방문자에 대한 인증 상태를 설정하려고 합니다. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>작업</b> </p> </td> 
   <td colname="col2"> <p>이러한 조건이 있는 경우 다음을 포함하는 ID 서비스를 호출합니다. </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">MID(1234). </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">데이터 제공업체 ID. 회사에 지정된 고유 ID입니다. 이 ID를 4444라고 하겠습니다. </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">방문자 ID(9876). </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>(선택 사항)</i> 이 방문자에 대한 인증 상태를 정의할 상태 ID. </li> 
    </ul> <p>그리고 <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local">직접 통합 가이드</a>에 나열된 다른 매개 변수가 있는 경우(예: <span class="codeph">d_blob</span> 또는 <span class="codeph">dcs_region</span> 등) 그러한 매개 변수를 전달해도 됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>솔루션 및 코드 샘플</b> </p> </td> 
   <td colname="col2"> <p>ID 서비스에 대한 호출 형식을 다음과 같이 지정합니다. </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>샘플 호출에 다음을 포함하는 방법을 참고하십시오. </p> 
    <ul id="ul_0667FBFD8D3C46BDBD027F484691EC97"> 
     <li id="li_FAB1FAE703DB48D1A32EE72684028964">MID: <span class="codeph">d_mid=1234</span> </li> 
     <li id="li_C97B74FF444F4BB4B4A5CB1CBBE52249">방문자의 고유 ID에 연결된 MID: <span class="codeph">d_mid=1234&amp;d_cid=4444%019876%011</span> </li> 
     <li id="li_D428DBF765234DD78DDF152C5EE8AB69">인증 상태 ID: <span class="codeph">...d_cid=4444%019876%011</span>(힌트: 마지막 숫자). </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 사용 사례 2: MID가 없으므로 생성해야 함 {#section-8e81291f8b684de8b88fae4002ae0029}

<table id="table_666A92693F8A413096DF6A64770C1141"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 사용 사례 요소 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>조건</b> </p> </td> 
   <td colname="col2"> <p>이 사용 사례에서는 다음과 같이 가정합니다. </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">사이트 방문자에 대한 MID가 없습니다. </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">ID 서비스에서 MID를 요청해야 합니다. </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41"><a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local">조직 ID</a>를 알고 있습니다. 이 5555를 호출해 보겠습니다. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>작업</b> </p> </td> 
   <td colname="col2"> <p>이러한 조건이 있는 경우 조직 ID를 포함하는 ID 서비스를 호출합니다. </p> <p>그리고 <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local">직접 통합 가이드</a>에 나열된 다른 매개 변수가 있는 경우(예: <span class="codeph">d_blob</span> 또는 <span class="codeph">dcs_region</span> 등) 그러한 매개 변수를 전달해도 됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>솔루션 및 코드 샘플</b> </p> </td> 
   <td colname="col2"> <p>ID 서비스에 대한 호출 형식을 다음과 같이 지정합니다. </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>샘플 호출에 조직 ID, <span class="codeph">d_orgid=5555</span>를 포함하는 방법을 확인합니다. 이 방문자에 대한 <span class="keyword">Experience Cloud</span> ID가 반환됩니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

