---
description: 이 도우미 메서드를 사용하면 SDID(Supplemental Data ID)를 쿼리 문자열 매개 변수로 리디렉션 URL에 추가할 수 있습니다. 이 작업은 A4T를 사용하며 한 페이지에서 다른 페이지로의 SDID를 유지하면서 이러한 개별 방문을 함께 연결해야 할 때 유용합니다. 이 기능을 사용하려면 소스 및 대상 도메인에서 동일한 조직 ID로 ID 서비스를 구현했어야 합니다.
keywords: ID 서비스
seo-description: 이 도우미 메서드를 사용하면 SDID(Supplemental Data ID)를 쿼리 문자열 매개 변수로 리디렉션 URL에 추가할 수 있습니다. 이 작업은 A4T를 사용하며 한 페이지에서 다른 페이지로의 SDID를 유지하면서 이러한 개별 방문을 함께 연결해야 할 때 유용합니다. 이 기능을 사용하려면 소스 및 대상 도메인에서 동일한 조직 ID로 ID 서비스를 구현했어야 합니다.
seo-title: appendSupplementalDataIDTo를 참조하십시오
title: appendSupplementalDataIDTo를 참조하십시오
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '412'
ht-degree: 100%

---

# appendSupplementalDataIDTo 를 참조하십시오 {#appendsupplementaldataidto}

이 도우미 메서드를 사용하면 SDID(Supplemental Data ID)를 쿼리 문자열 매개 변수로 리디렉션 URL에 추가할 수 있습니다. 이 작업은 A4T를 사용하며 한 페이지에서 다른 페이지로의 SDID를 유지하면서 이러한 개별 방문을 함께 연결해야 할 때 유용합니다. 이 기능을 사용하려면 소스 및 대상 도메인에서 동일한 조직 ID로 ID 서비스를 구현했어야 합니다.

내용:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 구문 및 코드 샘플 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> 샘플 출력 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 구문 및 코드 샘플 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> sdidParamExpiry를 사용하여 SDID 시간 제한 변경 </a> </li> 
</ul>

## 구문 및 코드 샘플 {#section-cbb0b2f73bcc418386796c24c01b2365}

**구문:** ` appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**코드 샘플**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219");
```

## 샘플 출력 {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

아래 표시된 대로 URL 리디렉션은 수신 페이지에 대한 호출에 방문자의 SDID, 조직 ID 및 UNIX 타임스탬프를 포함합니다.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## sdidParamExpiry를 사용하여 SDID 시간 제한 변경 {#section-99946715cefa4acc95200b093db5297e}

[sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) 구성을 사용하면 `appendSupplementalDataIDTo` 도우미 함수를 사용하여 한 페이지에서 다른 페이지로 해당 ID를 전달할 때 기본 SDID 만료 간격을 변경할 수 있습니다. 기본적으로 수신 페이지의 ID 서비스 코드는 참조 페이지에서 보낸 URL에서 SDID를 가져오는 데 30초가 걸립니다. 수신 페이지의 ID 서비스 코드가 30 초 이내에 SDID를 검색할 수 없으면 새 SDID를 요청합니다. 이 기능은 주로 한 페이지에서 다른 페이지로 SDID를 전달해야 하고 이 시간 제한 간격을 제어하려는 A4T 고객을 위한 것입니다.

기본 SDID 시간 제한을 변경해야 하는 경우 다음 구문을 사용하여 `sdidParamExpiry`을 `Visitor.getInstance` 함수에 추가합니다.

**구문:** ` sdidParamExpiry: *`시간(초)`*`

**코드 샘플**

구성되면 ID 서비스 코드가 이 샘플과 유사할 수 있습니다. 이 샘플은 SDID 제한 시간을 15초로 설정합니다.

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```
