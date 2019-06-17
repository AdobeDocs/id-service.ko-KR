---
description: 이러한 지침, 도구 및 절차를 통해 ID 서비스가 제대로 작동하는지 확인할 수 있습니다. 이러한 테스트는 일반적으로 ID 서비스에 적용되며, 다른 ID 서비스 및 Experience Cloud 솔루션 조합을 위한 것입니다.
keywords: ID 서비스
seo-description: 이러한 지침, 도구 및 절차를 통해 ID 서비스가 제대로 작동하는지 확인할 수 있습니다. 이러한 테스트는 일반적으로 ID 서비스에 적용되며, 다른 ID 서비스 및 Experience Cloud 솔루션 조합을 위한 것입니다.
seo-title: Experience Cloud ID 서비스 테스트 및 확인
title: Experience Cloud ID 서비스 테스트 및 확인
uuid: 442 DE 9 C 3-C 265-4412-89 BD-AEAA 286 DDAD 6
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Experience Cloud ID 서비스 테스트 및 확인{#test-and-verify-the-experience-cloud-id-service}

이러한 지침, 도구 및 절차를 통해 ID 서비스가 제대로 작동하는지 확인할 수 있습니다. 이러한 테스트는 일반적으로 ID 서비스에 적용되며, 다른 ID 서비스 및 Experience Cloud 솔루션 조합을 위한 것입니다.

## 시작하기 전에 {#section-b1e76ad552ed4eb793b6e521a55127d4}

ID 서비스를 테스트하고 확인하기 전에 알아야 할 중요한 정보입니다.

**브라우저 환경**

일반적인 브라우저 환경에서 테스트할 때는 테스트 전에 브라우저 캐시를 지웁니다.

익명 또는 시크릿 브라우저 세션에서 ID 서비스를 테스트할 수도 있습니다. 익명 세션에서는 각 테스트를 수행하기 전에 브라우저 쿠키 또는 캐시를 지울 필요가 없습니다.

**도구**

[ Adobe 디버거](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html) 및 [Charles HTTP 프록시](https://www.charlesproxy.com/)는 ID 서비스가 Analytics에서 제대로 작동하도록 구성되었는지 확인하는 데 도움이 됩니다. 이 섹션의 정보는 Adobe 디버거 및 Charles에서 반환한 결과를 기반으로 합니다. 하지만 가장 적합한 도구나 디버거를 자유롭게 사용할 수 있습니다.

## Adobe 디버거로 테스트하기 {#section-861365abc24b498e925b3837ea81d469}

디버거 응답 (mid) 를 보면 서비스 통합이 [!DNL Experience Cloud ID] 올바르게 [!DNL Adobe] 구성됩니다. MID에 대한 자세한 내용은 [쿠키 및 Experience Cloud ID 서비스를](../mcvid-introduction/mcvid-cookies.md) 참조하십시오.

디버거가 있는 ID 서비스의 상태를 확인하려면 [!DNL Adobe][](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html)다음을 수행하십시오.

1. 브라우저 쿠키를 지우거나 익명의 브라우저 세션을 엽니다.
1. ID 서비스 코드가 포함된 테스트 페이지를 로드합니다.
1. [!DNL Adobe] 디버거를 엽니다.
1. MID 결과를 확인합니다.

## Adobe Debugger 결과 이해 {#section-bd2caa6643d54d41a476d747b41e7e25}

mid는 다음 구문을 사용하는 키-값 쌍에 저장됩니다. `MID= *`Experience Cloud ID`*`. 디버거는 이 정보를 다음과 같이 표시합니다.

**성공**

다음과 유사한 응답이 표시되면 ID 서비스가 제대로 구현된 것입니다.

```
mid=20265673158980419722735089753036633573
```

[!DNL Analytics] 고객인 경우 MID 외에 AID([!DNL Analytics] ID)가 표시될 수 있습니다. 다음과 같은 경우 발생합니다.

* 초기/장기 사이트 방문자가 있는 경우
* 유예 기간을 활성화한 경우

**실패**

디버거가 다음과 같은 경우 [고객 지원 센터](https://helpx.adobe.com/marketing-cloud/contact-support.html)에 문의하십시오.

* MID를 반환하지 않는 경우
* 파트너 ID가 프로비저닝되지 않았다는 오류 메시지가 반환되는 경우

## Charles HTTP 프록시를 사용한 테스트 {#section-d9e91f24984146b2b527fe059d7c9355}

Charles에서 ID 서비스 상태를 확인하려면

1. 브라우저 쿠키를 지우거나 익명의 브라우저 세션을 엽니다.
1. Charles를 시작합니다.
1. ID 서비스 코드가 포함된 테스트 페이지를 로드합니다.
1. 요청 및 응답 호출과 아래에 설명된 데이터를 확인합니다.

## Charles 결과 이해 {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Charles를 사용하여 HTTP 호출을 모니터링할 때 살펴볼 위치와 찾을 내용, 사용할 시기에 대한 정보는 이 섹션을 참조하십시오.

**Charles에서 ID 서비스 요청 성공**

`Visitor.getInstance` 함수가 `dpm.demdex.net`에 JavaScript 호출을 수행하면 ID 서비스 코드가 제대로 작동하는 것입니다. 성공적인 요청에는 [조직 ID](../mcvid-reference/mcvid-requirements.md#section-a02f537129a64ffbb690d5738d360c26)가 포함되어 있습니다. 조직 ID는 다음 구문을 사용하는 키-값 쌍으로 전달됩니다. `d_orgid= *`조직 ID`*`. 탭 아래의 `dpm.demdex.net` 및 JavaScript 호출을 [!DNL Structure] 찾습니다. 탭 아래에서 조직 ID [!DNL Request] 를 찾습니다.

![](assets/charles_request.png)

**Charles에서 성공적인 ID 서비스 응답**

[DCS(데이터 수집 서버)](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html)의 응답에서 MID를 반환하면 계정이 ID 서비스에 대해 제대로 프로비저닝된 것입니다. mid는 이 구문을 사용하는 키-값 쌍으로 반환됩니다. `d_mid: *`방문자 Experience Cloud ID`*`. 아래에서 보듯이 [!DNL Response] 탭에서 MID를 찾습니다.

![](assets/charles_response_success.png)

**Charles에서 실패한 ID 서비스 응답**

DCS 응답에서 MID가 누락된 경우 계정이 제대로 프로비저닝되지 않은 것입니다. 실패한 응답은 아래와 같이 [!DNL Response] 탭의 오류 코드와 메시지를 반환합니다. DCS 응답에서 이 오류 메시지가 표시되면 고객 지원 센터에 문의하십시오.

![](assets/charles_response_unsuccessful.png)

오류 코드에 대한 자세한 정보는 [DCS 오류 코드, 메시지 및 예제](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html)를 참조하십시오.
