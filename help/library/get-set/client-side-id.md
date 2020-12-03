---
description: 이 ID 서비스 함수를 호출하여 ID 서비스가 클라이언트측 Experience Cloud 방문자 ID(MID)를 생성했는지 확인합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.
keywords: ID Service
seo-description: 이 ID 서비스 함수를 호출하여 ID 서비스가 클라이언트측 Experience Cloud 방문자 ID(MID)를 생성했는지 확인합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.
seo-title: isClientSideMarketingCloudVisitorID를 참조하십시오
title: isClientSideMarketingCloudVisitorID를 참조하십시오
uuid: 1c39ac60-1d2b-4ed4-a2ea-30d680e61e10
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 52%

---


# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}를 참조하십시오

이 ID 서비스 함수를 호출하여 ID 서비스가 클라이언트측 Experience Cloud 방문자 ID(MID)를 생성했는지 확인합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.

**구문**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

다음 표에서는 이 함수에서 반환된 응답을 나열하고 설명합니다.

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

