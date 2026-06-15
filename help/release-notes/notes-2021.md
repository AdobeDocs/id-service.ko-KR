---
description: Experience Cloud ID 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.
keywords: ID 서비스
title: 2021 릴리스 정보
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
TQID: https://experienceleague.adobe.com/AB8VuYn9X41P9REJ8C215GzBRtH66lb35i-q1PNbZfU
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 110
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

