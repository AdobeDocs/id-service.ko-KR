---
description: '일부 구현에서 방문자 ID가 JavaScript에서 서버로 전달되므로 서버에서 추가 Analytics 이벤트(예: 구입)를 전송할 수 있습니다.'
keywords: ID 서비스
title: JavaScript와 혼합된 서버측 구현
exl-id: 1986ee11-2021-4f34-bb56-6eaa87b6dd6d
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 100%

---

# JavaScript와 혼합된 서버측 구현 {#server-side-implementation-mixed-with-javascript}

일부 구현에서 방문자 ID가 JavaScript에서 서버로 전달되므로 서버에서 추가 Analytics 이벤트(예: 구입)를 전송할 수 있습니다.

ID 서비스 API는 서버에 전달할 수 있는 ID 값을 검색할 수 있도록 [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) 및 [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) 메서드를 제공합니다.

Experience Cloud 방문자 ID와 Analytics 방문자 ID를 모두 확인하고 두 ID(있는 경우)를 모두 전송하여 전송된 데이터가 기존 Analytics 방문자 프로필과 연결되어 있는지 확인합니다.

>[!IMPORTANT]
>
>Java용 AppMeasurement는 현재 Experience Cloud Identity Service를 지원하지 않습니다.

## 데이터 삽입 API {#section-955ce7664a4646d38b3005cb2df40baf}

Analytics 방문자 ID(설정된 경우)를 `<visitorID>` 요소에 포함합니다.

Experience Cloud 방문자 ID를 `<marketingCloudVisitorID>` 요소에 포함합니다.

[지원되는 XML 태그](https://developer.adobe.com/)를 참조하십시오.

## Java용 AppMeasurement {#section-d664b94934924d048300d9c2b6560085}

Experience Cloud Identity Service는 현재 Java용 AppMeasurement에서 지원하지 않습니다.
