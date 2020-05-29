---
description: 이 기능을 사용하면 브라우저에서 서드파티 쿠키를 차단할 때 도메인에서 방문자의 Experience Cloud ID를 공유할 수 있습니다. 이 기능을 사용하기 위해 ID 서비스를 구현했을 것이며, 소스 및 대상 도메인을 소유해야 합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.
keywords: ID Service
seo-description: 이 기능을 사용하면 브라우저에서 서드파티 쿠키를 차단할 때 도메인에서 방문자의 Experience Cloud ID를 공유할 수 있습니다. 이 기능을 사용하기 위해 ID 서비스를 구현했을 것이며, 소스 및 대상 도메인을 소유해야 합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.
seo-title: appendVisitorIDsTo(도메인 간 추적)
title: appendVisitorIDsTo(도메인 간 추적)
uuid: 06b453ee-73c5-4625-82d9-877ad2b4f702
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '446'
ht-degree: 100%

---


# appendVisitorIDsTo(도메인 간 추적){#appendvisitoridsto-cross-domain-tracking}

이 기능을 사용하면 브라우저에서 서드파티 쿠키를 차단할 때 도메인에서 방문자의 Experience Cloud ID를 공유할 수 있습니다. 이 기능을 사용하기 위해 ID 서비스를 구현했을 것이며, 소스 및 대상 도메인을 소유해야 합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.

내용:

<ul class="simplelist"> 
 <li> </a> 브라우저에서 타사 쿠키를 차단하는 경우 도메인에서 방문자 추적 <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> </a></li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> 방문자 ID 코드 샘플 추가 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> DTM(Dynamic Tag Management) 및 SDK 지원 </a> </li> 
</ul>

## 브라우저에서 타사 쿠키를 차단하는 경우 도메인에서 방문자 추적 {#section-7251d88befd440b4b79520e33c5aa44a}

ID 서비스는 사용자가 사이트를 방문할 때 브라우저에 자사 및 타사 쿠키를 기록합니다([쿠키 및 Experience Cloud Identity 서비스](../../introduction/cookies.md) 참조). 자사 쿠키에는 해당 방문자에 대한 고유 ID인 MID가 포함되어 있습니다. 서드파티 쿠키에는 ID 서비스가 MID를 생성하는 데 사용하는 다른 ID가 포함되어 있습니다. 브라우저가 이 서드파티 쿠키를 차단하면 ID 서비스는 다음을 수행할 수 없습니다.

* 다른 도메인으로 이동할 때 해당 사이트 방문자의 고유 ID를 다시 생성합니다.
* 조직이 소유한 여러 도메인에서 방문자를 추적합니다.

이 문제를 해결하려면 ` Visitor.appendVisitorIDsTo( *`url`*)`을 구현합니다. 이 속성을 사용하면 브라우저가 서드파티 쿠키를 차단하더라도 ID 서비스가 여러 도메인에서 사이트 방문자를 추적할 수 있습니다. 작동 방법은 다음과 같습니다.

* 방문자가 다른 도메인으로 이동할 때 이 ` Visitor.appendVisitorIDsTo( *`url`*)`은 원래 도메인에서 대상 도메인으로의 URL 경로 재지정에 MID를 조회 매개변수로 추가합니다.
* 대상 도메인의 ID 서비스 코드는 Adobe에 해당 방문자의 ID 요청을 전송하는 대신 URL에서 MID를 추출합니다. 이 요청에는 타사 쿠키 ID가 포함되어 있으며, 이 경우에는 사용할 수 없습니다.
* 대상 페이지의 ID 서비스 코드는 전달한 MID를 사용하여 방문자를 추적합니다.

자세한 내용은 코드 샘플을 참조하십시오.

## 방문자 ID 코드 샘플 추가 {#section-62d55f7f986542b0b9238e483d50d7b0}

다음 예제를 통해 ` Visitor.appendVisitorIDsTo( *`url`*)`을 시작할 수 있습니다. 제대로 구현된 경우 JavaScript 코드가 다음 예제와 유사할 수 있습니다.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678 
<draft-comment>
  |TS=123675879 
</draft-comment>" 
 
//Redirect to the destination
```

## DTM(Dynamic Tag Management) 및 SDK 지원 {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 지원 대상 </th> 
   <th colname="col2" class="entry"> 자세한 내용은 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/kr/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> DTM에서 appendVisitorIDTo 함수 설정 </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://docs.adobe.com/content/help/ko-KR/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Android ID 서비스 메서드 </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://docs.adobe.com/content/help/ko-KR/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> iOS ID 서비스 메서드 </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

