---
description: ID 서비스 사용과 관련된 기능 및 문제에 대한 FAQ입니다.
keywords: ID 서비스
seo-description: ID 서비스 사용과 관련된 기능 및 문제에 대한 FAQ입니다.
seo-title: ID 서비스 FAQ
title: ID 서비스 FAQ
uuid: E 8 D 8 F 819-3 D 73-4 FA 2-864 C -4867071 C 14 EE
translation-type: tm+mt
source-git-commit: 4dc668afd37cd1d6f9104adb1b102f1dd4c5746e

---


# ID 서비스 FAQ{#id-service-faqs}

ID 서비스 사용과 관련된 기능 및 문제에 대한 FAQ입니다.

## 기능 {#section-659e89f8b9a74cb8afff35587dc96836}

**ID 서비스에서 제공하는 기능에는 어떤 것이 있습니까?**

자세한 내용은 [개요](../mcvid-introduction/mcvid-overview.md).

**ID 서비스에서 Experience Cloud ID를 검색하도록 호출할 수 없는 이유는 무엇입니까?**

진단하기 어려울 수 있습니다. 확인할 수 있는 한 가지는 사이트의 컨텐츠 보안 정책 헤더입니다. 엄격한 보안 정책이 있는 경우 그러한 설정은 ID 서비스에서 보낸 타사 호출을 차단할 수 있습니다. 자세한 내용은 [컨텐츠 보안 정책 및 Experience Cloud ID 서비스](../mcvid-reference/mcvid-csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**VisitorAPI.js 파일 저장소**

모바일 앱에서 VisitorAPI.js를 로컬 파일로 호스트하는 경우 문제가 발생할 수 있습니다. 웹 서버에 파일을 호스트하는 것이 좋습니다.

## 페이지 로드 시간 및 지연 {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**ID 서비스 VisitorAPI.js 라이브러리의 배치가 페이지 로드 시간에 어떻게 영향을 줍니까?**

코드 `<head>` 섹션의 페이지 상단에 Visitorapi. js 라이브러리를 배치합니다. 이렇게 하면 페이지 본문 로드가 시작되기 전에 ID에 대한 호출이 종료되고 ID가 성공적으로 반환되는 기회를 최대화하는 데 도움이 됩니다.

ID 서비스 호출은 비동기적이며 [demdex.net 도메인](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)에 대한 유일한 호출입니다. ID 서비스 호출은 다른 요소가 페이지에서 로드되는 것을 차단하지 않습니다.

[!DNL Target] 고객의 경우, 페이지 안에 ID 서비스 `<body>` 코드를 삽입하면 [!DNL Target] 호출이 차단될 수 있습니다. 페이지 본문에 ID 서비스 코드를 배치해야 하는 경우 open `<body>` 태그 뒤에 삽입해야 합니다.

**ID 서비스가 모든 페이지 로드와 함께 서버 호출을 수행합니까?**

아니요, 이 호출은 처음으로 페이지를 렌더링할 때만 발생하고, 이후에는 7일마다 한 번씩 발생합니다. 그동안 서버 호출은 필요하지 않습니다. ID 서비스가 클라이언트측 모드에서 작동하므로 ID를 반환하기 위해 서버를 호출할 필요가 없습니다.

자세한 내용은 [개요](../mcvid-introduction/mcvid-overview.md).

**ID 서비스를 사용할 때 페이지 로드 시간이 느려지거나 사용자 환경에 영향을 줄 수 있는 것은 무엇입니까?**

가능한 조건을 모두 작성하기가 어렵습니다. 수십억의 소비자 클라이언트가 Adobe 서비스에 연결하면 이들이 연결하는 수많은 위치와 방식이 성능에 영향을 미칩니다. 예:

* 모바일 네트워크에서 속도가 크게 달라집니다. 또한 이러한 네트워크에서는 신호 및 데이터 또는 음성 패킷 손실이 발생합니다.
* 다양한 조건으로 WiFi를 통해 연결되는 장치에는 연결 문제가 발생합니다. 예를 들어 패킷 손실 및 속도 문제는 커피숍과 같은 공공장소나, 패킷이 지상파 네트워크에 도달하기 전에 위성을 통해 반송해야 같은 항공기와 같은 다른 환경에서 일반적으로 발생합니다.
* 잘못 구성된 로컬 네트워크는 연결 및 속도에 부정적인 영향을 줄 수 있습니다.
* 클라이언트 장치에는 현재 워크로드에 비해 메모리 부족, 과도한 디스크 교체 또는 제한된 CPU 전원과 같은 고유한 문제가 있을 수 있습니다.
* 브라우저는 원격 서버 호출을 큐에 넣고 실행하며, 브라우저 메이커 및 버전에 따라 다른 규칙을 사용하여 응답을 처리합니다. 이 동작은 속도와 성능에 영향을 줍니다.

**페이지 로드 시간을 줄이기 위한 몇 가지 개선 사항의 이름을 지정할 수 있습니까?**

스레드 생성을 예로 들 수 있습니다. 여러 ID 동기화를 요청하는 경우 스레드 생성을 도입했습니다. 연구 보고서에 따르면 여러 ID 동기화를 수행하는 고객의 경우 연속 CPU 계산이 많이 발생하므로 UI가 차단되는 것을 알 수 있습니다. 따라서 스레드 생성을 도입하여 ID 동기화 요청을 각각 100초로 구분했습니다.

이러한 변경으로 Visitor 2.3.0+ 및 DIL 6.10+를 사용하는 고객의 성능이 향상됩니다. 아래 그림에 향상된 페이지 로드 시간이 표시되어 있습니다.

![](assets/id_sync_improvements_copy.png)

**CORS와 JSON-P를 사용하는 브라우저의 요청이 페이지 성능에 영향을 줍니까?**

CORS를 사용한 리소스 요청이 JSONP를 사용한 요청보다 더 많이 사용됩니다. JSONP를 사용하는 경우 일부 브라우저에서는 페이지의 다른 동기 및 비동기 호출을 기준으로 하여 요청을 큐에 넣고 우선 순위를 낮게 지정합니다. CORS는 이러한 요청이 브라우저 호출 스택에서 우선 순위가 더 높은 것으로 처리되도록 합니다.

자세한 내용은 [Experience Cloud ID 서비스의 CORS 지원](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## 보안 {#section-b176b8492fbe4acfb79ebb30ec902f98}

**ID 서비스에서 CORS를 지원합니까?**

예. Experience Cloud ID 서비스에서 [CORS 지원을 참조하십시오](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**CORS란 무엇입니까?**

*`Cross-Origin Resource Sharing`* 또는 CORS는 브라우저에서 리소스를 요청하는 데 사용하는 메서드입니다. ID 서비스는 항상 지원하는 브라우저에서 CORS를 사용하여 리소스를 요청합니다. ID 서비스는 요청은 CORS를 지원하지 않는 이전 브라우저에서 JSON-P를 사용하여 리소스를 요청합니다. 자세한 내용은 [Experience Cloud](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**보안 요구 사항이 너무 엄격하여 JSONP를 사용하지 않을 경우 어떻게 됩니까?**

엄격한 보안 요구 사항이 있는 경우 ID 서비스 API 구성 `useCORSOnly: true`를 설정합니다. 사이트 방문자가 CORS를 지원하는 브라우저를 사용하는 경우에만 이 모드를 사용해야 합니다.

자세한 내용은 [Experience Cloud](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758) 및 [usecorsonly](../mcvid-library/mcvid-function-vars/mcvid-use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORE_ like_ this]
>
>* [고객 지원](https://helpx.adobe.com/marketing-cloud/contact-support.html)에 문의하십시오

