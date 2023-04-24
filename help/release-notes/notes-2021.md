---
description: Experience Cloud Identity 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.
keywords: ID 서비스
title: 2021 릴리스 노트
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Experience Cloud ID 서비스 릴리스 노트 - 2021

Experience Cloud ID 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.

## Visitor 5.3.0

다음 업데이트는 Visitor 5.3.0 릴리스에 포함되어 있습니다.

* 로컬 ECID를 생성하도록 알고리즘을 업데이트했습니다.
* 최신 옵트인 사용 `Secure` 및 `SameSite` 개인 정보 쿠키에 대한 플래그입니다.
* 하위 iFrame에 페이지가 로드될 때 Firefox 브라우저 문제에 대한 패치 수정.

## Visitor 5.2.0

다음 업데이트가 방문자 5.2.0 릴리스에 포함되어 있습니다.

* 이 버전에서는 이벤트를 도입했습니다 `onRecieveEcid`: ID 서비스에서 ECID를 받을 때 호출됩니다. 예:

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
