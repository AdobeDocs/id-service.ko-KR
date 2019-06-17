---
description: '일부 구현에서 방문자 ID가 JavaScript에서 서버로 전달되므로 서버에서 추가 Analytics 이벤트(예: 구입)를 전송할 수 있습니다.'
keywords: ID 서비스
seo-description: '일부 구현에서 방문자 ID가 JavaScript에서 서버로 전달되므로 서버에서 추가 Analytics 이벤트(예: 구입)를 전송할 수 있습니다.'
seo-title: JavaScript와 혼합된 서버측 구현
title: JavaScript와 혼합된 서버측 구현
uuid: 256 EA 0 E 7-1 EB 4-4 C 92-9 A 7 E-F 61 CB 1 ED 13 C 7
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# JavaScript와 혼합된 서버측 구현 {#server-side-implementation-mixed-with-javascript}

일부 구현에서 방문자 ID가 JavaScript에서 서버로 전달되므로 서버에서 추가 Analytics 이벤트(예: 구입)를 전송할 수 있습니다.

ID 서비스 API는 ID 값을 검색한 다음 서버로 전달하기 위해 [getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md) 및 [getAnalyticsVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md) 메서드를 제공합니다.

Experience Cloud 방문자 ID와 Analytics 방문자 ID를 모두 확인하고 두 ID(있는 경우)를 모두 전송하여 전송된 데이터가 기존 Analytics 방문자 프로필과 연결되어 있는지 확인합니다.

>[!IMPORTANT]
>
>Appmeasurement for Java는 현재 Experience Cloud ID 서비스를 지원하지 않습니다.

## 데이터 삽입 API {#section-955ce7664a4646d38b3005cb2df40baf}

Analytics 방문자 ID (설정된 경우) 를 `<visitorID>` 요소에 포함합니다.

요소에 Experience Cloud 방문자 ID `<marketingCloudVisitorID>` 를 포함합니다.

[지원되는 XML 태그](https://marketing.adobe.com/developer/en_US/documentation/data-insertion/r-supported-tags)를 참조하십시오.

## Java용 AppMeasurement {#section-d664b94934924d048300d9c2b6560085}

AppMeasurement for Java는 현재 Experience Cloud ID 서비스를 지원하지 않습니다.