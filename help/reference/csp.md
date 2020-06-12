---
description: CSP(Content Security Policy)는 브라우저가 웹 페이지에 로드되는 리소스 유형을 제어하는 HTTP 헤더 및 보안 기능입니다. ID 서비스를 사용하고 신뢰할 수 있는 도메인의 리소스를 수락하기 위해 허용 목록을 사용하는 엄격한 CSP가 있는 경우 이 섹션을 검토하십시오. 여기에 나열된 Adobe 도메인을 CSP 허용 목록에 추가해야 합니다.
keywords: ID Service
seo-description: CSP(Content Security Policy)는 브라우저가 웹 페이지에 로드되는 리소스 유형을 제어하는 HTTP 헤더 및 보안 기능입니다. ID 서비스를 사용하고 신뢰할 수 있는 도메인의 리소스를 수락하기 위해 허용 목록을 사용하는 엄격한 CSP가 있는 경우 이 섹션을 검토하십시오. 여기에 나열된 Adobe 도메인을 CSP 허용 목록에 추가해야 합니다.
seo-title: 컨텐츠 보안 정책 및 Experience Cloud Identity 서비스
title: 컨텐츠 보안 정책 및 Experience Cloud Identity 서비스
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: ht
source-git-commit: acf10dd734132662698791e473c1f3f4dda85d67
workflow-type: ht
source-wordcount: '619'
ht-degree: 100%

---


# 컨텐츠 보안 정책 및 Experience Cloud Identity 서비스 {#content-security-policies-and-the-experience-cloud-id-service}

CSP(Content Security Policy)는 브라우저가 웹 페이지에 로드되는 리소스 유형을 제어하는 HTTP 헤더 및 보안 기능입니다. ID 서비스를 사용하고 신뢰할 수 있는 도메인의 리소스를 수락하기 위해 허용 목록을 사용하는 엄격한 CSP가 있는 경우 이 섹션을 검토하십시오. 여기에 나열된 Adobe 도메인을 CSP 허용 목록에 추가해야 합니다.

## CSP 검토 {#section-5fde5c00a678455c914b8307a8caab82}

CSP는 HTTP 헤더 `Content-Security-Policy`를 사용하여 브라우저에서 페이지에 허용하거나 로드하는 리소스 유형을 제어합니다. CSP를 적용하면 다음을 방지할 수 있습니다.

* 소스를 알 수 없거나 허용 목록에 포함되지 않은 경우 JavaScript 파일이 로드됨.
* XXS(교차 사이트 스크립팅) 공격.
* 데이터 주입 공격.
* 사이트 디페이스먼트 공격.
* 악성 코드 배포.

CSP의 사용은 일반적이고 이해하기 쉽습니다. CSP를 자세히 설명하는 것은 이 설명서의 목적이 아닙니다(자세한 내용은 아래 관련 정보 링크 참조). 중요한 것은 CSP를 사용하고 보안 정책이 강력한 경우 CSP에 어떤 Adobe 도메인 이름을 추가해야 하는지를 이해하는 것입니다. 이러한 도메인을 추가하면 사이트에 액세스하는 방문자 브라우저에서 사용하는 Experience Cloud 리소스에 대한 중요한 호출을 수행할 수 있습니다.

## 화이트리스트에 작성할 Experience Cloud 도메인 {#section-30693e9a96834edfbf04de9e698cf2aa}

사용하는 각 목록 Experience Cloud 솔루션 또는 서비스에 이러한 도메인 이름 또는 URL을 CSP에 추가합니다.

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
   <td colname="col1"> <p> <b>Experience Cloud ID 서비스 및 Audience Manager</b> </p> </td> 
   <td colname="col2"> <p>아래 도메인을 포함하도록 CSP를 수정합니다.</p> 
   <p><ul>
   <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
   <li>Adobe Launch를 사용하여 태그를 배포하는 경우 도메인 목록에 <code>https://assets.adobedtm.com</code>도 추가해야 합니다.</li></ul></p> <p><span class="codeph">demdex.net</span> 도메인 호출은 <a href="../introduction/cookies.md" format="dita" scope="local">쿠키 및 Experience Cloud Identity 서비스</a>를 생성하고 ID를 동기화하는 데 사용됩니다. <a href="https://docs.adobe.com/content/help/ko-KR/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">Demdex 도메인에 대한 호출 이해</a>도 참조하십시오. </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Activity Map 플러그인</b> </p> </td> 
 <td colname="col2"> <p>CSP가 *.adobe.com을 포함하도록 수정합니다. **참고**: 2020년 1월 이전에 Activity Map을 이미 설치한 경우 브라우저에는 여전히 *.omniture.com에 대한 초기 요청이 표시되지만 *.adobe.com으로 리디렉션 됩니다. </p></td> 
 </tr>
 <tr>
 <td colname="col1"> <p> <b>Advertising Analytics</b> </p> </td> 
 <td colname="col2"> <p>쿼리 문자열 매개 변수에 대한 제어 권한이 있는 경우 매개 변수 's_kwcid' 및 'ef_id'를 화이트리스트에 추가해야 합니다. 기술적으로, Advertising Analytics는 's_kwcid'만 사용하지만 Ad Cloud 검색 또는 DSP를 선택하는 경우 'ef_id'도 사용합니다. 이러한 쿼리 문자열 매개 변수는 영숫자입니다. `s_kwcid` 매개 변수는 “!”를 사용합니다. 문자 및 `ef_id` 매개 변수는 “:” 문자를 사용합니다. URL에서 “!” 문자를 차단하고 있는 경우, 문자를 화이트리스트에 추가해야 합니다.</p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>* [컨텐츠 보안 정책 참조](https://content-security-policy.com/)
>* [MDN: 컨텐츠 보안 정책](https://developer.mozilla.org/ko-KR/docs/Web/HTTP/CSP)
>* [Wikipedia: 컨텐츠 보안 정책](https://en.wikipedia.org/wiki/Content_Security_Policy)

