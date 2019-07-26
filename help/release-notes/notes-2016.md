---
description: 2016년 Experience Cloud Identity 서비스의 기능 릴리스, 업데이트 또는 변경 사항입니다.
keywords: ID 서비스
seo-description: 2016년 Experience Cloud Identity 서비스의 기능 릴리스, 업데이트 또는 변경 사항입니다.
seo-title: 2016 릴리스 노트
title: 2016 릴리스 노트
uuid: 7a5a314a-3ff8-4561-9c64-6c10d2223887
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# 2016 릴리스 노트 {#release-notes}

2016년 Experience Cloud Identity 서비스의 기능 릴리스, 업데이트 또는 변경 사항입니다.

이러한 변경 사항은 [Experience Cloud 릴리스 노트](https://marketing.adobe.com/resources/help/ko_KR/whatsnew/)에도 캡처되었습니다. 이전 [!DNL Experience Cloud] 공지 사항에 대해서는 [이전 릴리스 노트](https://marketing.adobe.com/resources/help/ko_KR/whatsnew/?f=c_legacy_releases.html)를 참조하십시오.

## 버전 1.10 {#section-7d719b3213344a46858835042e0214ed}

2016년 11월

>[!IMPORTANT]
>
>* 버전 1.10은 [!DNL AppMeasurement] 1.8.0이 필요합니다.
>* Experience Cloud Identity 서비스 라이브러리 2.0.0 이상을 사용하면 기본적으로 Adobe Media Optimizer에 대한 ID 동기화가 시작됩니다. [ID 동기화 및 일치율 이해](/help/introduction/match-rates.md)를 참조하십시오.


**수정 사항 및 향상된 기능**

* 서버측 환경에 ID 서비스를 구현하는 방법에 대한 지침을 추가했습니다.
* 자신이 소유한 다른 도메인의 Experience Cloud 및 Analytics ID를 덮어쓸 수 있는 부울 함수인 `Visitor.overwriteCrossDomainMCIDAndAID`가 추가되었습니다. [방문자 ID 덮어쓰기](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde)를 참조하십시오.

* `TS = UTC` 타임스탬프를 `visitor.appendVisitorIDsTo` 함수의 속성으로 추가했습니다. ID 서비스는 5분 에이징 간격을 기반으로 하여 리디렉션 URL에서 ID를 사용해야 하는지 여부를 결정하는 데 타임스탬프를 사용합니다. 자세한 내용은 [방문자 ID 함수 추가](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* 지역 ID를 반환하는 `Visitor.getLocationHint,` 함수가 새로 추가되었습니다. [지역 ID 가져오기(위치 힌트)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)를 참조하십시오.

* 대상 게시 iFrame에서 ID 동기화를 수동으로 구현할 수 있는 `idSyncByURL`과 `idSyncByDataSource` 함수가 추가되었습니다. [URL 또는 데이터 소스 별로 ID 동기화](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48)를 참조하십시오.

* `disableThirdPartyCalls:true`인 경우 AppMeasurement 추적 호출을 차단한 버그가 수정되었습니다.
* ID 서비스에서 다른 도메인의 Experience Cloud ID(MID)를 전달할 수 없었던 버그가 수정되었습니다.

## 버전 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

2016년 10월

**수정 사항 및 향상된 기능**

* Audience Manager 고유 사용자 ID(AAMUUID)를 Experience Cloud ID로 ID 서비스에 전달하는 버그를 수정했습니다.
* AMCV 쿠키에 대한 TTL(time-to-live)이 만료된 경우, ID 서비스에서는 Experience Cloud ID가 쿠키에 들어 있는 한 해당 정보를 서버에 반환합니다. 이 호출 후, ID 서비스는 비동기 호출을 만들어 쿠키를 업데이트합니다. 이렇게 하면 ID 서비스가 서버 응답을 기다릴 필요가 없으므로 성능을 개선하는 데 도움이 됩니다. 이 서비스에서는 기존의 AMCV 쿠키 값을 사용한 다음, 업데이트를 요청할 수 있습니다.
* ID 서비스는 Experience Cloud ID(MID)를 페이지의 Adobe Media Optimizer 및 기타 내부 Adobe 도메인과 직접 자동으로 동기화합니다. 기존 계정 및 신규 계정 전체에 자동 동기화가 활성화됩니다. 이것은 Media Optimizer에 대한 일치율을 개선하는 데 도움이 됩니다. VisitorAPI.js 버전 1.8, 이상에 적용됩니다. [ID 동기화 및 일치율 이해](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab)를 참조하십시오.

**새로운 설명서 및 수정된 설명서**

**새로운 내용:** [AMCV 쿠키에서 영역 및 사용자 ID 가져오기](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## 버전 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

2016년 9월

**수정 사항 및 향상된 기능**

`disableThirdPartyCalls`가 `Visitor.getInstance` 함수에서 설정할 수 있는 선택적 부울 플래그로 추가되었습니다. `disableThirdPartyCalls= true`이면 ID 서비스는 다른 도메인을 호출하지 않습니다. 기본적으로 `disableThirdPartyCalls= false`입니다. [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b)를 참조하십시오.

## 버전 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

2016년 8월

**수정 사항 및 향상된 기능**

* `idSyncAttachIframeOnWindowLoad`가 `Visitor.getInstance` 함수에서 설정할 수 있는 선택적 부울 플래그로 추가되었습니다. `idSyncAttachIframeOnWindowLoad= true`이면 ID 서비스가 창 로드 시 ID 동기화 iFrame을 로드합니다. 기본적으로 ID 서비스는 가능한 빠르게 iFrame을 로드합니다. 이 플래그는 사용되지 않는 *를*&#x200B;바꿉니다`idSyncAttachIframeASAP`. [Visitor.getInstance 함수 변수](../library/function-vars/function-vars.md)를 참조하십시오.

* 도메인, 기본 앱 및 하이브리드 앱에서 웹 전환으로 [!DNL Experience Cloud] ID 추적을 지원하는 기능이 추가되었습니다. [방문자 ID 지원 기능 추가](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce)를 참조하십시오.

* ID 서비스에서 방문자 [!DNL Experience Cloud] ID 클라이언트측 또는 서버측을 생성했는지 또는 ID 호출이 시간 초과되었는지 확인하는 함수가 visitorAPI.js 코드에 대한 추가되었습니다. [시간 초과 추적 기능](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) 및 [클라이언트측 방문자 ID 생성 추적](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6)을 참조하십시오.

**새로운 설명서 및 수정된 설명서**

수정된 설명서: [Experience Cloud Identity 서비스 요구 사항](../reference/requirements.md)

**알려진 문제**

같은 페이지에서 [!DNL Audience Manager] DIL 코드와 visitorAPI.js 코드를 사용하는 고객은 DIL 변수 `secureDataCollection= false`를 설정해야 합니다. [secureDataCollection](https://marketing.adobe.com/resources/help/en_US/aam/?f=dil-secure-data-collection.html)을 참조하십시오.

## 버전 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

2016년 7월

>[!IMPORTANT]
>
>[!DNL Experience Cloud] ID 서비스 버전 1.6.0은 JavaScript 버전 1.6.2용 AppMeasurement가 *필요*&#x200B;합니다. ID 서비스 버전 1.6.0으로 업그레이드하는 경우 올바른 AppMeasurement 코드 버전을 사용 중인지 확인하십시오.

<table id="table_5472AAFA0DD2495DB8D92DEBE44A07A9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 기능 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>CORS(교차 도메인 리소스 공유) </p> </td> 
   <td colname="col2"> <p>CORS를 사용하면 브라우저에서 현재 도메인 이외의 도메인으로부터 리소스를 요청할 수 있습니다. Experience Cloud Identity 서비스는 클라이언트측의 교차 도메인 리소스 요청이 가능하도록 CORS 표준을 지원합니다. ID 서비스는 CORS를 지원하지 않는 브라우저에서는 JSONP 요청으로 되돌립니다. </p> <p>다음을 참조하십시오. </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local">Experience Cloud Identity 서비스에서 CORS 지원</a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**수정 사항 및 향상된 기능**

* ID 동기화 호출에 대한 `d_fieldgroup` 매개 변수를 `dpm.demdex.net`에 추가했습니다. 이 새 매개 변수는 내부 문제 해결 및 디버깅 목적에 사용됩니다.

* ID 서비스 iFrame에 제목 속성이 추가되었습니다. iFrame 제목 도움말 스크린 리더는 온라인 컨텐츠와 상호 작용할 때 지원이 필요한 사용자에게 페이지 정보를 제공합니다. iFrame 제목 속성이 `Adobe ID Syncing iFrame`으로 설정되어 있습니다. 
* `idSyncAttachIframeASAP: true`가 `Visitor.getInstance` 함수에서 설정할 수 있는 선택적 플래그로 추가됨. `true`일 경우, ID 서비스는 최대한 빠르게 ID 동기화 iFrame을 로드합니다. ID 동기화 일치율을 향상시킬 수 있도록 설계되었습니다. 기본적으로 ID 서비스는 iFrame을 윈도우 로드에 로드합니다. [Visitor.getInstance 함수 변수](../library/function-vars/function-vars.md)를 참조하십시오.

* AppMeasurement에서 무한 루프가 발생한 원인이 되는 콜백 함수 버그를 수정했습니다.
* 기본 `loadTimeout` 간격이 500밀리초에서 30,000밀리초로 변경되었습니다. [Visitor.getInstance 함수 변수](../library/function-vars/function-vars.md)를 참조하십시오.

**새로운 설명서 및 수정된 설명서**

**신규**

* [Analytics용 Experience Cloud Identity 서비스 구현](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)
* [Analytics, Audience Manager 및 Target용 Experience Cloud Identity 서비스 구현](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**수정된 설명서**

* [Experience Cloud Identity 서비스 요구 사항](../reference/requirements.md)
* [Experience Cloud Identity 서비스 테스트 및 확인](../implementation-guides/test-verify.md)

## 버전 1.5.7 {#section-735b4989a5744a42aeb2d97602dbda62}

2016년 6월

<table id="table_5D604D0820C84EC996ACB99126C8A3DF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 기능 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><span class="codeph">iframe.sandbox</span> 속성 변경 </p> </td> 
   <td colname="col2"> <p>이제 iFrame이 <span class="codeph">iframe.sandbox='allow-scripts allow-same-origin';</span>으로 설정되었습니다. </p> <p>이 2개의 토큰만 허용하므로 보안이 강화되고 ID 서비스에 ID 동기화에 필요한 기본 기능이 제공됩니다. </p> <p>sandbox 속성은 Internet Explorer 버전 9 이하에서 지원되지 않습니다. 자세한 내용은 이 <a href="https://developer.mozilla.org/ko-KR/docs/Web/HTML/Element/iframe" format="https" scope="external">iFrame 설명서</a>의 속성 섹션을 참조하십시오 . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Experience Cloud ID(MID) 인코딩 </p> </td> 
   <td colname="col2"> <p>ID 서비스는 서버에서 반환된 MID 값 또는 <span class="codeph">visitor.setMarketingCloudVisitorID()</span> 함수에 설정된 경우 MID 값을 인코딩합니다. MID에 대한 자세한 내용은 <a href="../introduction/cookies.md" format="dita" scope="local">쿠키 및 Experience Cloud ID</a>를 참조하십시오. </p> </td> 
  </tr> 
 </tbody> 
</table>

**수정 사항**

방문자 API는 기존 Analytics 방문자 ID가 없는 경우 Audience Manager와의 추가 재동기화 호출을 지정하지 않습니다.

## 버전 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

2016년 5월

**설명서 업데이트**

* [Android 및 iOS용 SDK 요구 사항](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Data Workbench 및 Experience Cloud Identity 서비스 ](../reference/dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8)
* [Experience Cloud Identity 서비스 테스트 및 확인](../implementation-guides/test-verify.md)

## 버전 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

2016년 4월

**설명서 업데이트**

[Target용 Experience Cloud Identity 서비스 구현](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

## 버전 1.5.4 {#section-1a44ba147fb3440ea7dec551faee3528}

2016년 3월

<table id="table_F4ED1F88709E4D3BA69C747879A4E18F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 기능 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>옵트아웃 지원 </p> </td> 
   <td colname="col2"> <p><span class="keyword">Experience Cloud</span> ID 서비스가 방문자의 옵트아웃 요청을 지원합니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> ID 동기화 간격 변경 </p> </td> 
   <td colname="col2"> <p>이제 <span class="keyword">Experience Cloud ID</span> 서비스에서 데이터 수집 서버를 호출할 때마다 ID 동기화 호출을 실행합니다. 이전에는 ID 서비스에서 첫 번째 호출에서 한 번만 요청하여 <span class="keyword">Experience Cloud</span> ID를 받았습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

**설명서 업데이트**

* [Analytics용 Experience Cloud Identity 서비스 ](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd): [!DNL Analytics]에서 ID 서비스를 설정하는 방법을 설명하는 새로운 절차입니다.

* [Experience Cloud Identity 서비스 마이그레이션 의사 결정 지점](../reference/analytics-reference/migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257): 명확성을 위해 텍스트가 수정되었습니다. 단일 도메인 사용이란 데이터 수집 CNAME을 더 이상 관리하지 않으려는 경우 여기에서 마이그레이션할 수 있음을 의미합니다. 그렇지만 CNAME이 작동하는 경우에는 변경할 필요가 없습니다.

## 버전 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

2016년 1월

**설명서 업데이트**

<table id="table_C1A5DBED6B104C0FBA54EC663D3B0E86"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 주제 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../reference/authenticated-state.md" format="dita" scope="local"> 고객 ID 및 인증 상태 </a> </p> </td> 
   <td colname="col2"> <p>텍스트가 개정되었습니다. 고객 ID를 인코딩 해제된 값으로만 전달해야 합니다. 인코딩 ID는 이중으로 인코딩된 식별자를 만듭니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

