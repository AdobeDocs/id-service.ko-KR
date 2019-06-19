---
description: ID 서비스 함수인 idSyncByURL 및 idSyncByDataSource를 사용하면 대상 게시 iFrame에서 ID 동기화를 수동으로 구현할 수 있습니다. VisitorAPI.js 버전 1.10 이상에서 사용 가능합니다.
keywords: ID 서비스
seo-description: ID 서비스 함수인 idSyncByURL 및 idSyncByDataSource를 사용하면 대상 게시 iFrame에서 ID 동기화를 수동으로 구현할 수 있습니다. VisitorAPI.js 버전 1.10 이상에서 사용 가능합니다.
seo-title: URL 또는 데이터 소스별 ID 동기화
title: URL 또는 데이터 소스별 ID 동기화
uuid: FF 83 D 910-8375-4295-9 F 2 A-E 14 C 15 EEE 09 A
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# URL 또는 데이터 소스별 ID 동기화{#id-synchronization-by-url-or-data-source}

ID 서비스 함수인 idSyncByURL 및 idSyncByDataSource를 사용하면 대상 게시 iFrame에서 ID 동기화를 수동으로 구현할 수 있습니다. VisitorAPI.js 버전 1.10 이상에서 사용 가능합니다.

내용:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/idsync.md#section-90ac61617482463aaf4c57009b830332" format="dita" scope="local"> 구문, 속성 및 매크로 </a> </li> 
 <li> <a href="../../library/get-set/idsync.md#section-0115615c37584a19a2ab11e917c4e7e9" format="dita" scope="local"> 샘플 코드 및 출력 </a> </li> 
</ul>

## 구문, 속성 및 매크로 {#section-90ac61617482463aaf4c57009b830332}

**구문**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 코드 </th> 
   <th colname="col2" class="entry"> 사용자 ID 동기화 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>사용자 지정 동기화 URL을 사용하여 다양한 데이터 파트너와 <span class="keyword">Audience Manager</span> 간에 동기화 </p> <p> 
     <draft-comment>
       다양한 데이터 파트너와 고객 관리자 간의 공동 작업 예를 들어 파트너 X는 이 아이콘을 사용하여 파트너 Y와 사용자 ID를 동기화한 다음 Audience Manager로 전송합니다. 
     </draft-comment> </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>이미 DPID 및 DPUUID를 알고 있으며 표준 ID 동기화 URL 포맷으로 <span class="keyword">Audience Manager</span>로 해당 ID를 전송하려고 할 때 </p> <p> 
     <draft-comment>
       사용자 ID를 이미 알고 있고 Audience Manager로 전송하려는 경우 
     </draft-comment> </p> </td> 
  </tr> 
 </tbody> 
</table>

**속성**

다음 표에는 두 함수 모두에 사용 가능한 속성이 나열 및 정의되어 있습니다.

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 이름 </th> 
   <th colname="col2" class="entry"> 유형 </th> 
   <th colname="col3" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpid </span> </td> 
   <td colname="col2"> 문자열 </td> 
   <td colname="col3"> <p>Audience Manager가 할당한 데이터 제공업체 ID입니다. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> 문자열 </td> 
   <td colname="col3"> <p>사용자에 대한 데이터 제공업체의 고유한 ID입니다. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> 숫자 </td> 
   <td colname="col3"> <p> <i>(선택 사항)</i> 쿠키 만료 시간을 설정하며 정수여야 합니다. 기본값은 20160분(14일)입니다. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> 문자열 </td> 
   <td colname="col3"> <p>대상 URL. </p> </td> 
  </tr> 
 </tbody> 
</table>

**매크로**

두 함수 모두 다음 매크로를 허용합니다.

* ** `%TIMESTAMP%`: ** 타임스탬프를 생성합니다 (밀리초 단위). 캐시 무효화에 사용됩니다.
* ** `%DID%`: **사용자의 Audience Manager ID를 삽입합니다.
* ** `%HTTP_PROTO%`: ** 통신 프로토콜 ( `http` 또는 `https`) 를 설정합니다.

