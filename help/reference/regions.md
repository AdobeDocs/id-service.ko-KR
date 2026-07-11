---
description: AMCV 쿠키에는 사이트 방문자에 대한 ECID 및 지역 ID가 포함되어 있습니다. 이러한 ID는 키-값 쌍으로 저장됩니다. mid 사용자 ID는 방문자의 ECID를 보유합니다. aamlh 지역 ID는 사이트 방문자에 대한 지역 ID를 보유합니다. AMCV 쿠키를 구문 분석하여 해당 정보를 복구할 수 있습니다.
keywords: 방문자 ID 서비스
title: AMCV 쿠키 또는 방문자 ID 서비스에서 지역 및 사용자 ID 가져오기
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
TQID: https://experienceleague.adobe.com/OBzPrrLffDFgRisA27XIIl33x-4aWmj0krXF3prLPUk
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 235
ht-degree: 42%

---

# AMCV 쿠키 또는 방문자 ID 서비스에서 지역 및 사용자 ID 가져오기 {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV 쿠키에는 사이트 방문자에 대한 ECID 및 지역 ID가 포함되어 있습니다. 이러한 ID는 키-값 쌍으로 저장됩니다. mid:user ID는 방문자의 ECID를 보유합니다. aamlh:region ID는 사이트 방문자에 대한 지역 ID를 보유합니다. AMCV 쿠키를 구문 분석하여 해당 정보를 복구할 수 있습니다.

자세한 내용은 [방문자 ID 서비스를 통해 사용자 ID 및 지역 가져오기](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html?lang=ko-KR)를 참조하십시오.

Audience Manager 고객인 경우 DCS(데이터 수집 서버)에서 전송한 응답에서 지역 ID를 가져올 수 있습니다. [DCS 응답에서 사용자 ID 및 지역 가져오기](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html?lang=ko-KR)를 참조하십시오.

방문자 ID 서비스에서 제공한 `GET` 메서드로 지역 ID를 가져올 수도 있습니다. [지역 ID 가져오기(위치 힌트)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)를 참조하십시오.

