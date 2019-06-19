---
description: getInstance는 지정된 Experience Cloud 조직 ID에 대한 방문자 ID 개체를 반환합니다. 이 메서드는 s.visitor를 통해 AppMeasurement에 제공되는 방문자 ID 개체를 초기화하는 데 필요합니다.
keywords: ID 서비스
seo-description: getInstance는 지정된 Experience Cloud 조직 ID에 대한 방문자 ID 개체를 반환합니다. 이 메서드는 s.visitor를 통해 AppMeasurement에 제공되는 방문자 ID 개체를 초기화하는 데 필요합니다.
seo-title: getInstance
title: getInstance
uuid: 259 b 88 a 6-E 3 D 0-4 AAB-B 935-566099 BDAB 98
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# getInstance{#getinstance}

getInstance는 지정된 Experience Cloud 조직 ID에 대한 방문자 ID 개체를 반환합니다. 이 메서드는 s.visitor를 통해 AppMeasurement에 제공되는 방문자 ID 개체를 초기화하는 데 필요합니다.

**구문**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>*방문자 기능을 다음으로* `var visitor = new Visitor`인스턴스화하지 마십시오. 여기에 언급된 적절한 함수 호출을 사용해야 합니다. [!DNL VisitorAPI.js] 코드 라이브러리 v3.0 이상에 적용됩니다.

**ActionScript/Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

`getInstance`에서 기존 인스턴스를 찾지 못할 경우 새 인스턴스가 만들어진 후 반환됩니다. 이것은의 [`s_gi()` 함수와 ](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=function_s_gi.html) 유사합니다 [!DNL AppMeasurement].

**일반적인 사용**

[!DNL Experience Cloud] ID 서비스 API는 [!DNL Adobe Experience Cloud] 각 조직 ID에 대해 만들어진 모든 인스턴스 목록을 유지 관리합니다. ID 서비스 API를 사용하는 애플리케이션이 인스턴스에 대한 참조를 전달하지 않을 경우 새 인스턴스를 만들지 않고 `getInstance`를 호출하여 해당 인스턴스를 찾을 수 있습니다. 또한 동일한 웹 페이지 또는 애플리케이션에서 여러 다른 조직을 위한 여러 인스턴스를 지원합니다.

이 메서드는 명확한 `init` 단계가 없으나 여러 위치에서 ID 서비스 API를 호출해야 하는 애플리케이션에 유용합니다. 해당 모든 위치에서 `getInstance`를 호출할 수 있으며 첫 번째 실행에서 해당 인스턴스가 생성됩니다. 기존 인스턴스는 후속 호출에 의해 반환됩니다.
