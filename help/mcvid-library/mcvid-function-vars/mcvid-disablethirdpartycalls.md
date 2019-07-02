---
description: ID 서비스가 다른 도메인을 호출하지 않도록 방지하는 선택적 부울 플래그입니다.
keywords: 도메인 간 추적;ID 서비스
seo-description: ID 서비스가 다른 도메인을 호출하지 않도록 방지하는 선택적 부울 플래그입니다.
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCalls{#disablethirdpartycalls}

ID 서비스가 다른 도메인을 호출하지 않도록 방지하는 선택적 부울 플래그입니다.

**구문:** ` `disableThirdPartyCalls: true|false``(기본값은 `false`임)

`disableThirdPartyCalls: true`이면 ID 서비스는 다른 도메인을 호출하지 않습니다.

**용도**

이 변수는 다음과 같은 고객을 대상으로 합니다.

* ID 서비스가 사용자의 인증된 안전한 페이지에서 호출을 하지 않도록 하려는 고객
* 사이트 방문자가 Experience Cloud ID(MID)를 보유하도록 하려는 고객
* 다른 Experience Cloud 솔루션을 제대로 작동시키려는 고객

**구현 전략**

다른 Experience Cloud 솔루션은 MID를 사용하기 때문에 ID 서비스에서 Adobe를 호출하여 이 ID를 반환하고 설정합니다. 웹 사이트의 인증된 섹션에서 ID 서비스가 호출을 하지 않도록 해야 하는 경우, 먼저 인증이 필요하지 않은 페이지에서 ID 서비스가 이러한 필요한 호출을 수행하도록 합니다. 사이트 방문자가 MID를 보유하고 나면 사이트의 인증된 섹션에서 ID 서비스 코드에 `disableThirdPartyCalls= true`를 설정할 수 있습니다. 여기에서는 대부분의 고객이 사이트의 보안 부분에 액세스하기 전에 인증 페이지로 이동한다고 가정합니다.

**코드 샘플**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

