---
description: 이러한 예제에서는 직접 통합 및 ECID와 관련된 2가지 공통 사용 사례를 다룹니다. MID는 사이트 방문자를 위한 고유하고 영구적인 ID입니다.
keywords: 방문자 ID 서비스
title: 직접 통합 사용 사례
exl-id: f2a55b90-8307-4242-b20a-6a3c367a251b
TQID: https://experienceleague.adobe.com/1vfYQsSZiqM3SrnP0lmSrZEWpAMsbwVK8sR0MNitetQ
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 489
ht-degree: 53%

---

# 직접 통합 사용 사례 {#direct-integration-use-cases}

이러한 예제에서는 직접 통합 및 ECID(MID라고도 함)와 관련된 2가지 공통 사용 사례를 다룹니다. 이 ID는 사이트 방문자의 고유한 영구 ID입니다.

>[!TIP]
>
>* [코드 구문 및 변수](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9)를 검토하고 이해한 후에 사용 사례로 이동합니다.
>* MID에 대한 자세한 내용은 [쿠키 및 방문자 ID 서비스](../introduction/cookies.md)를 참조하십시오.
>

## 사용 사례 1: ECID가 있지만 내 방문자 ID를 전달하고 인증 상태를 설정하려고 함 {#section-a67d89a343754d1286d03cf08d34b806}

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
   <td colname="col2"> <p>이 사용 사례는 다음을 가정합니다. </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">사이트 방문자를 위한 MID가 있습니다. 이 ID를 1234라고 하겠습니다. </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">고유 ID로 이 방문자를 알 수 있습니다. 이 ID를 9876이라고 하겠습니다. </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">MID(1234)를 자신의 고유 ID(9876)에 연결하려고 합니다. </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>(선택 사항)</i> 이 방문자에 대한 인증 상태를 설정하려고 합니다. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>작업</b> </p> </td> 
   <td colname="col2"> <p>이러한 조건이 주어지면 다음을 포함하는 방문자 ID 서비스를 호출합니다. </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">MID(1234)입니다. </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">데이터 공급자 ID입니다. 회사에 할당된 고유 ID입니다. 이 ID를 4444라고 하겠습니다. </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">방문자의 ID(9876)입니다. </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>(선택 사항)</i> 이 방문자의 인증 상태를 정의하는 상태 ID입니다. </li> 
    </ul> <p>또한 <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> 직접 통합 안내서</a>에 나열된 다른 매개 변수가 있는 경우(예: <span class="codeph"> d_blob</span> 또는 <span class="codeph"> dcs_region</span> 등) 그것도 전달해도 됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>솔루션 및 코드 샘플</b> </p> </td> 
   <td colname="col2"> <p>다음과 같이 방문자 ID 서비스에 대한 호출 형식을 지정합니다. </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>샘플 호출에 다음을 포함하는 방법을 참고하십시오. </p> 
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
   <td colname="col2"> <p>이 사용 사례는 다음을 가정합니다. </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">사이트 방문자를 위한 MID가 없습니다. </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">방문자 ID 서비스에서 MID를 요청해야 합니다. </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41"><a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local"> IMS 조직 ID</a>을(를) 알고 있습니다. 이 ID를 5555라고 하겠습니다. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>작업</b> </p> </td> 
   <td colname="col2"> <p>이러한 조건이 주어지면 IMS 조직 ID를 포함하는 방문자 ID 서비스를 호출합니다. </p> <p>또한 <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> 직접 통합 안내서</a>에 나열된 다른 매개 변수가 있는 경우(예: <span class="codeph"> d_blob</span> 또는 <span class="codeph"> dcs_region</span> 등) 그것도 전달해도 됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>솔루션 및 코드 샘플</b> </p> </td> 
   <td colname="col2"> <p>다음과 같이 방문자 ID 서비스에 대한 호출 형식을 지정합니다. </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>샘플 호출에 IMS 조직 ID, <span class="codeph">d_orgid=5555</span>을(를) 포함하는 방법을 참고하십시오. 이 방문자에 대한 ECID가 반환됩니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

