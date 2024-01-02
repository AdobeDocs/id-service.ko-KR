---
description: Experience Cloud ID 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.
keywords: ID 서비스
title: 2021 릴리스 정보
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
source-git-commit: 52956b38c59f60507aaf236b152ce41fc1229d14
workflow-type: ht
source-wordcount: '113'
ht-degree: 100%

---

# Experience Cloud ID 서비스 릴리스 정보 - 2021

Experience Cloud ID 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.

## 방문자 5.3.0

방문자 5.3.0 릴리스에는 다음 업데이트가 포함되어 있습니다.

* 로컬 ECID를 생성하도록 알고리즘이 업데이트됩니다.
* 최신 옵트인에 개인 정보 쿠키에 대한 `Secure` 및 `SameSite` 플래그가 포함됩니다.
* 페이지가 하위 iFrame에 로드될 때 발생하는 Firefox 브라우저 문제에 대한 패치가 수정되었습니다.

## 방문자 5.2.0

방문자 5.2.0 릴리스에는 다음 업데이트가 포함되어 있습니다.

* 이 버전에서는 ID 서비스에서 ECID를 수신할 때 호출되는 이벤트 `onReceiveEcid`(이)가 도입됩니다. 예:

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```
