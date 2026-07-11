---
description: 이러한 방문자 ID 서비스 함수를 호출하여 방문자 ID 서비스, Analytics 또는 Audience Manager ID 요청에 대한 시간 초과 상태를 확인할 수 있습니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.
keywords: 방문자 ID 서비스
title: callTimeOut 메서드
exl-id: ff3a2c5e-a0a8-4257-b538-0e4ce454b4e8
TQID: https://experienceleague.adobe.com/DIis78iaPQ7qpawlKwWCwReXbh5Mt0K8J3w-5KYdhmg
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 129
ht-degree: 30%

---

# callTimeOut 메서드{#calltimeout-methods}

이러한 방문자 ID 서비스 함수를 호출하여 방문자 ID 서비스, Analytics 또는 Audience Manager ID 요청에 대한 시간 초과 상태를 확인할 수 있습니다. `VisitorAPI.js` 버전 1.7.0 이상에서 사용할 수 있습니다.

## 시간 제한 기능 {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 솔루션 또는 서비스 </th> 
   <th colname="col2" class="entry"> 함수 구문 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>방문자 ID 서비스 </p> </td> 
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
   <td colname="col2"> <p>방문자 ID 서비스에서 요청을 보냈으며 요청 시간이 초과되었습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>방문자 ID 서비스가 요청을 보냈으며, 서버에서 성공적인 응답을 수신했습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>방문자 ID 서비스가 요청을 보내지 않았습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

