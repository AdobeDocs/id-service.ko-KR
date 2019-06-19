---
description: 경험 플랫폼 ID 서비스가 구현되기 전에 s_ vi 쿠키에 저장된 이전 Analytics ID (있는 경우) 를 반환합니다. 방문자에게 Analytics ID가 지정되지 않은 경우 빈 문자열을 반환합니다.
keywords: ID 서비스
seo-description: 경험 플랫폼 ID 서비스가 구현되기 전에 s_ vi 쿠키에 저장된 이전 Analytics ID (있는 경우) 를 반환합니다. 방문자에게 Analytics ID가 지정되지 않은 경우 빈 문자열을 반환합니다.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6 bb 8 ddfc -9 fc 1-4105-b 377-d 9 b 4 d 247 a 0 f 8
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

경험 플랫폼 ID 서비스가 구현되기 전에 s_ vi 쿠키에 저장된 이전 Analytics ID (있는 경우) 를 반환합니다. 방문자에게 Analytics ID가 지정되지 않은 경우 빈 문자열을 반환합니다.

**구문** `var analyticsID = visitor.getAnalyticsVisitorID()`

일반적으로 이 함수는 방문자 ID 읽기가 필요한 사용자 지정 솔루션에서 사용됩니다. 표준 구현에서는 사용되지 않습니다. 또한 `getAnalyticsVisitorID`는 [!DNL Analytics] ID를 읽은 후 시스템 또는 애플리케이션으로 가져오기 위해 콜백 함수에서도 사용됩니다.

**샘플 코드**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>[!DNL Analytics] 고객인 경우 ID를 [!DNL Analytics] 확인하고 함수에 보내십시오. 예를 들어 숨겨진 양식 요소의 방문자 ID를 데이터 삽입 API를 사용하는 서버측 애플리케이션에 전달할 때 두 식별자를 모두 원할 수 있습니다. 이 경우 [!DNL Experience Cloud] , AND [!DNL Analytics] 방문자 ID를 수집 및 반환해야 합니다. [Getmarketingcloudvisitorid](../../library/get-set/getmcvid.md)를 참조하십시오.

**&quot;aid&quot; 매개 변수는 이전 값입니다.**

`aid` 매개 변수는 2개의 다른 조건 세트 아래의 쿼리 문자열에 나타납니다. 

**사례 1**

다음 경우에 쿼리 문자열에 `aid` 매개 변수가 표시됩니다.

* [!DNL Experience Cloud] ID 서비스가 올바르게 배포됩니다.
* 사이트를 방문하는 사용자의 경우 기존 [!DNL Analytics] ID가 [s_vi 쿠키](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html)에 저장되어 있습니다.

**사례 2**

조직에서 ID `aid` 서비스를 완전히 구현하기 전에 [유예 기간을](../../reference/analytics-reference/grace-period.md) 사용하는 경우 쿼리 문자열에 매개 변수가 표시됩니다. 사이트를 방문하는 사용자가 유예 기간을 사용하지 않는 경우 방문자는 `mid`[!DNL Experience Cloud] (id) 매개 변수를 받게 됩니다.

>[!MORE_ like_ this]
>
>* [Analytics 쿠키](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

