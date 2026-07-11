---
description: COPPA(온라인 아동 개인 정보 보호법 - Children's Online Privacy Protection Act)에서는 입증할 수 있는 부모의 동의 없이 13세 미만의 어린이로부터 온라인으로 개인 정보를 수집하는 것을 금지합니다. COPPA를 중요하게 생각하는 고객은 원하는 경우 브라우저의 타사 도메인에서 쿠키를 설정하지 못하도록 하는 변수를 자신의 방문자 ID 서비스 코드에 추가할 수 있습니다.
keywords: 방문자 ID 서비스
title: Adobe 방문자 ID 서비스의 COPPA 지원
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
TQID: https://experienceleague.adobe.com/szz7syrA2KSDasXTox02PTbxBy60tfFc80hHmsjXwc0
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 363
ht-degree: 36%

---

# Adobe 방문자 ID 서비스의 COPPA 지원 {#coppa-support-in-the-experience-cloud-id-service}

COPPA(온라인 아동 개인 정보 보호법 - Children&#39;s Online Privacy Protection Act)에서는 입증할 수 있는 부모의 동의 없이 13세 미만의 어린이로부터 온라인으로 개인 정보를 수집하는 것을 금지합니다. COPPA를 중요하게 생각하는 고객은 원하는 경우 브라우저의 타사 도메인에서 쿠키를 설정하지 못하도록 하는 변수를 자신의 방문자 ID 서비스 코드에 추가할 수 있습니다.

>[!NOTE]
>
>버전 3.0.0 이상

**쿠키 및 추적**

웹 페이지가 로드되면 방문자 ID 서비스는 Adobe 데이터 수집 서버(DCS)를 호출합니다. DCS 응답에는 CX Enterprise 쿠키 및 demdex.net 쿠키가 포함됩니다.

* CX 엔터프라이즈 쿠키는 자사 도메인에 설정됩니다. 여러 다른 도메인이 액세스를 허용하기 위해 함께 작동하지 않는 한 해당 도메인에서 방문자를 추적하는 데 사용할 수 없습니다.
* demdex.net 쿠키는 서드파티 도메인에서 설정됩니다. 여기에는 여러 도메인에서 방문자를 추적하는 데 사용할 수 있는 고유 식별자가 포함되어 있습니다.

**쿠키 및 COPPA 규정 준수**

어린이를 대상으로 하는(또는 주로 어린이를 대상으로 하는) 웹 사이트에서 여러 도메인의 방문자를 추적하는 서드파티 쿠키는 COPPA 부모 동의 요구 사항을 트리거합니다. 내부 웹 사이트 분석을 위해 COPPA를 보다 쉽게 준수하려면 아래에 표시된 것처럼 변수 `disableThirdPartyCookies:true`를 `Visitor.getInstance` 함수에 추가합니다.

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

`true`로 설정되면 `disableThirdPartyCookies` 개체는 DCS가 서드파티의 demdex.net 쿠키를 반환하지 않게 합니다. 사이트 방문자의 브라우저에 이미 이 쿠키가 있는 경우 방문자 ID 서비스 는 이 쿠키를 사용하여 새 ECID를 만들거나 기존 ID를 반환하지 않습니다. 대신 방문자 ID 서비스는 퍼스트 파티 쿠키에 새로운 무작위 ID를 만듭니다. 활성화되면 방문자 ID 서비스 로 데이터를 수집하고 COPPA에서 허용하는 다른 내부 작업을 포함하여 다양한 CX 엔터프라이즈 솔루션에서 공유할 수 있습니다.

>[!MORELIKETHIS]
>
>* [Adobe 개인정보 보호 센터](https://www.adobe.com/kr/privacy.html)
>* [COPPA란?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

