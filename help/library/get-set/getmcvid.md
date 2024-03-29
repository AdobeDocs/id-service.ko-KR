---
description: getMarketingCloudVisitorID는 Experience Cloud 방문자 ID를 반환합니다.
keywords: ID 서비스
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 100%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID는 Experience Cloud 방문자 ID를 반환합니다.

**구문:** ` var *`변수 이름`* = visitor.getMarketingCloudVisitorID()`

이 메서드는 일반적으로 방문자 ID를 읽어야 하는 사용자 지정 솔루션에 사용됩니다. 표준 구현에서는 사용되지 않습니다. 또한 `getMarketingCloudVisitorID`는 [!DNL Analytics] ID를 읽은 후 시스템 또는 애플리케이션으로 가져오기 위해 콜백 함수에서도 사용됩니다.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>[!DNL Analytics] 고객인 경우 [!DNL Analytics] ID도 확인한 후 함수로 보내십시오. 예를 들어 숨겨진 양식 요소의 방문자 ID를 데이터 삽입 API를 사용하는 서버측 애플리케이션에 전달할 때 두 식별자를 모두 원할 수 있습니다. 이 경우 [!DNL Experience Cloud] 및 [!DNL Analytics] 방문자 ID를 수집한 후 반환해야 합니다. [Analytics 방문자 ID 가져오기](../../library/get-set/getanalyticsvisitorid.md)를 참조하십시오.
