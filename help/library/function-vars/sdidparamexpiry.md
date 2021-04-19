---
description: 이 구성을 사용하면 appendSupplementalDataIDTo 도우미 함수를 사용하여 한 페이지에서 다른 페이지로 해당 ID를 전달할 때 기본 SDID(Supplemental Data ID) 만료 간격을 재정의할 수 있습니다. 기본적으로 수신 페이지의 ID 서비스 코드는 참조 페이지에서 보낸 URL에서 SDID를 가져오는 데 30초가 걸립니다. 수신 페이지의 ID 서비스 코드가 30 초 이내에 SDID를 검색할 수 없으면 새 SDID를 요청합니다. 이 기능은 주로 한 페이지에서 다른 페이지로 SDID를 전달해야 하고 이 시간 제한 간격을 제어하려는 A4T 고객을 위한 것입니다.
keywords: ID 서비스
seo-description: 이 구성을 사용하면 appendSupplementalDataIDTo 도우미 함수를 사용하여 한 페이지에서 다른 페이지로 해당 ID를 전달할 때 기본 SDID(Supplemental Data ID) 만료 간격을 재정의할 수 있습니다. 기본적으로 수신 페이지의 ID 서비스 코드는 참조 페이지에서 보낸 URL에서 SDID를 가져오는 데 30초가 걸립니다. 수신 페이지의 ID 서비스 코드가 30 초 이내에 SDID를 검색할 수 없으면 새 SDID를 요청합니다. 이 기능은 주로 한 페이지에서 다른 페이지로 SDID를 전달해야 하고 이 시간 제한 간격을 제어하려는 A4T 고객을 위한 것입니다.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '357'
ht-degree: 100%

---

# sdidParamExpiry{#sdidparamexpiry}

이 구성을 사용하면 appendSupplementalDataIDTo 도우미 함수를 사용하여 한 페이지에서 다른 페이지로 해당 ID를 전달할 때 기본 SDID(Supplemental Data ID) 만료 간격을 재정의할 수 있습니다. 기본적으로 수신 페이지의 ID 서비스 코드는 참조 페이지에서 보낸 URL에서 SDID를 가져오는 데 30초가 걸립니다. 수신 페이지의 ID 서비스 코드가 30 초 이내에 SDID를 검색할 수 없으면 새 SDID를 요청합니다. 이 기능은 주로 한 페이지에서 다른 페이지로 SDID를 전달해야 하고 이 시간 제한 간격을 제어하려는 A4T 고객을 위한 것입니다.

**SDID 시간 제한 재정의**

기본 SDID 시간 제한을 변경해야 하는 경우 다음 구문을 사용하여 `sdidParamExpiry`을 `Visitor.getInstance` 함수에 추가합니다.

**구문:** ` sdidParamExpiry: *`시간(초)`*`

**코드 샘플**

구성되면 ID 서비스 코드가 이 샘플과 유사할 수 있습니다. 이 샘플은 SDID 제한 시간을 15초로 설정합니다. 이 구성은 [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) 도우미 메서드와 함께 작동합니다.

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
