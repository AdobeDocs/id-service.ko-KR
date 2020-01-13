---
title: 고유 방문자 식별
description: Adobe ECID(ID 서비스)에 대한 문서
translation-type: ht
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# 고유 방문자 식별

다수의 컨텍스트 중에서 고유한 방문자를 식별하는 방법에는 우선 순위가 지정된 시퀀스가 포함되어 있어 이 결정에서 정확성을 보장합니다. 다음 표에는 해당 우선 순위가 지정된 시퀀스가 표시됩니다.


 
| 사용된 순서 | 쿼리 매개 변수(수집 방법) | post_visid_type 열 값 | 제공 시기 |
|--- |--- |--- |--- |
| 1 | [vid (s.visitorID)](https://marketing.adobe.com/resources/help/ko_KR/sc/implement/visid_custom.html) | 0 |s.visitorID가 설정되어 있습니다.| 
| 2 | [aid(s_vi cookie)](https://marketing.adobe.com/resources/help/ko_KR/sc/implement/visid_analytics.html) | 3 |방문자 ID 서비스를 배포하기 전 방문자에게 이미 s_vi 쿠키가 있었거나 방문자 ID [유예 기간](https://marketing.adobe.com/resources/help/ko_KR/mcvid/mcvid_grace_period.html)을 구성했습니다. |
| 3 | [mid(Identity Service에 의해 설정된 AMCV_ 쿠키)](https://marketing.adobe.com/resources/help/ko_KR/mcvid/) | 5 | 방문자의 브라우저에서 쿠키(퍼스트 파티)를 승인하고, Identity Service가 배포됩니다 . |
| 4 | [fid(H.25.3 이상 또는 JavaScript용 AppMeasurement에서 쿠키 폴백)](https://marketing.adobe.com/resources/help/ko_KR/sc/implement/visid_fallback.html) | 4 | 방문자의 브라우저에서 쿠키(퍼스트 파티)를 승인합니다. |
| 5 | [HTTP 모바일 가입자 헤더](https://marketing.adobe.com/resources/help/ko_KR/sc/implement/visid_fallback.html) | 2 | 장치가 모바일 장치로 인식됩니다. |
| 6 | [IP 주소, 사용자 에이전트, 게이트웨이 IP 주소](https://marketing.adobe.com/resources/help/ko_KR/sc/implement/visid_fallback.html) | 1 | 방문자의 브라우저에서 쿠키를 승인하지 않습니다. |


고유 방문자를 보고하는 방법에 대한 자세한 내용은 [Analytics 고유 방문자](https://docs.adobe.com/content/help/ko-KR/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)를 참조하십시오.
