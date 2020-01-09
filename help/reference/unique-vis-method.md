---
title: 고유 방문자 식별
description: Adobe ECID(ID 서비스) 설명서
translation-type: tm+mt
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# 고유 방문자 식별

여러 컨텍스트 중 고유 방문자를 식별하는 방법에는 우선 순위가 지정된 시퀀스가 포함되어 있으므로 이 결정의 정확성을 보장합니다. 다음 표는 우선 순위가 지정된 시퀀스를 보여줍니다.


 
| 사용된 순서| 쿼리 매개 변수(컬렉션 메서드)| post_visid_type 열 값| 제공 시기||—|—|—|—|| 1 |[vid(s.visitorID)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_custom.html)| 0 |s.visitorID가 설정되었습니다.| 
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_analytics.html) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_grace_period.html) configured.|| 3 |[mid(ID 서비스에서 설정된 AMCV_ 쿠키)](https://marketing.adobe.com/resources/help/en_US/mcvid/)| 5 | 방문자의 브라우저가 쿠키를 수락하고(퍼스트 파티) ID 서비스가 배포됩니다.|| 4 |[fid(H.25.3 이상 버전의 폴백 쿠키 또는 JavaScript용 AppMeasurement)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 4 | 방문자 브라우저가 쿠키를 수락함(퍼스트 파티).|| 5 |[HTTP 모바일 구독자 헤더](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_mobile.html)| 2 | 장치가 모바일 장치로 인식됩니다.|| 6 |[IP 주소, 사용자 에이전트, 게이트웨이 IP 주소](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 1 | 방문자의 브라우저가 쿠키를 허용하지 않습니다. |


고유 방문자가 보고되는 방식에 대한 자세한 내용은 Analytics의 고유 [방문자를 참조하십시오](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
