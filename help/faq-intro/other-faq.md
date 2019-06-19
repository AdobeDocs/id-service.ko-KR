---
description: ID 서비스에서 다른 Experience Cloud 솔루션 사용과 관련된 기능 및 문제에 대한 FAQ입니다.
keywords: ID 서비스
seo-description: ID 서비스에서 다른 Experience Cloud 솔루션 사용과 관련된 기능 및 문제에 대한 FAQ입니다.
seo-title: 다른 Experience Cloud 솔루션에 대한 FAQ
title: 다른 Experience Cloud 솔루션에 대한 FAQ
uuid: 7 d 848663-6 cbb -4 d 80-ab 06-7 b 6 d 2 dc 20 e 2 b
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# 다른 Experience Cloud 솔루션에 대한 FAQ{#faqs-for-other-experience-cloud-solutions}

ID 서비스에서 다른 Experience Cloud 솔루션 사용과 관련된 기능 및 문제에 대한 FAQ입니다.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**다이내믹 태그 관리를 사용하여 방문자 ID 서비스를 배포할 수 있습니까?**

예, 이 옵션이 선호되고 권장됩니다.

자세한 내용은 [DTM을 사용한 표준 구현](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)을 참조하십시오.

## Analytics 및 Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**Experience Platform Identity Service를 구현하면 사용자의 방문 내역을에서[!DNL Adobe Analytics][!DNL Audience Manager]내역으로 내보냅니까?**

다음 두 가지 옵션을 사용할 수 있습니다.

* ID 서비스가 구현된 후에 사용자에게 방문한 활동이 있으면 방문자 및 방문자 기록이 [!DNL Audience Manager]에 대한 데이터 내보내기에 포함됩니다.
* ID 서비스가 구현된 후에 사용자에게 방문한 활동이 없으면 방문자 및 방문자 기록이 Audience Manager에 대한 데이터 내보내기에 포함되지 않습니다. 새 활동이 없으므로 Analytics ID를 Experience Cloud ID와 연결할 방법이 없습니다.

