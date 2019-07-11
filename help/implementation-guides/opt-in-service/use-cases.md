---
description: 옵트인 서비스를 관리하는 샘플 사용 사례 및 솔루션.
seo-description: 옵트인 서비스를 관리하는 샘플 사용 사례 및 솔루션.
seo-title: 옵트인 사용 사례
title: 옵트인 사용 사례
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: ht
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671

---


# 옵트인 사용 사례 {#opt-in-use-cases}

옵트인 서비스를 관리하는 샘플 사용 사례 및 솔루션.

## 팁 및 문제 해결 {#section-5c566366410f4a8f89eca0d3f556d99f}

* Visitor JS 초기화가 동기화되고, 페이지 로드 중에 실행됩니다. 지연 시간이 높은 CMP 또는 권한 지속성과 상호 작용하는 경우 [옵트인 설정](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)에 설명된 비동기 함수를 사용하는 것이 좋을 수 있습니다.
* 옵트인은 도메인별 구현입니다. 교차 도메인 구현은 처리하지 않습니다.
* 특정 라이브러리에 대해 타사 호출을 비활성화하려면 각 라이브러리에 해당 환경 설정을 별도로 구성해야 합니다.

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
   <td colname="col1"> <p>Analytics는 사전 동의 상태에서 수집하는 것이 좋지만, 동의를 받을 때까지 다른 모든 라이브러리를 로드할 수 없습니다. </p> </td> 
   <td colname="col2"> <p>옵트인을 사용하여 Analytics 카테고리를 사전 동의 상태에서 활성화합니다. </p> </td> 
   <td colname="col3"> <p>Analytics는 사전 동의 수집에 ECID가 아닌 Analytics 식별자를 사용합니다. ECID가 승인되면 새 식별자가 사용되고, 방문자가 활성화 및 통합에 사용할 수 있는 ECID를 수신합니다. </p> <p>사전/사후 동의 상태에서 방문자 단편화가 예상됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>자사 측정은 사전 동의 상태에서 수집하는 것이 좋습니다. 동의를 받을 때까지 다른 모든 유형의 데이터 사용이 금지됩니다. </p> </td> 
   <td colname="col2"> <p>옵트인을 사용하여 Analytics + ECID 라이브러리를 사전 동의 상태에서 활성화합니다. </p> <p>사전 동의 상태에서 타사 쿠키 + ID를 차단하려면 'disablethirdpartycookies' 구성을 ECID 라이브러리에 추가합니다. </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 호출은 ECID 검색을 트리거하지만 Demdex 쿠키, 기타 타사 쿠키 또는 ID 동기화가 없습니다. </p> <p>Analytics에 대한 사전/사후 동의 상태에 일관된 방문자를 유지합니다. 사전 동의 상태의 수집이 사후 동의 데이터 수집에 연결됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>자사 측정과 타겟팅은 사전 동의 상태에서 허용됩니다. 동의를 받을 때까지 다른 모든 유형의 데이터 사용이 금지됩니다. </p> </td> 
   <td colname="col2"> <p>옵트인을 사용하여 Analytics + ECID + Target 라이브러리를 사전 동의 상태에서 활성화합니다. </p> <p>사전 동의 상태에서 타사 쿠키 + ID를 차단하려면 <span class="codeph">isablethirdpartycookies</span> 구성을 ECID 라이브러리에 추가합니다. 사후 동의 상태에서 플래그를 제거합니다. </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 호출은 ECID 검색을 트리거하지만 Demdex 쿠키, 기타 타사 쿠키 또는 ID 동기화가 없습니다. </p> <p>자사 솔루션 대한 사전/사후 동의 상태에 일관된 방문자를 유지합니다. 사전 동의 상태의 수집이 사후 동의 데이터 수집에 연결됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>사전 동의 상태에 설정할 수 있는 쿠키가 없습니다. </p> </td> 
   <td colname="col2"> <p>옵트인을 사용하여 동의를 받을 때까지 모든 라이브러리가 로드되지 않도록 차단합니다. </p> </td> 
   <td colname="col3"> <p>구현은 ECID를 포함하여 예상되는 라이브러리와 모든 라이브러리이며, 사후 동의 상태에서 올바른 순서로 로드됩니다. </p> <p>추적에 동의하지 않는 고객에 대한 데이터 손실이 발생합니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

