---
description: 브라우저가 Experience Cloud Identity 서비스에서 리소스를 요청하는 방법을 제어하는 선택적 부울 플래그입니다.
keywords: ID 서비스
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 100%

---

# useCORSOnly{#usecorsonly}

브라우저가 Experience Cloud Identity 서비스에서 리소스를 요청하는 방법을 제어하는 선택적 부울 플래그입니다.

**구문:** `useCORSOnly: true|false` (기본값은 `false`임)

**개요**

`false`로 설정하면 브라우저가 CORS 또는 JSONP로 리소스 확인을 수행합니다. 그러나 ID 서비스는 항상 먼저 CORS를 사용하여 리소스 요청을 시도합니다. CORS를 지원하지 않는 이전 브라우저에서는 JSONP로 되돌아갑니다. 브라우저에서 CORS만 사용해야 하는 경우, `useCORSOnly:true` 함수 호출에 `Visitor.getInstance`를 설정합니다.

>[!IMPORTANT]
>
>보안 요구 사항이 엄격하면 `Set useCORSOnly: true`입니다. 모든 방문자가 CORS를 지원하는 브라우저를 사용한다고 확신하는 경우에만 이 모드를 활성화해야 합니다. 사용자 경험은 CORS를 지원하지 않는 브라우저의 영향을 받지 않습니다. 하지만 CORS를 지원하지 않는 브라우저에서는 리소스를 요청하거나 [!DNL Adobe Experience Cloud]와 데이터를 교환할 수 없습니다.

**코드 샘플**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```
