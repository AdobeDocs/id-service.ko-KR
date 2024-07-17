---
description: Experience Cloud ID 서비스가 기존 Analytics ID와 어떻게 작동되는지에 대한 개요입니다.
keywords: ID 서비스
title: Analytics 및 Experience Cloud ID 요청
exl-id: 8c682159-e23a-4641-9ffd-e0028dc2f305
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 95%

---

# Analytics 및 Experience Cloud ID 요청{#analytics-and-experience-cloud-id-requests}

Experience Cloud ID 서비스가 기존 Analytics ID와 어떻게 작동되는지에 대한 개요입니다.

## 요약 {#section-64d8523ff7634cb987d0c6480f587dd3}

지금까지 Experience Cloud ID 서비스는 Adobe Analytics에 완전히 통합되었습니다. 이 서비스는 Analytics의 필수적인 부분으로 남아 있지만 현재는 [!DNL Experience Cloud]의 기타 솔루션 및 기능에 대한 중요한 작업을 수행합니다. 이러한 기존의 기록으로 인해 Analytics ID를 확인하거나 기록하는 것은 [Experience Cloud ID 서비스에서 ID를 요청하고 설정하는 방법](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)에 설명된 일반 프로세스와는 조금 다릅니다. ID를 확인하기 위한 작업 순서에 대한 자세한 내용은 [Analytics 및 Experience Cloud ID 설정](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6)을 참조하십시오.

## AMCV 쿠키가 브라우저에서 설정되지 않음 {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

[!DNL Experience Cloud] (AMCV) 쿠키가 없는 경우 [!DNL Adobe] 에 대한 ID 서비스 호출은 기존 Analytics ID의 존재 여부에 따라 달라지는 응답을 생성합니다. 기존 [!DNL Analytics] ID는 [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=ko-KR)에 저장됩니다. 아래 표는 s_vi 쿠키의 상태를 기반으로 AMCV 쿠키에 ID를 쓰는 방법을 설명합니다.

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> s_vi 쿠키 상태 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> s_vi 쿠키가 설정되지 않음</b> </p> </td> 
   <td colname="col2"> <p>ID 서비스는 방문자에게 <span class="keyword">Experience Cloud</span> ID(MID)를 지정합니다. MID는 <span class="keyword">Analytics</span> 및 기타 <span class="keyword">Experience Cloud</span> 솔루션에서 방문자를 식별합니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> s_vi 쿠키가 설정됨</b> </p> </td> 
   <td colname="col2"> <p>s_vi 쿠키를 사용하는 사이트 방문자가 Experience Cloud ID 서비스를 처음 사용하면 이 서비스는 다음을 수행합니다. </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">s_vi 쿠키에 저장된 <span class="keyword">Analytics</span> ID를 AMCV 쿠키에 씁니다. AID(<span class="keyword">Analytics</span> ID)로 기록됩니다. 이 동작은 방문자 수에 영향을 미치지 <i>않습니다</i>. <span class="keyword"> Analytics</span>는 이전 ID를 사용하여 사용자를 계속 식별합니다. </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">MID를 AMCV 쿠키에 씁니다. MID는 다른 솔루션에서 사용자를 식별합니다. </li> 
    </ul> <p> <p>참고: <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">유예 기간</a>을 사용할 경우 데이터 센터 응답에는 항상 s_vi 쿠키에 저장된 이전 ID가 포함됩니다. 유예 기간 동안 이전 ID가 AMCV 쿠키에 AID 값으로 기록됩니다. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>s_fid 쿠키로 식별되는 사용자의 이전 FID 값은 AMCV 쿠키로 마이그레이션되지 않습니다. s_fid 쿠키가 있는 경우 사용자는 마치 s_vi 쿠키가 없는 것처럼(위 참조) 마이그레이션되고 사이트의 새 방문자로 나타납니다. 자세한 내용은 [Analytics 쿠키](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=ko-KR)를 참조하십시오.

## AMCV 쿠키가 브라우저에서 설정됨 {#section-01c088fc565c4b24ba1722c7cc240310}

AMCV 쿠키가 있고 쿠키에 이전 [!DNL Analytics] ID 값이 없는 경우 Analytics는 MID를 [!DNL Analytics] 식별자로 사용합니다.
