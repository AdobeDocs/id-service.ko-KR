---
description: AMCV 쿠키에는 사이트 방문자에 대한 Experience Cloud ID(MID) 및 지역 ID가 포함되어 있습니다. 이러한 ID는 키-값 쌍으로 저장됩니다. mid 사용자 ID는 방문자의 Experience Cloud ID를 보유합니다. aamlh 지역 ID는 사이트 방문자에 대한 지역 ID를 보유합니다. AMCV 쿠키를 구문 분석하여 해당 정보를 복구할 수 있습니다.
keywords: ID Service
seo-description: AMCV 쿠키에는 사이트 방문자에 대한 Experience Cloud ID(MID) 및 지역 ID가 포함되어 있습니다. 이러한 ID는 키-값 쌍으로 저장됩니다. mid 사용자 ID는 방문자의 Experience Cloud ID를 보유합니다. aamlh 지역 ID는 사이트 방문자에 대한 지역 ID를 보유합니다. AMCV 쿠키를 구문 분석하여 해당 정보를 복구할 수 있습니다.
seo-title: AMCV 쿠키 또는 ID 서비스에서 지역 및 사용자 ID 가져오기
title: AMCV 쿠키 또는 ID 서비스에서 지역 및 사용자 ID 가져오기
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# AMCV 쿠키 또는 ID 서비스에서 지역 및 사용자 ID 가져오기 {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV 쿠키에는 사이트 방문자에 대한 Experience Cloud ID(MID) 및 지역 ID가 포함되어 있습니다. 이러한 ID는 키-값 쌍으로 저장됩니다. mid:사용자 ID는 방문자의 Experience Cloud ID를 보유합니다. amlh:region ID는 사이트 방문자의 지역 ID를 보관합니다. AMCV 쿠키를 구문 분석하여 해당 정보를 복구할 수 있습니다.

For more information, see [Get User IDs and Regions Through the Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

[!DNL Audience Manager] 고객인 경우, DCS(데이터 수집 서버)에서 전송한 응답에서 지역 ID를 가져올 수 있습니다. See [Get User IDs and Regions from a DCS Response](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

또한 ID 서비스에서 제공한 `GET` 메서드로 지역 ID를 가져올 수도 있습니다. [지역 ID 가져오기(위치 힌트)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)를 참조하십시오.
