---
description: ID 서비스 함수 idSyncByURL 및 idSyncByDataSource를 사용하면 대상 게시 iFrame에서 ID 동기화를 수동으로 구현할 수 있습니다. VisitorAPI.js 버전 1.10 이상에서 사용할 수 있습니다.
keywords: ID 서비스
title: URL 또는 데이터 소스별 ID 동기화
exl-id: a22e6b47-00ff-4b51-9958-ddeccc1e507e
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 96%

---

# URL 또는 데이터 소스별 ID 동기화{#id-synchronization-by-url-or-data-source}

ID 서비스 함수 idSyncByURL 및 idSyncByDataSource를 사용하면 대상 게시 iFrame에서 ID 동기화를 수동으로 구현할 수 있습니다. VisitorAPI.js 버전 1.10 이상에서 사용할 수 있습니다.

## 구문, 속성 및 매크로 {#section-90ac61617482463aaf4c57009b830332}

**구문**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 코드 </th> 
   <th colname="col2" class="entry"> 사용자 ID 동기화 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>사용자 지정 동기화 URL을 사용하여 다양한 데이터 파트너와 <span class="keyword">Audience Manager</span> 간에 동기화 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>이미 DPID 및 DPUUID를 알고 있으며 표준 ID 동기화 URL 포맷으로 <span class="keyword">Audience Manager</span>로 해당 ID를 전송하려고 할 때 </p> <p></p> </td> 
  </tr> 
 </tbody> 
</table>

**속성**

다음 표는 두 함수 모두에서 사용할 수 있는 속성을 나열하고 정의합니다.

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 이름 </th> 
   <th colname="col2" class="entry"> 유형 </th> 
   <th colname="col3" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpid </span> </td> 
   <td colname="col2"> 문자열 </td> 
   <td colname="col3"> <p>Audience Manager에서 지정한 데이터 공급자 ID. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> 문자열 </td> 
   <td colname="col3"> <p>사용자에 대한 데이터 공급자의 고유 ID입니다. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> 숫자 </td> 
   <td colname="col3"> <p> <i>(선택 사항)</i> 쿠키 만료 시간을 설정합니다. 정수여야 합니다. 기본값은 20160분(14일)입니다. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> 문자열 </td> 
   <td colname="col3"> <p>대상 URL. </p> </td> 
  </tr> 
 </tbody> 
</table>

**매크로**

두 함수 모두 다음 매크로를 허용합니다.

* `%TIMESTAMP%`: 타임스탬프를 생성합니다(밀리초 단위). 캐시 무효화에 사용됩니다.
* `%DID%`: 사용자의 Audience Manager ID를 삽입합니다.
* `%HTTP_PROTO%`: 통신 프로토콜(`http` 또는 `https`)을 설정합니다.

## 샘플 코드 및 출력 {#section-0115615c37584a19a2ab11e917c4e7e9}

성공하면 두 함수 모두 `Successfully queued`를 반환합니다. 실패한 경우 오류 메시지 문자열을 반환합니다.

### visitor.idSyncByURL

**샘플 코드**

```javascript
   //Instatiate Visitor
    var visitor = Visitor.getInstance
    ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
   // Fires url with macros replaced 
    visitor.idSyncByURL({ 
    dpid: '24', // must be a string 
    url: '//su.addthis.com/red/usync?pid=16&puid=%DID%&url=%HTTP_PROTO%://
    dpm.demdex.net/ibs:dpid=420&dpuuid={{uid}}', 
    minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**샘플 출력**

```
http://su.addthis.com/red/usync?pid=16&puid=28777806459181003670799219185178493848&url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D
```

### visitor.idSyncByDataSource

**샘플 코드**

```javascript
  //Instantiate Visitor
   var visitor = Visitor.getInstance
   ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
  // Fires 'http:/https:' + '//dpm.demdex.net/ibs:dpid=&dpuuid='
   visitor.idSyncByDataSource({ 
     dpid: '24', // must be a string
     dp     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**샘플 출력**

```
http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765
```

>[!MORELIKETHIS]
>
>* [DIL idSync](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-instance-methods.html#idsync)

