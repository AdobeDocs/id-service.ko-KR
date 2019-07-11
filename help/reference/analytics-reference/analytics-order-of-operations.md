---
description: 방문자 ID 서비스를 배포한 후에는 5가지 방법으로 Analytics에서 방문자를 식별할 수 있습니다.
keywords: ID 서비스
seo-description: 방문자 ID 서비스를 배포한 후에는 5가지 방법으로 Analytics에서 방문자를 식별할 수 있습니다.
seo-title: Analytics ID 작업 순서
title: Analytics ID 작업 순서
uuid: cb1d136e-093f-43b0-a7e1-96f1e61fdad0
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Analytics ID 작업 순서{#order-of-operations-for-analytics-ids}

방문자 ID 서비스를 배포한 후에는 5가지 방법으로 Analytics에서 방문자를 식별할 수 있습니다.

많은 시나리오에서 한 번의 호출로 2~3개의 다른 ID가 표시될 수 있지만, Analytics에서는 해당 목록에 있는 첫 번째 ID를 공식적인 [!DNL Experience Cloud] ID로 사용합니다. 예를 들어, 사용자 지정 방문자 ID(`vid` 쿼리 매개 변수에 포함됨)를 설정하는 경우, 이 ID는 동일한 히트에 있을 수 있는 다른 ID보다 먼저 사용됩니다. 자세한 내용은 [Analytics 및 Experience Cloud ID 설정](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6)을 참조하십시오.

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 사용된 순서 </th> 
   <th colname="col2" class="entry"> 쿼리 매개 변수(컬렉션 방법) </th> 
   <th colname="col3" class="entry"> 존재할 때 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>첫 번째<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/ko_KR/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p><span class="codeph">s.visitorID</span>가 설정되었습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>두 번째<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/ko_KR/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (s_vi 쿠키)</a> </p> </td> 
   <td colname="col3"> <p><span class="keyword">Experience Cloud</span> ID 서비스를 배포하기 전에 방문자에게 기존의 s_vi 쿠키가 있었거나 또는 <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">유예 기간</a>을 구성했습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>세 번째<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID(MID) </a> </p> </td> 
   <td colname="col3"> <p>방문자의 브라우저가 퍼스트 파티 쿠키를 수락합니다. AMCV 쿠키에 의해 설정됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>네 번째<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/ko_KR/sc/implement/?f=visid_fallback" format="http" scope="external"> fid(H.25.3 이상의 폴백 쿠키 또는 AppMeasurement for JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>브라우저가 서드 파티 쿠키를 허용하지 않으며 Analytics 추적 서버가 서드 파티 추적 서버로 설정됩니다. </p> <p> <p>참고: <span class="codeph">fid</span>는 기존 식별자이며, 사용자 사이트에서 ID 서비스를 구현한 경우에는 사용되지 않습니다. 이 경우 자사 <a href="../../introduction/cookies.md" format="dita" scope="local">AMCV 쿠키</a>로 인해 <span class="codeph">fid</span>를 사용할 수 없으므로 이 fid가 필요하지 않습니다. fid는 기존 코드를 지원하기 위해 또한 여러 기록상의 이유로 인해 유지되고 있습니다. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>다섯 번째<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/ko_KR/sc/implement/?f=visid_fallback" format="http" scope="external"> IP 주소, 사용자 에이전트, 게이트웨이 IP 주소</a> </p> </td> 
   <td colname="col3"> <p>방문자의 브라우저가 쿠키를 수락하지 않습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

