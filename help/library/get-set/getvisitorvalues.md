---
description: Analytics에 대한 식별자, 즉 ID 서비스, 데이터 컬렉션 옵트아웃, 지리적 위치 및 메타데이터 "blob" 컨텐츠를 기본적으로 반환하는 비동기 API입니다. 또한 선택적 visitor.FIELDS 열거와 함께 반환할 ID를 제어할 수 있습니다.
keywords: ID 서비스
seo-description: Analytics에 대한 식별자, 즉 ID 서비스, 데이터 컬렉션 옵트아웃, 지리적 위치 및 메타데이터 "blob" 컨텐츠를 기본적으로 반환하는 비동기 API입니다. 또한 선택적 visitor.FIELDS 열거와 함께 반환할 ID를 제어할 수 있습니다.
seo-title: getVisitorValues
title: getVisitorValues
uuid: 7fb831b3-cf7e-40e2-a219-07fec28ad49c
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# getVisitorValues{#getvisitorvalues}

Analytics에 대한 식별자, 즉 ID 서비스, 데이터 컬렉션 옵트아웃, 지리적 위치 및 메타데이터 &quot;blob&quot; 컨텐츠를 기본적으로 반환하는 비동기 API입니다. 또한 선택적 visitor.FIELDS 열거와 함께 반환할 ID를 제어할 수 있습니다.

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

이 코드는 표준 데이터 세트를 반환합니다. 요청 및 응답이 다음 예와 비슷하게 보일 수 있습니다.

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

기본 샘플 응답에서 일부 값은 데모 목적으로 축소되었습니다.

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

이 코드는 `visitor.FIELDS` 열거를 사용하여 특정 ID 세트를 반환하기 위해 선택적 배열을 사용합니다. 이 경우 방문자의 Experience Cloud ID(MCID)와 Analytics ID(MCAID)만 사용합니다. 요청 및 응답이 다음 예와 비슷하게 보일 수 있습니다.

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

다음 표에는 응답 매개 변수 목록 및 정의가 나와 있습니다. 또한 이러한 매개 변수는 `visitor.FIELDS` 열거형의 모든 값입니다. 이 메서드는 특정 변수에 대한 값이 없는 경우 및 빈 문자열을 반환합니다.

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
   <td colname="col2"> <p>데이터 수집 영역 ID입니다. 특정 ID 서비스 데이터 센터의 지리적 위치에 대한 숫자 식별자입니다. </p> <p><a href="https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html" format="https" scope="external">DCS 지역 ID, 위치 및 호스트 이름</a>과 <a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getLocationHint </a>를 참조하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>방문자의 <span class="keyword">Analytics</span> ID입니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>방문자 Experience Cloud ID입니다. </p> <p>자세한 내용은 <a href="../../introduction/cookies.md" format="dita" scope="local"> 쿠키 및 Experience Platform Identity Service </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>방문자가 데이터 수집을 해제했는지 여부를 나타내는 플래그입니다. </p> <p>값은 다음과 같습니다. </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph"> 'isoptedout-true'</span>: 방문자가 데이터 수집을 해제했습니다. </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph"> 'isoptedout-false'</span>: 방문자가 데이터 수집을 해제하지 않았습니다. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

