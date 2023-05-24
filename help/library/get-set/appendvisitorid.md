---
description: 이 기능을 사용하면 브라우저에서 서드파티 쿠키를 차단할 때 도메인에서 방문자의 Experience Cloud ID를 공유할 수 있습니다. 이 기능을 사용하기 위해 ID 서비스를 구현했을 것이며, 소스 및 대상 도메인을 소유해야 합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.
keywords: ID 서비스
title: appendVisitorIDsTo (도메인 간 추적)
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
source-git-commit: c035f0af76f70322e4d79ed842502b26c3f155ac
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 100%

---

# appendVisitorIDsTo (도메인 간 추적){#appendvisitoridsto-cross-domain-tracking}

이 기능을 사용하면 브라우저에서 서드파티 쿠키를 차단할 때 도메인에서 방문자의 Experience Cloud ID를 공유할 수 있습니다. 이 기능을 사용하기 위해 ID 서비스를 구현했을 것이며, 소스 및 대상 도메인을 소유해야 합니다. VisitorAPI.js 버전 1.7.0 이상에서 사용 가능합니다.

내용:

<ul class="simplelist"> 
 <li> </a> 브라우저에서 서드파티 쿠키를 차단하는 경우 도메인에서 방문자 추적 <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> </a></li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> 방문자 ID 코드 샘플 추가 </a> </li> 
 </a> </li> 
</ul>

<!-- <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management (DTM) and SDK Support -->

## 브라우저에서 서드파티 쿠키를 차단하는 경우 도메인에서 방문자 추적 {#section-7251d88befd440b4b79520e33c5aa44a}

ID 서비스는 사용자가 사이트를 방문할 때 브라우저에 자사 및 서드파티 쿠키를 기록합니다([쿠키 및 Experience Cloud Identity Service](../../introduction/cookies.md) 참조). 자사 쿠키에는 해당 방문자에 대한 고유 ID인 MID가 포함되어 있습니다. 서드파티 쿠키에는 ID 서비스가 MID를 생성하는 데 사용하는 다른 ID가 포함되어 있습니다. 브라우저가 이 서드파티 쿠키를 차단하면 ID 서비스는 다음과 같은 작업을 수행할 수 없습니다.

* 다른 도메인으로 이동할 때 해당 사이트 방문자의 고유 ID를 다시 생성합니다.
* 조직이 소유한 여러 도메인에서 방문자를 추적합니다.

이 문제를 해결하려면 ` Visitor.appendVisitorIDsTo( *`url`*)`을 구현합니다. 이 속성을 사용하면 브라우저가 서드파티 쿠키를 차단하더라도 ID 서비스가 여러 도메인에서 사이트 방문자를 추적할 수 있습니다. 작동 방법은 다음과 같습니다.

* 방문자가 다른 도메인으로 이동할 때 이 ` Visitor.appendVisitorIDsTo( *`url`*)`은 원래 도메인에서 대상 도메인으로의 URL 경로 재지정에 MID를 조회 매개변수로 추가합니다.
* 대상 도메인의 ID 서비스 코드는 Adobe에 해당 방문자의 ID 요청을 전송하는 대신 URL에서 MID를 추출합니다. 이 요청에는 서드파티 쿠키 ID가 포함되어 있으며, 이 경우에는 사용할 수 없습니다.
* 대상 페이지의 ID 서비스 코드는 전달한 MID를 사용하여 방문자를 추적합니다.

자세한 내용은 코드 샘플을 참조하십시오.

## 방문자 ID 코드 샘플 추가 {#section-62d55f7f986542b0b9238e483d50d7b0}

다음 예제 코드를 활용하여 `appendVisitorIDsTo` 함수 사용을 시작해 보십시오.

>[!TIP]
>
>이 코드는 Adobe Analytics 확장의 일부인 사용자 정의 코드 편집기 또는 [AppMeasurement.js](https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=ko-KR)의 상단에 배치할 수 있습니다.

```js
var adbeDomains = ["marketo.com", "figma.com", "workfront.com"];
var visitor = Visitor.getInstance("9E1005A551ED61CA0A490D45@AdobeOrg", {
  trackingServer: "sstats.adobe.com",
  trackingServerSecure: "sstats.adobe.com",
  marketingCloudServer: "sstats.adobe.com",
  marketingCloudServerSecure: "sstats.adobe.com"
});
adbeDomains.forEach(function(domain) {
  var domainRegex = RegExp(domain);
  if (!domainRegex.test(location.hostname)) {
    hrefSelector = '[href*="' + domain + '"]';
    document.querySelectorAll(hrefSelector).forEach(function(href) {
      href.addEventListener('mousedown', function(event) {
        var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(event.currentTarget.href)
        event.currentTarget.href = destinationURLWithVisitorIDs.replace(/MCAID%3D.*%7CMCORGID/, 'MCAID%3D%7CMCORGID');
      });
    });
  }
});
```

<!-- >[!IMPORTANT]
>
>In order for the values passed in the URL via appendVisitorsIDsTo to be picked up, the [ovewriteCrossDomainMCIDAndAID](../function-vars/overwrite-visitor-id.md) variable must be set to true.

The following example can help you get started with ` Visitor.appendVisitorIDsTo( *`url`*)`. When implemented properly, your JavaScript code could look similar to the following example.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
``` -->

<!-- ## Dynamic Tag Management (DTM) and SDK Support {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Support for </th> 
   <th colname="col2" class="entry"> See </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> Set the appendVisitorIDTo Function in DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Android ID Service Methods </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> iOS ID Service Methods </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table> -->
