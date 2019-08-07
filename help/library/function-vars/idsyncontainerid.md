---
description: 이 속성은 ID 동기화에 사용할 데이터 소스 컨테이너 ID를 설정합니다.
keywords: ID 서비스
seo-description: 이 속성은 ID 동기화에 사용할 데이터 소스 컨테이너 ID를 설정합니다.
seo-title: idSyncContainerID
title: idSyncContainerID
uuid: e35dc48b-1aa1-41e3-91c1-ef1e9d2d8b90
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# idSyncContainerID{#idsynccontainerid}

이 속성은 ID 동기화에 사용할 데이터 소스 컨테이너 ID를 설정합니다.

내용:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> 구문 및 코드 샘플 </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local"> 컨테이너이란 무엇이며, 언제 사용해야 합니까? </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> DIL 및 VisitorAPI.js 사용 시 컨테이너 ID 설정 </a> </li> 
</ul>

## 구문 및 코드 샘플 {#section-b0c50732b1c84bed8616e82e8e83d58c}

**구문:** ` idSyncContainerID: *`컨테이너 ID 값`*`

**코드 샘플:**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## 컨테이너이란 무엇이며, 언제 사용해야 합니까? {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**컨테이너**

컨테이너는 [!DNL Audience Manager]에서 만든 개체입니다. 외부에서 액세스할 수 없지만 이러한 컨테이너에는 다음과 같은 데이터 소스가 모두 나열되어 있습니다.

* ID 동기화에 사용할 수 있지만, 사용하지 않는 데이터 소스.
* ID 동기화에 사용되고 있는 데이터 소스.

[!DNL Audience Manager] 고객이 아니더라도 도메인의 다른 페이지에 있는 다른 데이터 소스와 ID를 교환하는 경우 계정에 이러한 컨테이너가 있습니다. [!DNL Audience Manager]에서 ID 동기화를 사용할 수 있는 기술 및 백엔드 기능을 제공하기 때문입니다.

**사용 사례**

상황에 따라 이 구성을 ID 서비스 코드에 추가해야 하거나 추가하지 않아도 될 수도 있습니다.

<table id="table_48621F343C7F4760A75F6BCC2DB2DA20"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 조건 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>필요하지 않음</b> </p> </td> 
   <td colname="col2"> <p>다음과 같은 경우 이 구성을 사용할 필요가 없습니다. </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808"><span class="keyword">Experience Cloud</span> 솔루션에서 ID 서비스를 사용하고 있으며, ID를 다른 데이터 소스와 동기화하지 않습니다. 이 경우 계정에 ID가 0인 기본 컨테이너가 있으며 조치가 필요하지 않습니다. </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">모든 데이터 소스는 한 컨테이너에 있습니다. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>필요함</b> </p> </td> 
   <td colname="col2"> <p>다음 조건이 모두 적용되는 경우 이 구성을 사용해야 합니다. </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE"><span class="keyword">Audience Manager</span>를 사용하지 않습니다 . </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">컨테이너에 구성된 다른 데이터 소스와 ID를 동기화해야 합니다. </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">도메인의 다른 페이지에 있는 다른 컨테이너의 데이터 소스와 ID를 동기화해야 합니다. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## DIL 및 VisitorAPI.js 사용 시 컨테이너 ID 설정 {#section-f283cb69c8de4348b5316cc4e02a3e9e}

동일한 페이지에서 [!UICONTROL DIL]*및* VisitorAPI.js를 배포한 경우 다음을 수행하십시오.

* 방문자 ID 서비스 코드가 ID 동기화를 위한 DIL보다 우선합니다.
* ID 서비스 코드에서만 `idSyncContainerID` 구성을 설정합니다.

