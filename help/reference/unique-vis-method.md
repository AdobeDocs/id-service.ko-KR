---
title: 고유 방문자 식별
description: Adobe ECID(ID 서비스)에 대한 문서
translation-type: tm+mt
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 100%

---


# 고유 방문자 식별

다수의 컨텍스트 중에서 고유한 방문자를 식별하는 방법에는 우선 순위가 지정된 시퀀스가 포함되어 있어 이 결정에서 정확성을 보장합니다. 다음 표에는 해당 우선 순위가 지정된 시퀀스가 표시됩니다.

| 사용된 명령 | 쿼리 매개 변수(수집 방법) | post_visid_type 열 값 | 제공 시점 |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/ko-KR/analytics/technotes/visitor-identification.html)  | 0  | `s.visitorID`이(가) 설정되어 있습니다. |
|  2  | aid  [s_vi 쿠키](https://docs.adobe.com/content/help/ko-KR/analytics/technotes/visitor-identification.html)  | 3  | 방문자 ID 서비스를 배포하기 전 방문자에게 이미 s_vi 쿠키가 있었거나 방문자 ID [유예 기간](https://docs.adobe.com/content/help/ko-KR/id-service/using/reference/analytics-reference/grace-period.html)을 구성했습니다.  |
|  3  | mid [AMCV_ cookie, Identity 서비스에서 설정](https://docs.adobe.com/content/help/ko-KR/id-service/using/home.html)  |  5  |  방문자의 브라우저가 쿠키를 승인하고 (자사) [!UICONTROL Identity 서비스]가 배포됩니다.  |
|  4  | fid [H.25.3 이상의 폴백 쿠키 또는 AppMeasurement for JavaScript](https://docs.adobe.com/content/help/ko-KR/analytics/technotes/visitor-identification.html)  |  4  | 방문자의 브라우저가 쿠키를 승인합니다(자사).  |
|  5  |  [HTTP 모바일 가입자 헤더](https://docs.adobe.com/content/help/ko-KR/analytics/technotes/visitor-identification.html)  |  2  |  장치는 모바일 장치로 인식됩니다.  |
|  6  |  [IP 주소, 사용자 에이전트, 게이트웨이 IP 주소](https://docs.adobe.com/content/help/ko-KR/analytics/technotes/visitor-identification.html)  |  1  |  방문자의 브라우저가 쿠키를 승인하지 않습니다. |

고유 방문자를 보고하는 방법에 대한 자세한 내용은 [Analytics 고유 방문자](https://docs.adobe.com/content/help/ko-KR/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)를 참조하십시오.
