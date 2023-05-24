---
description: Analytics에 대한 식별자, 즉 ID 서비스, 데이터 컬렉션 옵트아웃, 지리적 위치 및 메타데이터 "blob" 콘텐츠를 기본적으로 반환하는 비동기 API입니다. 또한 선택적 visitor.FIELDS 열거와 함께 반환할 ID를 제어할 수 있습니다.
keywords: ID 서비스
title: getVisitorValues
exl-id: bd023e8d-a804-4205-989f-e1e58080b63c
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 100%

---

# getVisitorValues{#getvisitorvalues}

Analytics에 대한 식별자, 즉 ID 서비스, 데이터 컬렉션 옵트아웃, 지리적 위치 및 메타데이터 &quot;blob&quot; 콘텐츠를 기본적으로 반환하는 비동기 API입니다. 또한 선택적 visitor.FIELDS 열거와 함께 반환할 ID를 제어할 수 있습니다.

내용:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local"> 구문 </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> 사용 사례 1: 기본 데이터 세트 요청 </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> 사용 사례 2: 사용자 지정 데이터 세트 요청 </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> 정의된 응답 매개 변수 </a> </li> 
</ul>

## 구문 {#section-5aebe3907b2b46e997f45a1d1ed35c09}

이 함수에서 사용하는 구문(기울임체는 변수 자리 표시자를 나타냄): ` var *`값`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`ID 유형`*, visitor.FIELDS. *`ID 유형`*]);`

함수 매개 변수 설명:

* ` *`callback`*`은 반환된 ID를 수신하는 고유한 콜백 코드를 나타냅니다.
* *(선택 사항)* ` visitor.FIELDS. *`ID 유형`*`은 이 함수가 반환할 [ID 값](../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5)을 지정할 수 있는 열거형입니다.

자세한 내용은 다음 사용 사례 및 정의를 참조하십시오.

## 사용 사례 1: 기본 데이터 세트 요청 {#section-36a31683558742a5915db3a391e09f7b}

이 코드는 표준 데이터 세트를 반환합니다. 요청 및 응답은 다음 예제와 비슷합니다.

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

기본 샘플 응답에서 일부 값은 데모용으로 축약되었습니다.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCOPTOUT: 'isoptedout-true', 
    MCAID: 'aid-1234', 
    MCAAMLH: 7, 
    MCAAMB: 'hgfe54236786oygj' 
}
```

## 사용 사례 2: 사용자 지정 데이터 세트 요청 {#section-467b2f4e513344c89b7332b05f6f59f3}

이 코드는 `visitor.FIELDS` 열거를 사용하여 특정 ID 세트를 반환하기 위해 선택적 배열을 사용합니다. 이 경우 방문자의 Experience Cloud ID(MCID) 및 Analytics ID(MCAID)만 필요합니다. 요청 및 응답은 다음 예제와 비슷합니다.

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

사용자 지정된 샘플 응답은 요청에 지정된 ID만 반환합니다.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## 정의된 응답 매개 변수 {#section-4c4c300167694c6fbff1d6c612f372b5}

다음 표에는 응답 매개 변수 목록 및 정의가 나와 있습니다. 또한 이러한 매개 변수는 `visitor.FIELDS` 열거형의 모든 값입니다. 참고 사항으로, 이 메서드는 특정 변수에 대한 값이 없으면 빈 문자열을 반환합니다.

<table id="table_32D0FEEA76CE4F298EED4B8F5C644232"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 값 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMB </span> </p> </td> 
   <td colname="col2"> <p>"Blob"이라고도 하는 암호화된 <span class="keyword">Audience Manager</span> 메타데이터입니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMLH </span> </p> </td> 
   <td colname="col2"> <p>데이터 수집 지역 ID. 특정 ID 서비스 데이터 센터의 지리적 위치에 대한 숫자 식별자입니다. </p> <p><a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=ko-KR" format="https" scope="external">DCS 지역 ID, 위치 및 호스트 이름</a>과 <a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getLocationHint </a>를 참조하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>방문자의 <span class="keyword">Analytics</span> ID입니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>방문자의 Experience Cloud ID. </p> <p><a href="../../introduction/cookies.md" format="dita" scope="local">쿠키 및 Experience Cloud ID 서비스</a>를 참조하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>방문자가 데이터 수집을 옵트아웃했는지 여부를 나타내는 플래그. </p> <p>값에는 다음이 포함됩니다. </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph"> 'isoptedout-true'</span>: 방문자가 데이터 수집을 해제했습니다. </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph"> 'isoptedout-false'</span>: 방문자가 데이터 수집을 해제하지 않았습니다. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
