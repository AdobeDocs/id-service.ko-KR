---
description: 브라우저가 Experience Cloud Identity 서비스에서 리소스를 요청하는 방법을 제어하는 선택적 부울 플래그입니다.
keywords: ID 서비스
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
TQID: https://experienceleague.adobe.com/QMYUbL2y8X5gSUcLmYnKZnp5mfEu7-uiogOx3rx2dkY
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 145
ht-degree: 87%

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