## 샘플 코드 및 출력 {#section-0115615c37584a19a2ab11e917c4e7e9}

두 함수 모두 성공 시 반환됩니다 `Successfully queued` . 실패한 경우 오류 메시지 문자열을 반환합니다.

**visitor.idSyncByURL**

<table id="table_56AD8291DF9445C69CC2BF50435E1626"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 샘플 코드 </th> 
   <th colname="col2" class="entry"> 샘플 출력 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Instatiate 방문자 
 var visitor = Visitor. getinstance ("marketing-cloud-org-id-here", {});

    // &amp; amp; nbsp; Fires &amp; amp; nbsp; URL &amp; amp; nbsp; With &amp; amp; nbsp; 매크로 및 amp; nbsp; Replacedvisitor
    . idsyncbyurl ({
    &amp; amp; nbsp; DPID: &amp; amp; nbsp; &#39; 24 &#39;, &amp; amp; nbsp; // &amp; amp; nbsp; 필수 (&amp; amp)nbsp; be &amp; amp; nbsp; A &amp; amp; nbsp; 문자열
    및 amp; nbsp; URL: &amp; amp; nbsp; &#39;//su.addthis.com/red/usync?pid=16&amp;amp;puid=%DID%&amp;amp;url=%HTTP_PROTO%%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D&#39;,&amp;nbsp;minutesToLive:&amp;nbsp;20160&amp;nbsp;//&amp;nbsp;optional,&amp;nbsp;defaults&amp;nbsp;to&amp;nbsp;20160&amp;nbsp;minutes&amp;nbsp;(14&amp;nbsp;days)&amp;nbsp
    ;
    }); &lt;/code &gt; &lt;/p &gt; &lt;/td &gt;
<td colname="col2"> <p> <span class="codeph"> http://su.addthis.com/red/usync?pid=16&amp;puid=28777806459181003670799219185178493848&amp;url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

**visitor.idSyncByDataSource**

<table id="table_90D61A7E715D47238AAFF2808B33C2F0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 샘플 코드 </th> 
   <th colname="col2" class="entry"> 샘플 출력 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Instantiate 방문자 
 var visitor = Visitor. getinstance ("marketing-cloud-org-id-here", {});

    // &amp; amp; nbsp; Fires &amp; amp; nbsp; &#39; http:/https:&#39;&amp;nbsp;+&amp;nbsp;&#39;//dpm.demdex.net/ibs:dpid=&amp;lt;dpid&amp;gt;&amp;amp;dpuuid=&amp;lt;dpuuid&amp;gt;&#39;visitor.idSyncByDataSource(
    {
    &amp; amp; nbsp; DPID: &amp; amp; nbsp; &#39; 24 &#39;, &amp; amp; nbsp; // &amp; amp; nbsp; 필수 (&amp; amp)nbsp; be &amp; amp; nbsp; A &amp; amp; nbsp; 문자열
    및 amp; nbsp; DPUUID: &amp; amp; nbsp; &#39; 98765 &#39;, &amp; amp; nbsp; // &amp; amp; nbsp; 필수 (&amp; amp)nbsp; be &amp; amp; nbsp; A &amp; amp; nbsp; 문자열
    및 amp; nbsp; Minutestolive: &amp; amp; nbsp; 20160 &amp; amp; nbsp; // &amp; amp; nbsp; optional, &amp; amp; nbsp; 기본값 및 amp; nbsp; To &amp; amp; nbsp; 20160 &amp; amp; nbsp; 분 및 amp; nbsp; (14 &amp; amp; nbsp; days) &amp; amp; nbsp;
    }); &lt;/code &gt; &lt;/p &gt; &lt;/td &gt;
<td colname="col2"> <p> <span class="codeph"> http://dpm.demdex.net/ibs:dpid=24&amp;dpuuid=98765 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_ like_ this]
>
>* [DIL idSync](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_idsync.html)

