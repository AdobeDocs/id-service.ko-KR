---
description: 옵트인 서비스를 관리하는 샘플 사용 사례 및 솔루션.
title: 옵트인 사용 사례
exl-id: 4c57685f-40b7-4af4-8527-3c2795586f0f
TQID: https://experienceleague.adobe.com/ssSKMn1pEhduempV4zjCqi4Pol1U0oEBU6l36SkUTH4
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c1579802-ddd4-4214-8a91-97b2066abe11id: c2be0313-b3ae-45e0-b454-d20bf54b23f2id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 460
ht-degree: 90%

---

# 옵트인 사용 사례 {#opt-in-use-cases}

옵트인 서비스를 관리하는 샘플 사용 사례 및 솔루션.

## 팁 및 문제 해결 {#section-5c566366410f4a8f89eca0d3f556d99f}

* 방문자 JS 초기화는 동기식이며 페이지 로드 중에 실행됩니다. 대기 시간이 긴 CMP 또는 권한 지속성과 인터페이스로 접속하는 경우 [옵트인 설정](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)에 설명된 비동기 기능을 사용하는 것이 좋습니다.
* 옵트인은 도메인별 구현입니다. 도메인 간 구현을 처리하지 않습니다.
* 특정 라이브러리에 대한 서드파티 호출을 비활성화하려면 각 라이브러리에서 해당 기본 설정을 개별적으로 구성해야 합니다.

## 옵트인 시나리오 {#section-1178053c065c430bba26f82ef383a71c}

이러한 사용 사례는 옵트인 서비스 사용에 대한 예제입니다.

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 요구 사항 </th> 
   <th colname="col2" class="entry"> 솔루션 </th> 
   <th colname="col3" class="entry"> 영향 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Analytics는 동의 전 상태에서는 수집할 수 있지만 동의를 받을 때까지 다른 모든 라이브러리를 로드할 수 없습니다 </p> </td> 
   <td colname="col2"> <p>옵트인을 사용하여 동의 전 상태에서 Analytics 범주 활성화 </p> </td> 
   <td colname="col3"> <p>Analytics는 동의 전 수집에서 ECID가 아닌 Analytics 식별자를 사용합니다. ECID가 승인되면 새 식별자가 사용되며 방문자는 활성화 및 통합에 사용할 수 있는 ECID를 받게 됩니다. </p> <p>동의 전/후 상태에서 방문자 조각화가 예상됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>자사 측정은 동의 전 상태에서 수집해도 됩니다. 다른 모든 유형의 데이터 사용은 동의를 받을 때까지 금지됩니다. </p> </td> 
   <td colname="col2"> <p>동의 전 상태에서 Analytics + ECID 라이브러리를 활성화하려면 옵트인을 사용하십시오. </p> <p>동의 전 상태에서 타사 쿠키 + ID를 차단하려면 'disablethirdpartycookies' 구성을 ECID 라이브러리에 추가합니다. </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 호출은 ECID 검색을 위해 트리거되지만 Demdex 쿠키는 없으며 다른 서드파티 쿠키 또는 ID 동기화가 존재합니다. </p> <p>일관된 방문자를 Analytics에 대한 동의 전/후 상태로 유지합니다. 동의 전 상태의 수집은 동의 후 데이터 수집과 연결됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>동의 전 상태에서는 자사 측정 및 타겟팅이 허용됩니다. 다른 모든 유형의 데이터 사용은 동의를 받을 때까지 금지됩니다. </p> </td> 
   <td colname="col2"> <p>동의 전 상태에서 Analytics + ECID + Target 라이브러리를 활성화하려면 옵트인을 사용하십시오. </p> <p>사전 동의 상태에서 타사 쿠키 + ID를 차단하려면 <span class="codeph">isablethirdpartycookies</span> 구성을 ECID 라이브러리에 추가합니다. 동의 후 상태에서 플래그를 제거합니다. </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 호출은 ECID 검색을 위해 트리거되지만 Demdex 쿠키는 없으며 다른 서드파티 쿠키 또는 ID 동기화가 존재합니다. </p> <p>일관된 방문자를 자사 솔루션에 대한 동의 전/후 상태로 유지합니다. 동의 전 상태의 수집은 동의 후 데이터 수집과 연결됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>동의 전 상태에서는 쿠키를 설정할 수 없습니다. </p> </td> 
   <td colname="col2"> <p>동의를 받을 때까지 모든 라이브러리가 로드되지 않도록 차단하려면 옵트인을 사용하십시오. </p> </td> 
   <td colname="col3"> <p>구현은 예상대로 이루어지며 ECID를 포함한 모든 라이브러리는 동의 후 상태에서 올바른 시퀀스로 로드됩니다. </p> <p>추적에 동의하지 않는 고객의 데이터 손실. </p> </td> 
  </tr> 
 </tbody> 
</table>

