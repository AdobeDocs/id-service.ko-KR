---
description: ID 요청 및 응답 프로세스를 대략적으로 나타낸 것입니다. 이러한 예제에서는 개별 사이트, 여러 다른 사이트 및 자체 조직 ID가 있는 다른 Experience Cloud 고객이 관리하는 사이트에 대한 ID 지정을 다룹니다.
keywords: ID 서비스
seo-description: ID 요청 및 응답 프로세스를 대략적으로 나타낸 것입니다. 이러한 예제에서는 개별 사이트, 여러 다른 사이트 및 자체 조직 ID가 있는 다른 Experience Cloud 고객이 관리하는 사이트에 대한 ID 지정을 다룹니다.
seo-title: Experience Cloud ID 서비스가 ID 요청 및 설정
title: Experience Cloud ID 서비스가 ID 요청 및 설정
uuid: FF 7 F 5 B 7 E-E 959-4391-B 75 C-B 7 A 36286 E 0 EA
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Experience Cloud ID 서비스가 ID 요청 및 설정{#how-the-experience-cloud-id-service-requests-and-sets-ids}

ID 요청 및 응답 프로세스를 대략적으로 나타낸 것입니다. 이러한 예제에서는 개별 사이트, 여러 다른 사이트 및 자체 조직 ID가 있는 다른 Experience Cloud 고객이 관리하는 사이트에 대한 ID 지정을 다룹니다.

>[!NOTE]
>
>Experience Cloud ID 서비스가 방문자 ID를 만드는 방법에 익숙하지 않은 경우 잠시 시간을 내어 [Experience Cloud](../mcvid-introduction/mcvid-cookies.md)를 검토하십시오.

**팁:** [교차 도메인 추적에 나와 있는 ID 서비스 비디오](https://helpx.adobe.com/marketing-cloud-core/kb/MCID/CrossDomain.html)를 참조하십시오.

## Experience Cloud ID 요청 {#section-0b5e261fbd0547d9b9a1680e5ce536cc}

다음 예제에서는 ID 서비스에서 Experience Cloud 방문자 ID를 요청하고 수신하는 방법을 보여줍니다. 이러한 예에서는 두 개의 가상 회사인 Food Company와 Sports Company를 사용하여 ID 요청 및 응답에 대한 데이터 흐름을 보여줍니다. 회사마다 고유한 Experience Cloud 조직 ID가 있으며 모든 사이트에 ID 서비스 코드가 구현되어 있습니다. 이러한 사용 사례에서는 Analytics, 이전 ID 또는 타사 쿠키를 차단하는 브라우저가 없는 일반적인 ID 서비스에 대한 데이터 흐름을 나타냅니다.

![](assets/sample_sites.png)

**첫 번째 요청**

이 예제에서 새 방문자는 Food Company에서 관리하는 피자 사이트를 방문합니다. Food Company의 피자 웹 사이트에는 ID 서비스 코드가 있습니다. 피자 사이트가 로드되면 ID 서비스 코드가 피자 도메인에서 AMCV 쿠키를 확인합니다.

* AMCV 쿠키가 설정된 경우 사이트 방문자에게는 Experience Cloud ID가 있습니다. 이 경우 쿠키는 방문자를 추적하고 데이터를 다른 Experience Cloud 솔루션과 공유합니다.
* AMCV 쿠키가 설정되지 않은 경우 ID 서비스 코드는 [에서 지역 데이터 수집 서버(](https://marketing.adobe.com/resources/help/en_US/aam/?f=c_compcollect.html)DCS`dpm.demdex.net/id`)를 호출합니다([Demdex 도메인 호출 이해](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) 참조). 이 호출에는 Food Company에 대한 조직 ID가 포함됩니다. 조직 ID는 ID 서비스 코드의 `Visitor.getInstance` 함수에 설정됩니다.

![](assets/request1.png)

**첫 번째 응답**

응답에서 DCS는 [!DNL Experience Cloud] ID(MID) 및 demdex 쿠키를 반환합니다. ID 서비스 코드는 AMCV 쿠키에 MID 값을 씁니다. 예를 들어 DCS가 MID 값 1234를 반환한다고 가정할 경우 AMCV 쿠키가 `mid|1234`로 저장되고 자사의 피자 도메인에 설정됩니다. demdex 쿠키에도 고유한 ID(5678)가 포함되어 있습니다. 이 쿠키는 피자 도메인과는 별개인 타사의 demdex.net 도메인에 설정됩니다.

![](assets/response1.png)

다음 예제와 같이 방문자가 Food Company에 속하는 다른 사이트로 이동할 경우 ID 서비스는 demdex ID 및 조직 ID를 사용하여 올바른 MID를 만들고 반환할 수 있습니다.

## 사이트 간 요청 및 응답 {#section-15ea880453af467abd2874b8b4ed6ee9}

이 예제에서 Food Company 방문자는 피자 사이트에서 타코 사이트로 이동합니다. Food Company의 타코 웹 사이트에는 ID 서비스 코드가 있습니다. 방문자는 타코 웹 사이트를 방문해본 적이 없습니다.

이러한 상황을 고려할 때 타코 사이트에는 AMCV 쿠키가 없습니다. 또한 해당 AMCV 쿠키는 피자 도메인에 고유하게 적용되므로 ID 서비스는 피자 사이트에 설정된 AMCV 쿠키를 사용할 수 없습니다. 따라서 ID 서비스는 DCS를 호출하여 방문자 ID를 확인하고 요청해야 합니다. 이 경우 DCS 호출에는 Food Company의 조직 ID *및* demdex ID가 포함됩니다. 또한 demdex ID가 피자 사이트에서 선택된 후 demdex.net 도메인 아래에 타사 쿠키로 저장됩니다.

![](assets/request2.png)

DCS는 조직 ID 및 demdex ID를 수신한 후에 사이트 방문자에 대한 올바른 MID를 만들고 반환합니다. MID는 조직 ID 및 demdex ID에서 수학적으로 파생되므로 AMCV 쿠키에 값 `mid = 1234`mid = 가 포함됩니다.

![](assets/response2.png)

## 다른 사이트의 ID 요청 {#section-ba9a929e50d64b0aba080630fd83b6f1}

이 예제에서 방문자는 Food Company 사이트를 나간 후 Sports Company에서 소유하는 축구 사이트로 이동합니다. 방문자가 축구 사이트를 방문하면 ID 확인 및 요청 프로세스가 이전 예제에서 설명한 것과 동일한 방식으로 작동합니다. 그렇지만 Sports Company에는 자체 조직 ID가 있으므로 ID 서비스는 다른 MID를 반환합니다. 새 MID는 Sports Company에서 제어하는 도메인에 고유하며, 해당 기업이 [!DNL Experience Cloud]에서 솔루션 간에 방문자 데이터를 추적하고 공유할 수 있게 해 줍니다. demdex ID는 타사 쿠키에 포함되고 도메인이 달라져도 그대로 유지되므로 이 방문자에 대해 동일하게 유지됩니다.

![](assets/req_resp.png)

