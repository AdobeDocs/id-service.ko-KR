---
description: 2018년 Experience Cloud ID 서비스의 기능 릴리스, 업데이트 또는 변경 사항입니다.
keywords: ID 서비스
title: 2018 릴리스 정보
exl-id: ad3cccf1-2753-4ac9-a68c-15b2d62bbc1a
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '477'
ht-degree: 100%

---

# 2018 릴리스 정보 {#release-notes}

2018년 Experience Cloud ID 서비스의 기능 릴리스, 업데이트 또는 변경 사항입니다.

## 버전 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 항목 설명 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>AMCV 쿠키에 대한 보안 강화 </p> </td> 
   <td colname="col2"> <p>내부 보안 검사 중에 DTM 라이브러리를 사용할 때 세션 관리에 사용되는 쿠키가 적절한 속성을 지정하지 못하는 것을 발견했습니다. 이로 인해 쿠키 정보가 실수로 공유될 수 있습니다. 이 문제를 해결하기 위해 고객이 AMCV 쿠키를 보안으로 설정할 수 있는 구성을 도입했습니다. <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a>를 참조하십시오. </p> </td> 
  </tr> 
 </tbody> 
</table>

## 버전 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 항목 설명 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>AMCV 쿠키에 대한 보안 강화 </p> </td> 
   <td colname="col2"> <p>내부 보안 검사 중에 DTM 라이브러리를 사용할 때 세션 관리에 사용되는 쿠키가 적절한 속성을 지정하지 못하는 것을 발견했습니다. 이로 인해 쿠키 정보가 실수로 공유될 수 있습니다. 이 문제를 해결하기 위해 고객이 AMCV 쿠키를 보안으로 설정할 수 있는 구성을 도입했습니다. secureCookie를 참조하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>통합 코드 및 ID는 숫자이거나 비어 있지 않은 문자열이어야 합니다. </p> </td> 
   <td colname="col2"> <p>데이터에 숫자도 아니고 비어 있지 않은 문자열도 아닌 통합 “코드” 또는 “ID”가 포함되어 있을 때 “setCustomerIDs”를 확인하는 문제가 해결되었습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ECID JS는 공용 Git 리포지토리에서 사용할 수 있습니다. </td> 
   <td colname="col2"> 이제 모든 Experience Cloud 고객이 다음에 있는 공용 Git 리포지토리의 ECID JS를 사용할 수 있습니다. https://github.com/Adobe-Marketing-Cloud/id-service/releases </td> 
  </tr> 
 </tbody> 
</table>

## 버전 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 항목 설명 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>고유 방문자 수의 비정상적인 급증 </p> </td> 
   <td colname="col2"> <p>Experience Cloud ID 서비스 3.1.0이 릴리스된 후 이 버전을 구현할 때 고유 방문자 수가 비정상적으로 급증하는 문제가 발견되었습니다. 이 동작은 최신 버전의 ECID, v3.1.0에서만 나타나며 사용자가 Safari 브라우저의 개인정보 설정에서 “현재 웹 사이트에서만 허용” 옵션을 선택한 경우에만 나타납니다. 버전 3.1.2는 이 문제를 해결합니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

## 버전 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>편리한 시간에 버전 3.1.0에서 최신 버전으로 업그레이드하는 것이 좋습니다. 버전 3.1.2 설명을 참조하십시오. Adobe Experience Platform Launch, DTM 및 AppMeasurement에서 최신 번들을 사용할 수 있습니다.

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 항목 설명 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>잘못된 도메인에 설정된 쿠키 </p> </td> 
   <td colname="col2"> <p>임시 방문자 쿠키가 구성(initConfig)에 제공된 도메인에서 쿠키를 설정하는 대신 “기본” 쿠키 도메인에서 설정하는 버그를 수정했습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

## 버전 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 항목 설명 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>여러 ID 동기화 요청에 대한 스레드 산출 </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>여러 ID 동기화를 수행하는 고객의 경우 지속적인 CPU 계산으로 인해 일부 경우 UI가 차단됩니다. ID 동기화 요청을 각각 100밀리초 씩 분리하는 스레드 일시 중단을 도입하고 있습니다. </p> <p>이 변경 사항은 Visitor 2.3.0+ 및 DIL 6.10+를 사용하는 고객의 성능을 향상시킵니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 서드파티 통화를 비활성화하는 기능이 추가됨 </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>Adobe에서 서드파티 동기화 통화를 비활성화할 수 있도록 다음 구성 이름을 변경했습니다. </p> <p>idSyncDisableSyncs에서 disableIdSyncs로 </p> <p>idSyncDisable3rdPartySyncing에서 disableThirdPartyCookies로 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Internet Explorer 지원 </p> </td> 
   <td colname="col2"> <p>ID 서비스는 더 이상 Internet Explorer 6, 7, 8 및 9를 지원하지 않습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>getInstance 설명서로 업데이트 </p> </td> 
   <td colname="col2"> <p>Visitor 함수에 이 함수를 var visitor = new Visitor로 인스턴스화하지 않았다는 경고가 추가되었습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>
