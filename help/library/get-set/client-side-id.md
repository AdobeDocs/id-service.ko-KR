---
description: 이 ID 서비스 함수를 호출하여 ID 서비스가 클라이언트측 Experience Cloud 방문자 ID(MID)를 생성했는지 확인합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.
keywords: ID 서비스
title: isClientSideMarketingCloudVisitorID를 참조하십시오
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
TQID: https://experienceleague.adobe.com/kQK7Lw-j33luPqTSzQKGuf8fMPuOEDoQBzesZa-bvVo
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 127
ht-degree: 100%

---

# isClientSideMarketingCloudVisitorID를 참조하십시오{#isclientsidemarketingcloudvisitorid}

이 ID 서비스 함수를 호출하여 ID 서비스가 클라이언트측 Experience Cloud 방문자 ID(MID)를 생성했는지 확인합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.

**구문**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

다음 테이블은 이 함수가 반환하는 응답을 나열하고 설명합니다.

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

