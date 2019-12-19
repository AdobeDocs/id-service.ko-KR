---
description: CSP(컨텐츠 보안 정책)는 브라우저에서 웹 페이지에 로드되는 리소스 유형에 대한 제어 권한을 제공하는 HTTP 헤더 및 보안 기능입니다. ID 서비스를 사용하며, 신뢰할 수 있는 도메인의 리소스를 승인하는 데 화이트리스트를 사용하는 엄격한 CSP가 있는 경우 이 섹션을 검토하십시오. 여기에 나열된 Adobe 도메인을 CSP 화이트리스트에 추가해야 합니다.
keywords: ID Service
seo-description: CSP(컨텐츠 보안 정책)는 브라우저에서 웹 페이지에 로드되는 리소스 유형에 대한 제어 권한을 제공하는 HTTP 헤더 및 보안 기능입니다. ID 서비스를 사용하며, 신뢰할 수 있는 도메인의 리소스를 승인하는 데 화이트리스트를 사용하는 엄격한 CSP가 있는 경우 이 섹션을 검토하십시오. 여기에 나열된 Adobe 도메인을 CSP 화이트리스트에 추가해야 합니다.
seo-title: 컨텐츠 보안 정책 및 Experience Cloud Identity 서비스
title: 컨텐츠 보안 정책 및 Experience Cloud Identity 서비스
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: ht
source-git-commit: fbfea06bc2a4493b6d9b84a8f367749e1d803650

---


# 컨텐츠 보안 정책 및 Experience Cloud Identity 서비스 {#content-security-policies-and-the-experience-cloud-id-service}

CSP(컨텐츠 보안 정책)는 브라우저에서 웹 페이지에 로드되는 리소스 유형에 대한 제어 권한을 제공하는 HTTP 헤더 및 보안 기능입니다. ID 서비스를 사용하며, 신뢰할 수 있는 도메인의 리소스를 승인하는 데 화이트리스트를 사용하는 엄격한 CSP가 있는 경우 이 섹션을 검토하십시오. 여기에 나열된 Adobe 도메인을 CSP 화이트리스트에 추가해야 합니다.

## CSP 검토 {#section-5fde5c00a678455c914b8307a8caab82}

CSP는 HTTP 헤더 `Content-Security-Policy`를 사용하여 브라우저에서 페이지에 허용하거나 로드하는 리소스 유형을 제어합니다. CSP를 적용하면 다음을 수행할 수 있습니다.

* 소스를 알 수 없거나 소스가 화이트리스트에 포함되지 않은 경우 JavaScript 파일을 로드하지 않습니다.
* 사이트 간 스크립팅(XXS) 공격을 방지합니다.
* 데이터 삽입 공격을 방지합니다.
* 사이트 손상 공격을 방지합니다.
* 악성코드 배포를 방지합니다.

CSP 사용이 일반적이며 잘 알려져 있습니다. 이 설명서의 목적은 CSP를 자세히 설명하는 것이 아닙니다(자세한 내용은 아래의 관련 정보 링크 참조). CSP와 Adobe 도메인 이름을 사용하고 엄격한 보안 정책을 사용하는 경우 CSP에 Adobe 도메인 이름을 추가해야 한다는 것을 알고 있는 것이 중요합니다. 이러한 도메인을 추가하면 사용자 사이트에 액세스하는 방문자 브라우저에서 사용자가 사용하는 Experience Cloud 리소스에 대한 중요한 호출을 할 수 있습니다.

## 화이트리스트에 작성할 Experience Cloud 도메인 {#section-30693e9a96834edfbf04de9e698cf2aa}

사용하는 각 Experience Cloud 솔루션 또는 서비스 목록에 대해 이러한 도메인 이름이나 URL을 CSP에 추가합니다.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud 솔루션 또는 서비스 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>다음을 포함하도록 CSP를 수정합니다. </p> <p> 
     <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B"> 
      <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"> <span class="codeph"> *.2o7.net</span> </li> 
      <li id="li_4B12A283716746949201528CD6AF529E"> <span class="codeph"> *.omtrdc.net</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Target</b> </p> </td> 
   <td colname="col2"> <p><span class="codeph">*.tt.omtrdc.net</span>을 포함하도록 CSP를 수정합니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>방문자 ID 서비스</b> </p> </td> 
   <td colname="col2"> <p><span class="codeph">*.demdex.net</span>을 포함하도록 CSP를 수정합니다. </p> <p><span class="codeph">demdex.net</span> 도메인 호출은 <a href="../introduction/cookies.md" format="dita" scope="local">쿠키 및 Experience Cloud Identity 서비스</a>를 생성하고 ID를 동기화하는 데 사용됩니다. <a href="https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html" format="https" scope="external">Demdex 도메인에 대한 호출 이해</a>도 참조하십시오. </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Activity Map 플러그인</b> </p> </td> 
 <td colname="col2"> <p>CSP가 *omniture.com을 포함하도록 수정합니다. </p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>
>* [컨텐츠 보안 정책 참조](https://content-security-policy.com/)
>* [MDN: 컨텐츠 보안 정책](https://developer.mozilla.org/ko-KR/docs/Web/HTTP/CSP)
>* [Wikipedia: 컨텐츠 보안 정책](https://en.wikipedia.org/wiki/Content_Security_Policy)

