---
description: COPPA(온라인 아동 개인 정보 보호법 - Children’s Online Privacy Protection Act)에서는 입증할 수 있는 부모의 동의 없이 13세 미만의 어린이로부터 온라인으로 개인 정보를 수집하는 것을 금지합니다. COPPA를 중요하게 생각하는 고객은 브라우저의 타사 도메인에서 쿠키를 설정하지 못하도록 하는 옵션 변수를 Experience Cloud ID 서비스 코드에 추가할 수 있습니다.
keywords: ID 서비스
seo-description: COPPA(온라인 아동 개인 정보 보호법 - Children’s Online Privacy Protection Act)에서는 입증할 수 있는 부모의 동의 없이 13세 미만의 어린이로부터 온라인으로 개인 정보를 수집하는 것을 금지합니다. COPPA를 중요하게 생각하는 고객은 브라우저의 타사 도메인에서 쿠키를 설정하지 못하도록 하는 옵션 변수를 Experience Cloud ID 서비스 코드에 추가할 수 있습니다.
seo-title: Experience Cloud ID 서비스의 COPPA 지원
title: Experience Cloud ID 서비스의 COPPA 지원
uuid: 621 B 5 EBD -92 E 7-4635-BE 85-8 D 7 E 36589 FCB
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Experience Cloud ID 서비스의 COPPA 지원 {#coppa-support-in-the-experience-cloud-id-service}

COPPA(온라인 아동 개인 정보 보호법 - Children’s Online Privacy Protection Act)에서는 입증할 수 있는 부모의 동의 없이 13세 미만의 어린이로부터 온라인으로 개인 정보를 수집하는 것을 금지합니다. COPPA를 중요하게 생각하는 고객은 브라우저의 타사 도메인에서 쿠키를 설정하지 못하도록 하는 옵션 변수를 Experience Cloud ID 서비스 코드에 추가할 수 있습니다.

>[!NOTE]
>
>버전 1.5.3 이상

**쿠키 및 추적**

웹 페이지가 로드되면 [!DNL Experience Cloud] ID 서비스는 [!DNL Adobe] 데이터 수집 서버(DCS)를 호출합니다. DCS 응답에는 Experience Cloud 쿠키와 demdex.net 쿠키가 포함되어 있습니다.

* Experience Cloud 쿠키는 퍼스트 파티 도메인에서 설정됩니다. 해당 도메인이 액세스를 허용하기 위해 함께 작동하지 않는 한, 여러 다른 도메인에서 방문자를 추적하는 데 사용할 수 없습니다.
* demdex.net 쿠키는 타사 도메인에서 설정됩니다. 여기에는 다양한 도메인의 방문자를 추적하는 데 사용할 수 있는 고유한 식별자가 포함되어 있습니다.

**쿠키 및 COPPA 규격**

주로 아이들을 대상으로 하는 웹 사이트의 여러 다양한 도메인에서 방문자를 추적하는 타사 쿠키는 COPPA 보호자 동의 요구 사항을 트리거합니다. 내부 웹 사이트 분석을 위해 COPPA를 보다 쉽게 준수하려면 아래에 표시된 것처럼 변수 `disableThirdPartyCookies:true`를 `Visitor.getInstance` 함수에 추가합니다.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

`true`로 설정되면 `disableThirdPartyCookies` 개체는 DCS가 타사의 demdex.net 쿠키를 반환하지 않게 합니다. 사이트 방문자의 브라우저에 이미 이 쿠키가 있는 경우 ID 서비스에서 새 [!DNL Experience Cloud] ID를 만들거나 기존 ID를 반환하는 데 이 쿠키를 사용하지 않습니다. 대신 [!DNL Experience Cloud] ID 서비스는 퍼스트 파티 쿠키에 새로운 무작위 ID를 만듭니다. 사용하도록 설정하면 ID 서비스를 사용하여 데이터를 수집한 후, COPPA에서 허용한 다른 내부 작업을 비롯하여 다양한 [!DNL Experience Cloud] 솔루션에서 공유할 수 있습니다.

>[!MORE_ like_ this]
>
>* [Adobe 개인 정보 보호 센터](http://www.adobe.com/privacy.html)
>* [COPPA란?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

