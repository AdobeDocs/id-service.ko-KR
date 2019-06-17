---
description: 이 ID 서비스 함수를 호출하여 ID 서비스가 클라이언트측 Experience Cloud 방문자 ID(MID)를 생성했는지 확인합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.
keywords: ID 서비스
seo-description: 이 ID 서비스 함수를 호출하여 ID 서비스가 클라이언트측 Experience Cloud 방문자 ID(MID)를 생성했는지 확인합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1 c 39 ac 60-1 d 2 b -4 ed 4-a 2 ea -30 d 680 e 61 e 10
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}를 참조하십시오

이 ID 서비스 함수를 호출하여 ID 서비스가 클라이언트측 Experience Cloud 방문자 ID(MID)를 생성했는지 확인합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.

**구문**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

다음 표에는 이 함수에 의해 반환된 응답이 나열 및 설명되어 있습니다.

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 응답 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> true</span> </p> </td> 
   <td colname="col2"> <p>ID 서비스가 <span class="keyword">Experience Cloud</span> 서버에서 MID를 수신할 수 없었거나 수신하지 않았습니다. MID를 브라우저에서 로컬로 생성했습니다(클라이언트측). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>ID 서비스가 <span class="keyword">Experience Cloud</span> 서버에서 MID를 수신했습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>ID 서비스가 <span class="keyword">Experience Cloud</span> 서버를 호출하지 않았습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

