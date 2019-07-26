---
description: Experience Cloud Identity 서비스를 배포하기 전에 이 서비스가 여러 도메인의 방문자 추적에 어떻게 영향을 미치는지 이해하고, 다른 메서드를 사용하거나 JavaScript 파일을 통해 데이터를 수집하는 경우에 발생할 수 있는 문제를 알고 있어야 합니다.
keywords: ID 서비스
seo-description: Experience Cloud Identity 서비스를 배포하기 전에 이 서비스가 여러 도메인의 방문자 추적에 어떻게 영향을 미치는지 이해하고, 다른 메서드를 사용하거나 JavaScript 파일을 통해 데이터를 수집하는 경우에 발생할 수 있는 문제를 알고 있어야 합니다.
seo-title: Experience Cloud Identity 서비스 마이그레이션 의사 결정 지점
title: Experience Cloud Identity 서비스 마이그레이션 의사 결정 지점
uuid: ee56b5de-fcf3-4cfb-9e53-762af7c4d2ff
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Experience Cloud Identity 서비스 마이그레이션 의사 결정 지점

Experience Cloud Identity 서비스를 배포하기 전에 이 서비스가 여러 도메인의 방문자 추적에 어떻게 영향을 미치는지 이해하고, 다른 메서드를 사용하거나 JavaScript 파일을 통해 데이터를 수집하는 경우에 발생할 수 있는 문제를 알고 있어야 합니다.

이 섹션의 질문에 답변하여 수행해야 하는 추가 마이그레이션 단계를 확인하십시오.

## 데이터 수집 CNAME이 있습니까?

많은 고객들은 ID 서비스 마이그레이션의 일부로 데이터 수집 CNAME 외부로 마이그레이션할 수 있습니다.

<table id="table_13F7C1E3D64D4F86B0149C9D3B54AADD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 데이터 수집 방법 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>CNAME 사용 </p> </td> 
   <td colname="col2"> <p>다음 질문을 참조하여 데이터 수집 CNAME 외부로 마이그레이션해야 하는지 결정하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>CNAME 사용 안 함 </p> </td> 
   <td colname="col2"> <p><a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local">데이터 수집 CNAME이 없는 경우 데이터 수집 서버가 *.2o7.net입니까 아니면 *.sc.omtrdc.net입니까?</a>로 건너뜁니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

## 데이터 수집 CNAME이 있는 경우 여러 개의 도메인이 있습니까?

데이터를 *동일한 보고서 세트*&#x200B;로 보내는 여러 도메인이 있는 경우 CNAME과 함께 데이터 수집을 사용하는 것이 좋습니다. 이렇게 하면 여러 도메인에서 방문자를 추적하는 데 도움이 됩니다. 단일 도메인에서 데이터를 수집하는 경우에는 데이터 수집 CNAME을 유지 관리해도 이점이 없습니다.

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 데이터 수집 위치 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>여러 도메인 </p> </td> 
   <td colname="col2"> <p>여러 도메인 간에 방문자를 추적하며 고객이 다른 도메인을 방문하기 전에 식별될 수 있는 기본 시작 사이트도 있는 경우 데이터 수집 CNAME을 계속 사용해야 합니다. 자세한 내용은 <a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local">데이터 수집 CNAME 및 도메인 간 추적</a>을 참조하십시오. </p> <p>ID 서비스에서 CNAME를 구성하려면 추적 서버 매개 변수인 <span class="codeph">visitor.marketingCloudServer</span> 및 <span class="codeph">visitor.marketingCloudServerSecure</span>를 추가로 지정해야 합니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>단일 도메인 </p> </td> 
   <td colname="col2"> <p>단일 도메인 사용이란 데이터 수집 CNAME을 더 이상 관리하지 않으려는 경우 여기에서 마이그레이션할 수 있음을 의미합니다. 그렇지만 CNAME이 작동하는 경우에는 변경할 필요가 없습니다. </p> <p>CNAME을 제거하는 경우 </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">새 추적 서버가 <a href="https://marketing.adobe.com/resources/help/ko_KR/whitepapers/rdc/" format="https" scope="external">RDC 규격</a> 서버인지 확인합니다. </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762"><span class="keyword">Experience Cloud</span> ID 서비스로 마이그레이션하기 몇 개월 전에 CNAME에서 RDC 추적 서버로 이동합니다. </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i>*.2o7.net</i> 추적 서버를 사용하지 <span class="codeph">마십시오</span>. </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1"><a href="https://helpx.adobe.com/kr/marketing-cloud/contact-support.html" format="https" scope="external">고객 지원 센터</a>에 문의하여 방문자 마이그레이션을 설정하십시오. 이렇게 하면 일관된 방문자 수를 계산하는 데 도움이 됩니다. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 여러 개의 Analytics JavaScript 파일이 있습니까 아니면 Flash 애플리케이션이나 비디오를 추적하고 있습니까?

사이트에 *동일한 보고서 세트*&#x200B;로 데이터를 전송하는 Analytics JavaScript 파일 또는 Flash 애플리케이션이나 비디오가 여러 개 있는 경우 [!DNL Experience Cloud] ID 서비스를 롤아웃하는 동안 방문자가 Analytics ID로 계속 식별되도록 유예 기간을 구성해야 합니다.

<table id="table_8A4EA063AF4345B69BC98537E2E702BA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 데이터 수집 방법 </th> 
   <th colname="col2" class="entry"> 필수 작업 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">다중 Analytics Javascript 파일 </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">기타 데이터 수집 방법 </li> 
    </ul> </td> 
   <td colname="col2"> <p>각 JavaScript 파일 및 기타 데이터 수집 라이브러리에 방문자 ID 서비스를 롤아웃할 수 있도록 방문자 ID 서비스 유예 기간을 구성해야 합니다. 자세한 내용은 <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> ID 서비스 유예 기간</a>을 참조하십시오. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>단일 Analytics JavaScript 파일 </p> </td> 
   <td colname="col2"> <p>유예 기간 없이 방문자 ID 서비스를 사용하도록 단일 JavaScript 파일을 업데이트할 수 있습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

## 지원되지 않는 데이터 수집 방법을 사용하고 있습니까?

링크를 추적하는 방법을 업데이트하거나 Sliverlight 외부로 마이그레이션해야 할 수 있습니다.

<table id="table_A72AEB92F48345DD83F136B9989F4EF9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 데이터 수집 방법 </th> 
   <th colname="col2" class="entry"> 필수 작업 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>JavaScript 및/또는 Flash </p> </td> 
   <td colname="col2"> <p>없음. <span class="keyword">Experience Cloud</span> ID 서비스는 다음과 같은 데이터 수집 방법을 지원합니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>방문자가 Silverlight 컨텐츠 및 <span class="keyword">Experience Cloud</span> ID 서비스를 사용하는 사이트의 다른 섹션에 액세스할 수 있는 경우 Silverlight에서 마이그레이션해야 합니다. ID 서비스에서는 Silverlight를 지원하지 않습니다. </p> <p> Silverlight 기반 비디오 플레이어를 추적하는 경우 대신 사용할 수 있는 JavaScript API를 공급업체에서 제공할 수 있습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>하드 코딩된 이미지 태그 </p> </td> 
   <td colname="col2"> <p>JavaScript를 사용하도록 하드 코딩된 링크를 업데이트하십시오. </p> </td> 
  </tr> 
 </tbody> 
</table>

