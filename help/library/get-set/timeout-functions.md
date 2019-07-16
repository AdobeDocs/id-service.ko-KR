---
description: 이러한 ID 서비스 함수를 호출하여 경험 플랫폼 ID 서비스, 분석 또는 Audience Manager ID 요청의 시간 초과 상태를 결정합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.
keywords: ID 서비스
seo-description: 이러한 ID 서비스 함수를 호출하여 경험 플랫폼 ID 서비스, 분석 또는 Audience Manager ID 요청의 시간 초과 상태를 결정합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.
seo-title: callTimeOut 메서드
title: callTimeOut 메서드
uuid: e5047498-11db-4945-b356-c92b7d447573
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# callTimeOut 메서드{#calltimeout-methods}

이러한 ID 서비스 함수를 호출하여 경험 플랫폼 ID 서비스, 분석 또는 Audience Manager ID 요청의 시간 초과 상태를 결정합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.

## 시간 초과 함수 {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 솔루션 또는 서비스 </th> 
   <th colname="col2" class="entry"> 함수 구문 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Experience Platform Identity Service </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.MCIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AnalyticsIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AAMIDCallTimedOut()</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

## 함수 응답 {#section-ff73aaca58b74e10a0953c49a3387160}

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 응답 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> TRUE</span> </p> </td> 
   <td colname="col2"> <p>ID 서비스가 요청을 보냈으며, 요청 시간이 초과되었습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>ID 서비스가 요청을 보냈으며, 서버에서 성공한 응답을 수신했습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>ID 서비스가 요청을 보내지 않았습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

