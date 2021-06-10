---
description: ID 서비스에서 Adobe Experience Cloud Device Co-op로 데이터를 전송하거나 전송하지 않는지 여부를 결정하는 선택적 부울 구성입니다.
keywords: ID 서비스
title: isCoopSafe
exl-id: 827f7819-9f95-4e8d-90c3-dcf86b67715b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 100%

---

# isCoopSafe{#iscoopsafe}

ID 서비스에서 Adobe Experience Cloud Device Co-op로 데이터를 전송하거나 전송하지 않는지 여부를 결정하는 선택적 부울 구성입니다.

내용:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> 요구 사항 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> 사용 사례 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> 구문 및 코드 샘플 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> 이벤트 호출 POST 매개 변수 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> 사후 인스턴스화 API </a> </li> 
</ul>

## 요구 사항 {#section-4883eda6beb8437182bcc82bb58fae41}

`isCoopSafe`를 사용하려면 다음을 수행해야 합니다.

* ID 서비스 코드 버전 2.4 이상을 사용합니다.
* [Experience Cloud Device Co-op](https://docs.adobe.com/content/help/ko-KR/device-co-op/using/about/overview.html)에 참여합니다. 예상 Co-op 구성원은 이 설명서를 검토하여 `isCoopSafe`가 데이터 사용하여 장치 그래프를 생성하는 방법으로 인해 발생할 수 있는 문제를 해결하는지 확인해야 합니다.

* [!DNL Adobe] 컨설턴트와 함께 장치 Co-op 계정에 화이트리스트 또는 블랙리스트 플래그를 설정합니다. 이 플래그를 활성화하기 위한 셀프 서비스 경로가 없습니다.

## 사용 사례 {#section-d18af2b903f248e18ae8108aaf0a8ebb}

`isCoopSafe`는 장치 Co-op의 현재 또는 예상 멤버의 데이터 수집과 관련된 2가지 사용 사례를 해결하는 데 도움이 됩니다. 이러한 사용 사례는 장치 그래프를 작성하는 데 도움이 되도록 사이트 방문자 데이터를 장치 Co-op에 전달하는 방식에 대한 것입니다. 다음 표에서는 `isCoopSafe`를 이러한 사용 사례에서 사용하여 데이터를 장치 그래프로 보내거나 차단하는 방법을 설명합니다.

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 사용 사례 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>인증된 방문자</b> </p> </td> 
   <td colname="col2"> <p>장치 그래프를 작성하기 위해 장치 Co-op에서 사용 약관에 동의하거나 동의하지 않은 인증된 방문자에 대한 데이터를 사용하는 방법을 제어하려면 ID 서비스 코드에 <span class="codeph">isCoopSafe</span>를 추가합니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> </b>타사 사이트의 DIL<b> </b></p> </td> 
   <td colname="col2"> <p>다음과 같은 타사 사이트에서 사용할 ID 서비스 코드에 <span class="codeph">isCoopSafe</span>를 추가합니다. </p> <p> 
     <ul id="ul_C27BB26510314834A2A7CD99D46DA4AC"> 
      <li id="li_4E6AE574F18646F09C0CF4553EEA1A9E">인증된 방문자가 사용 기간 계약을 수락했는지 여부를 확인할 수 없습니다. </li> 
      <li id="li_26D0561BF32B4278B0A6B5082C17FED8">Device Co-op이 데이터를 사용하여 장치 그래프를 작성하는 방법을 제어해야 합니다. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## 구문 및 코드 샘플 {#section-952f56724a2b4d349340e26fbaf33ddd}

**구문:** `isCoopSafe: true | false`

부울 옵션은 장치 Co-op에서 고객 데이터를 사용하거나 사용하지 않는 방법을 결정합니다.

* `isCoopSafe: true`: 모바일 SDK 또는 웹 사이트에서 수집한 방문자 데이터를 사용하여 장치 그래프를 작성&#x200B;*할 수 있습니다*.

* `isCoopSafe: false`: 모바일 SDK 또는 웹 사이트에서 수집한 방문자 데이터를 사용하여 장치 그래프를 작성&#x200B;*할 수 없습니다*.

**코드 샘플**

ID 서비스 코드가 인스턴스화할 때 이를 설정합니다.

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## 이벤트 호출 POST 매개 변수 {#section-fcd441933506493faefaa6b51f194a17}

설정하는 플래그(`true` 또는 `false`)에 따라 ID 서비스는 `isCoopSafe`를 이러한 POST 매개 수로 변환하여 이벤트 호출 [!DNL Adobe]로 보냅니다.

* `d_coop_safe=1`
* `d_coop_unsafe=1`

POST 매개 수는 장치 그래프에 사용자 데이터를 포함할 수 있는지 여부를 [!DNL Experience Cloud] 장치 Co-op에 알립니다. 아래 표에서는 이벤트 호출 시 전달된 POST 매개 변수와 `isCoopSafe` 부울 플래그 간의 관계를 정의합니다. `isCoopSafe`를 사용하지 않는 경우에는 이벤트 호출 시 아무 것도 전달되지 않습니다.

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 구성 상태 </th> 
   <th colname="col2" class="entry"> POST 매개 변수 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: true </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_safe=1 </span> </p> <p>Co-op 장치에서 방문자 데이터를 사용하여 장치 그래프를 작성할 수 있습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: false </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_unsafe=1 </span> </p> <p>Co-op 장치에서 방문자 데이터를 사용하여 장치 그래프를 작성할 수 없습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

## 사후 인스턴스화 API {#section-9281c39c8b6249d7864100b5cbca7dc6}

이러한 API를 사용하면 `isCoopSafe` 상태를 재정의할 수 있습니다. 이러한 기능은 페이지가 새로 고쳐지지 않는 사이트 또는 단일 페이지 앱에서 방문자의 사후 인스턴스화/사후 로그인 상태를 변경할 수 있도록 해주므로 필요합니다. 예를 들어, 사용자가 사이트 또는 앱을 인증하고 나중에 Device Co-op에서 해당 데이터를 사용할 수 있도록 하는 사용 약관 정책을 수락하는 경우 이러한 API를 호출해야 합니다.

<table id="table_BAA96B1F82BE48C3A61A1AF1367BA45C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopSafe(); </span> </p> </td> 
   <td colname="col2"> <p>후속 이벤트 호출 시 POST 매개 변수 <span class="codeph">d_coop_safe=1</span>을 설정합니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopUnsafe(); </span> </p> </td> 
   <td colname="col2"> <p>후속 이벤트 호출 시 POST 매개 변수<span class="codeph"> d_coop_unsafe=1</span>을 설정합니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORELIKETHIS]
>
>* [DIL isCoopSafe](https://docs.adobe.com/content/help/ko-KR/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-coopsafe.html)

