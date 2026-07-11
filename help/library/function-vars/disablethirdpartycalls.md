---
description: 방문자 ID 서비스가 다른 도메인을 호출하지 않도록 방지하는 선택적 부울 플래그입니다.
keywords: 도메인 간 추적;방문자 ID 서비스
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
TQID: https://experienceleague.adobe.com/mv00QfToxSqeITADmY1LbihbtJNHf1zzQef9uKDu-dc
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 205
ht-degree: 24%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

방문자 ID 서비스가 다른 도메인을 호출하지 않도록 방지하는 선택적 부울 플래그입니다.

**구문:** ` `disableThirdPartyCalls: true|false``(기본값은 `false`임)

`disableThirdPartyCalls: true`일 때 방문자 ID 서비스는 다른 도메인을 호출하지 않습니다.

**용도**

이 변수는 다음과 같은 고객을 위해 설계되었습니다.

* 방문자 ID 서비스가 안전하고 인증된 페이지에서 호출을 하지 못하도록 하는 방법.
* ECID가 있는 사이트 방문자입니다.
* 다른 CX 엔터프라이즈 솔루션도 제대로 작동합니다.

**구현 전략**

다른 CX 엔터프라이즈 솔루션은 MID에 의존하기 때문에 방문자 ID 서비스는 Adobe을 호출하여 이 ID를 반환하고 설정합니다. 방문자 ID 서비스가 웹 사이트의 인증된 섹션에서 호출을 하지 않도록 해야 하는 경우, 먼저 인증이 필요하지 않은 페이지에서 이러한 필요한 호출을 수행하도록 합니다. 사이트 방문자가 MID를 보유하고 나면 사이트의 인증된 섹션에서 방문자 ID 서비스 코드에 `disableThirdPartyCalls= true`을(를) 설정할 수 있습니다. 여기에서는 모두는 아니더라도 대부분의 고객들이 사이트의 보안 부분에 액세스하기 전에 인증 페이지로 이동할 것이라고 가정합니다.

**코드 샘플**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

