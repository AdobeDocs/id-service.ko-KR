---
description: 이 구성을 사용하면 appendSupplementalDataIDTo 도우미 함수를 사용하여 한 페이지에서 다른 페이지로 해당 ID를 전달할 때 기본 보조 데이터 ID(SDID) 만료 간격을 대체할 수 있습니다. 기본적으로 수신 페이지의 ID 서비스 코드에는 참조 페이지에서 보낸 URL에서 SDID를 가져오는 데 30초가 있습니다. 수신 페이지의 ID 서비스 코드가 30초 이내에 SDID를 검색할 수 없으면 새 SDID가 필요합니다. 이 기능은 주로 한 페이지에서 다른 페이지로 SDID를 전달해야 하고 이 시간 초과 간격을 제어하려는 A4T 고객을 위한 것입니다.
keywords: ID Service
seo-description: 이 구성을 사용하면 appendSupplementalDataIDTo 도우미 함수를 사용하여 한 페이지에서 다른 페이지로 해당 ID를 전달할 때 기본 보조 데이터 ID(SDID) 만료 간격을 대체할 수 있습니다. 기본적으로 수신 페이지의 ID 서비스 코드에는 참조 페이지에서 보낸 URL에서 SDID를 가져오는 데 30초가 있습니다. 수신 페이지의 ID 서비스 코드가 30초 이내에 SDID를 검색할 수 없으면 새 SDID가 필요합니다. 이 기능은 주로 한 페이지에서 다른 페이지로 SDID를 전달해야 하고 이 시간 초과 간격을 제어하려는 A4T 고객을 위한 것입니다.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 7%

---


# sdidParamExpiry{#sdidparamexpiry}

이 구성을 사용하면 appendSupplementalDataIDTo 도우미 함수를 사용하여 한 페이지에서 다른 페이지로 해당 ID를 전달할 때 기본 보조 데이터 ID(SDID) 만료 간격을 대체할 수 있습니다. 기본적으로 수신 페이지의 ID 서비스 코드에는 참조 페이지에서 보낸 URL에서 SDID를 가져오는 데 30초가 있습니다. 수신 페이지의 ID 서비스 코드가 30초 이내에 SDID를 검색할 수 없으면 새 SDID가 필요합니다. 이 기능은 주로 한 페이지에서 다른 페이지로 SDID를 전달해야 하고 이 시간 초과 간격을 제어하려는 A4T 고객을 위한 것입니다.

**SDID 시간 초과 재정의**

기본 SDID 시간 제한을 변경해야 하는 경우 다음 구문을 사용하여 `sdidParamExpiry`을 `Visitor.getInstance` 함수에 추가합니다.

**구문:** ` sdidParamExpiry: *`시간(초)`*`

**코드 샘플**

구성할 때 ID 서비스 코드는 이 샘플과 유사할 수 있습니다. 이 샘플은 SDID 시간 초과를 15초로 설정합니다. 이 구성은 appendSupplementalDataIDTo [](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) 도우미 메서드와 함께 작동합니다.

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

