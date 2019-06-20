---
description: Experience Cloud ID 서비스가 구현되기 전에 s_ vi 쿠키에 저장된 이전 Analytics ID (있는 경우) 를 반환합니다. 방문자에게 Analytics ID가 지정되지 않은 경우 빈 문자열을 반환합니다.
keywords: ID 서비스
seo-description: Experience Cloud ID 서비스가 구현되기 전에 s_ vi 쿠키에 저장된 이전 Analytics ID (있는 경우) 를 반환합니다. 방문자에게 Analytics ID가 지정되지 않은 경우 빈 문자열을 반환합니다.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6 bb 8 ddfc -9 fc 1-4105-b 377-d 9 b 4 d 247 a 0 f 8
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Experience Cloud ID 서비스가 구현되기 전에 s_ vi 쿠키에 저장된 이전 Analytics ID (있는 경우) 를 반환합니다. 방문자에게 Analytics ID가 지정되지 않은 경우 빈 문자열을 반환합니다.

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
>[!DNL Analytics] 고객인 경우 ID를 [!DNL Analytics] 확인하고 함수에 보내십시오. 예를 들어 숨겨진 양식 요소의 방문자 ID를 데이터 삽입 API를 사용하는 서버측 애플리케이션에 전달할 때 두 식별자를 모두 원할 수 있습니다. In this case, you should collect and return the [!DNL Experience Cloud] and [!DNL Analytics] visitor IDs. [Getmarketingcloudvisitorid](../../library/get-set/getmcvid.md)를 참조하십시오.

**&quot;aid&quot; 매개 변수는 이전 값입니다.**

`aid` 매개 변수는 2개의 다른 조건 세트 아래의 쿼리 문자열에 나타납니다. 

**사례 1**

다음 경우에 쿼리 문자열에 `aid` 매개 변수가 표시됩니다.

* [!DNL Experience Cloud] ID 서비스가 올바르게 배포됩니다.
* 사이트를 방문하는 사용자의 경우 기존 [!DNL Analytics] ID가 [s_vi 쿠키](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html)에 저장되어 있습니다.

**사례 2**

You will see the `aid` parameter in a query string when your organization is using a [grace period](../../reference/analytics-reference/grace-period.md) before fully implementing the ID service. If the user visiting your site is new, and you&#39;re not using a grace period, the visitor will get the `mid` ( [!DNL Experience Cloud] ID) parameter.

>[!MORE_ like_ this]
>
>* [Analytics 쿠키](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

