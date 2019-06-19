---
description: CORS(교차 도메인 리소스 공유)를 사용하면 브라우저에서 현재 도메인 이외의 도메인으로부터 리소스를 요청할 수 있습니다. Experience Platform Identity Service는 이러한 클라이언트측 교차 리소스 요청을 활성화하는 CORS 표준을 지원합니다. ID 서비스는 오래된 브라우저나 CORS를 지원하지 않는 브라우저에서는 JSONP 요청으로 되돌립니다.
keywords: ID 서비스
seo-description: CORS(교차 도메인 리소스 공유)를 사용하면 브라우저에서 현재 도메인 이외의 도메인으로부터 리소스를 요청할 수 있습니다. Experience Platform Identity Service는 이러한 클라이언트측 교차 리소스 요청을 활성화하는 CORS 표준을 지원합니다. ID 서비스는 오래된 브라우저나 CORS를 지원하지 않는 브라우저에서는 JSONP 요청으로 되돌립니다.
seo-title: 경험 플랫폼 ID 서비스의 CORS 지원
title: 경험 플랫폼 ID 서비스의 CORS 지원
uuid: E 656 B 573-72 A 8-4312-A 7 D 5-5 CC 3818 F 0 A 9 E
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# 경험 플랫폼 ID 서비스의 CORS 지원 {#cors-support-in-the-experience-cloud-id-service}

CORS(교차 도메인 리소스 공유)를 사용하면 브라우저에서 현재 도메인 이외의 도메인으로부터 리소스를 요청할 수 있습니다. Experience Platform Identity Service는 이러한 클라이언트측 교차 리소스 요청을 활성화하는 CORS 표준을 지원합니다. ID 서비스는 오래된 브라우저나 CORS를 지원하지 않는 브라우저에서는 JSONP 요청으로 되돌립니다.

## 동일 출처 정책 및 ID 서비스 요청 문제 {#section-6608cf46d27143eeaeabacaa6aa14e8e}

동일 출처 정책은 웹 브라우저에서 시행하는 보안 제어 또는 제한 사항입니다. 이 수준에서 시행되면 웹 브라우저 자체가 한 페이지에서 다른 페이지로 작성된 리소스에 대한 요청이 허용되는지 또는 차단되는지 여부를 확인합니다. 요청이 동일 출처 요청인지 확인하기 위해 브라우저는 다음 항목을 비교합니다.

* URI(Uniform Resource Identifier)
* 호스트명(예: http://www.my-webpage-example.com)
* 포트 번호(예: HTTP 및 HTTPS 요청용 포트 80 및 440)

브라우저는 두 페이지 모두 이러한 특성을 공유하는 경우 요청이 성공하도록 허용하고 그렇지 않은 경우 리소스 요청을 차단합니다.

## CORS를 통한 동일 출처 정책 문제 해결 {#section-76c87ec3295d447bab220c84f138c235}

CORS는 여러 도메인에서 리소스를 요청할 수 있는 안전하고 효율적인 방법을 제공합니다. CORS 사양에는 브라우저가 리소스 요청을 송신, 수신 및 평가하는 데 사용하는 HTTP 헤더 세트가 포함되어 있습니다. 리소스 요청을 평가하는 것은 *`preflight check`*. 이 검사를 통해 브라우저와 서버에서는 어떤 요청이 허용 또는 차단되는지를 확인합니다. Preflight 검사는 리소스를 요청하는 앱, API 또는 스크립트에 대해 투명합니다. 리소스 요청 프로세스에서 중요한 두 개의 헤더는 다음과 같습니다.

* `Origin`: 요청의 소스를 식별하는 요청 헤더입니다.
* `Access-Control-Allow-Origin`: 리소스를 요청자와 공유할 수 있는지 나타내는 응답 헤더입니다.

이러한 헤더가 어떻게 작동하는지 살펴보겠습니다. 이 예제에서는 [!DNL Experience Cloud] ID 서비스를 사이트(www.finance-website.com)에 구현한 금융 서비스 회사가 있다고 가정합니다. 다음 표에는 CORS 요청 및 응답 헤더가 리소스에 대한 액세스를 확인하는 방법이 정의되어 있습니다.

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 작업 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>요청</b> </p> </td> 
   <td colname="col2"> <p>금융 회사의 페이지가 로드되어 브라우저에서 <span class="codeph">dpm.demdex.net</span>에 요청을 합니다. 이는 ID 서비스에서 사용하는 DCS(데이터 수집 서버)의 도메인에 대한 호출입니다. 이 도메인 간 요청에는 다음 헤더가 포함됩니다. </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin:https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>응답</b> </p> </td> 
   <td colname="col2"> <p>DCS 도메인의 응답에는 금융 회사의 사이트에 필요한 리소스에 대한 액세스 권한을 제공하는 다음 헤더가 포함됩니다. </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

[Usecorsonly를 참조하십시오](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

## CORS 사용의 기타 이점 {#section-6f44f30694c44f95bf9854b8a2af8449}

아래 표에는 CORS가 ID 서비스를 사용하는 고객에게 제공하는 몇 가지 이점이 설명되어 있습니다.

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 이점 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>보안 강화</b> </p> </td> 
   <td colname="col2"> <p>CORS는 <a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a>를 사용하여 데이터를 요청하고 전송합니다. 이 방법은 JSONP 요청보다 더 안전하며 DCS의 응답에 포함될 수 있는 임의의 JavaScript를 실행할 수 있는 방법이 없도록 보장합니다. CORS XMLHttpRequest 응답 페이로드는 ID 서비스 JavaScript에 의해 구문 분석되며 콜백 함수에서 실행되지 않습니다. </p> <p> <p>참고: 쿠키를 허용하려면 <span class="codeph">XMLHttpRequest</span> 개체의 <span class="codeph">withCredentials</span> 속성이 <span class="codeph">true</span>로 설정되어 있어야 합니다. 이 속성은 Chrome, Firefox, Internet Explorer(버전 10 이상), Opera 및 Safari에서 지원됩니다. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>성능 향상</b> </p> </td> 
   <td colname="col2"> <p>CORS는 다음과 같은 이유로 성능 향상에 도움이 됩니다. </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">브라우저가 리소스 요청을 관리합니다. 요청 프로세스는 ID 서비스에 대해 투명합니다. </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">비동기 JSONP 요청과 달리 브라우저가 CORS 요청의 우선순위를 결정하지 않고 큐에 넣지 않습니다. </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">ID 서비스가 허용적으로 응답합니다. 즉, URL이 <span class="codeph">Origin</span>으로 전달되면 ID 서비스에서 요청한 리소스에 대한 페이지 액세스를 허용합니다. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
