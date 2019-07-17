---
description: Experience Cloud ID 서비스 영역 ID를 반환합니다. 지역 ID(또는 위치 힌트)는 특정 ID 서비스 데이터 센터의 지리적 위치에 대한 숫자 식별자입니다. 서버측 API에서 Audience Manager를 호출하도록 하려면 영역 ID가 필요합니다.
keywords: ID 서비스
seo-description: Experience Cloud ID 서비스 영역 ID를 반환합니다. 지역 ID(또는 위치 힌트)는 특정 ID 서비스 데이터 센터의 지리적 위치에 대한 숫자 식별자입니다. 서버측 API에서 Audience Manager를 호출하도록 하려면 영역 ID가 필요합니다.
seo-title: getLocationHint를 참조하십시오
title: getLocationHint를 참조하십시오
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# getLocationHint{#getlocationhint}를 참조하십시오

Experience Cloud ID 서비스 영역 ID를 반환합니다. 지역 ID(또는 위치 힌트)는 특정 ID 서비스 데이터 센터의 지리적 위치에 대한 숫자 식별자입니다. 서버측 API에서 Audience Manager를 호출하도록 하려면 영역 ID가 필요합니다.

**구문:** ` var *`변수 이름`* = visitor.getLocationHint()`

영역 ID 및 해당 위치 목록에 대해서는 [DCS 영역 ID, 위치 및 호스트 이름](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html)을 참조하십시오.

**코드 샘플**

위치 힌트 함수는 AMCV 쿠키에서 지역 ID를 읽습니다. 지역 ID가 이미 AMCV 쿠키에 설정된 경우 즉시 콜백이 발생합니다. 지역 ID가 설정되어 있지 않으면 함수가 지역 ID를 콜백에 전달하기 전에 서버에서 응답을 기다립니다. 코드는 다음 예와 비슷하게 보일 수 있습니다.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

