---
description: Experience Cloud ID 서비스 지역 ID를 반환합니다. 지역 ID(또는 위치 힌트)는 특정 ID 서비스 데이터 센터의 지리적 위치에 대한 숫자 식별자입니다. Audience Manager에 서버측 API를 호출하려면 지역 ID가 필요합니다.
keywords: ID 서비스
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '185'
ht-degree: 100%

---

# getLocationHint{#getlocationhint}

Experience Cloud ID 서비스 지역 ID를 반환합니다. 지역 ID(또는 위치 힌트)는 특정 ID 서비스 데이터 센터의 지리적 위치에 대한 숫자 식별자입니다. Audience Manager에 서버측 API를 호출하려면 지역 ID가 필요합니다.

**구문:** ` var *`변수 이름`* = visitor.getLocationHint()`

지역 ID 및 해당 위치 목록을 보려면 [DCS 지역 ID, 위치 및 호스트 이름](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=ko-KR)을 참조하십시오.

**코드 샘플**

위치 힌트 함수는 AMCV 쿠키에서 지역 ID를 읽습니다. 지역 ID가 이미 AMCV 쿠키에 설정된 경우 콜백이 즉시 수행됩니다. 지역 ID가 설정되지 않은 경우 함수는 지역 ID를 콜백으로 전달하기 전에 서버로부터 응답을 기다립니다. 코드는 다음 예와 비슷하게 보일 수 있습니다.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```
