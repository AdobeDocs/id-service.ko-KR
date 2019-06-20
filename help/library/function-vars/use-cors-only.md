---
description: 브라우저가 Experience Cloud ID 서비스에서 리소스를 요청하는 방법을 제어하는 부울 플래그 (선택 사항) 입니다.
keywords: ID 서비스
seo-description: 브라우저가 Experience Cloud ID 서비스에서 리소스를 요청하는 방법을 제어하는 부울 플래그 (선택 사항) 입니다.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607 DC 035-DFFC -4 F 4 D-BE 51-08 EF 6 C 0 A 8 FAD
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# useCORSOnly{#usecorsonly}

브라우저가 Experience Cloud ID 서비스에서 리소스를 요청하는 방법을 제어하는 부울 플래그 (선택 사항) 입니다.

**구문:**`useCORSOnly: true|false` (기본값은 `false`.)

**개요**

`false`로 설정하면 브라우저가 CORS 또는 JSONP로 리소스 확인을 수행합니다. 하지만 ID 서비스는 항상 CORS로 먼저 리소스 요청을 시도합니다. ID 서비스는 CORS를 지원하지 않는 오래된 브라우저에서는 JSONP로 되돌립니다. 브라우저에서 CORS만 사용해야 하는 경우, `useCORSOnly:true` 함수 호출에 `Visitor.getInstance`를 설정합니다.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` 엄격한 보안 요구 사항이 있는 경우 모든 방문자가 CORS를 지원하는 브라우저를 사용한다고 확신하는 경우에만 이 모드를 활성화해야 합니다. 사용자 경험은 CORS를 지원하지 않는 브라우저의 영향을 받지 않습니다. 하지만 CORS를 지원하지 않는 브라우저에서는 리소스를 요청하거나 [!DNL Adobe Experience Cloud]와 데이터를 교환할 수 없습니다.

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

