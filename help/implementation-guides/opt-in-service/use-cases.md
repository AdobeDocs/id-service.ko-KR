---
description: 옵트인 서비스를 관리하는 샘플 사용 사례 및 솔루션.
seo-description: 옵트인 서비스를 관리하는 샘플 사용 사례 및 솔루션.
seo-title: 옵트인 사용 사례
title: 옵트인 사용 사례
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 16%

---


# 옵트인 사용 사례 {#opt-in-use-cases}

옵트인 서비스를 관리하는 샘플 사용 사례 및 솔루션.

## 팁 및 문제 해결 {#section-5c566366410f4a8f89eca0d3f556d99f}

* 방문자 JS 초기화는 동기적이며 페이지 로드 중에 실행됩니다. 대기 시간이 높은 CMP 또는 권한 지속성과 상호 작용하는 경우 옵트인 설정에 설명된 비동기 기능을 사용하는 것이 [좋습니다](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047).
* 옵트인은 도메인별 구현입니다. 크로스 도메인 구현을 처리하지 않습니다.
* 특정 라이브러리에 대한 타사 호출을 비활성화하려면 각 라이브러리에서 해당 기본 설정을 별도로 구성해야 합니다.

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
   <td colname="col1"> <p>사전 동의 상태로 수집해도 되지만 동의를 받을 때까지 다른 모든 라이브러리는 로드할 수 없습니다 </p> </td> 
   <td colname="col2"> <p>옵트인을 사용하여 사전 동의 상태에서 분석 카테고리를 활성화합니다. </p> </td> 
   <td colname="col3"> <p>Analytics는 사전 동의 수집에서 ECID가 아닌 Analytics 식별자를 사용합니다. ECID가 승인되면 새로운 식별자가 사용되고 방문자는 활성화 및 통합에 사용할 수 있는 ECID를 받게 됩니다. </p> <p>사전/사후 동의 상태의 방문자 약진이 예상됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>퍼스트 파티 측정은 사전 동의 상태로 수집해도 됩니다. 다른 모든 유형의 데이터 사용은 동의를 받을 때까지 금지됩니다. </p> </td> 
   <td colname="col2"> <p>옵트인을 사용하여 사전 동의 상태에서 Analytics + ECID 라이브러리를 활성화합니다. </p> <p>ECID 라이브러리에 'disablethirdpartycookies' 구성을 추가하여 타사 쿠키 + ID 동기화를 사전 동의 상태에서 차단합니다. </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 호출은 ECID 검색에 대해 트리거되지만 Demdex 쿠키, 다른 타사 쿠키 또는 ID 동기화가 표시되지 않습니다. </p> <p>Analytics에 대한 사전/사후 동의 상태를 일관되게 유지합니다. 사전 동의 상태의 수집은 사후 동의 데이터 수집과 연계됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>퍼스트 파티 측정 + 타깃팅은 사전 동의 상태에서 허용됩니다. 다른 모든 유형의 데이터 사용은 동의를 받을 때까지 금지됩니다. </p> </td> 
   <td colname="col2"> <p>옵트인을 사용하여 사전 동의 상태에서 Analytics + ECID + Target 라이브러리를 활성화합니다. </p> <p>사전 동의 상태에서 타사 쿠키 + ID를 차단하려면 <span class="codeph">isablethirdpartycookies</span> 구성을 ECID 라이브러리에 추가합니다. 사후 동의 상태에서 플래그를 제거합니다. </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 호출은 ECID 검색에 대해 트리거되지만 Demdex 쿠키, 다른 타사 쿠키 또는 ID 동기화가 없습니다. </p> <p>퍼스트 파티 솔루션에 대해 일관된 방문자를 사전/사후 동의 상태로 유지합니다. 사전 동의 상태의 수집은 사후 동의 데이터 수집과 연계됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>사전 동의 상태에서 쿠키를 설정할 수 없음 </p> </td> 
   <td colname="col2"> <p>동의 수신까지 모든 라이브러리의 로드 차단 </p> </td> 
   <td colname="col3"> <p>구현은 예상대로 수행되며 ECID를 비롯한 모든 라이브러리는 동의 후 상태로 올바른 순서로 로드됩니다. </p> <p>동의를 하지 않는 고객의 데이터 손실 추적 </p> </td> 
  </tr> 
 </tbody> 
</table>

