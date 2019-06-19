---
description: 동일한 보고서 세트에 데이터를 전송 중인 JavaScript 파일이 여러 개 있거나 사이트에서 Flash 비디오 측정과 같은 기타 기술을 사용하는 경우에는 유예 기간을 구성하는 것이 좋습니다.
keywords: ID 서비스
seo-description: 동일한 보고서 세트에 데이터를 전송 중인 JavaScript 파일이 여러 개 있거나 사이트에서 Flash 비디오 측정과 같은 기타 기술을 사용하는 경우에는 유예 기간을 구성하는 것이 좋습니다.
seo-title: ID 서비스 유예 기간
title: ID 서비스 유예 기간
uuid: 10 A 7 DB 7 D-DE 32-4379-914 F-EDAF 929 EFA 32
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# ID 서비스 유예 기간 {#the-id-service-grace-period}

동일한 보고서 세트에 데이터를 전송 중인 JavaScript 파일이 여러 개 있거나 사이트에서 Flash 비디오 측정과 같은 기타 기술을 사용하는 경우에는 유예 기간을 구성하는 것이 좋습니다.

[!DNL Experience Cloud] ID 서비스를 배포하면 새 방문자가 더 이상 데이터 수집 서버에서 Analytics 방문자 ID를 받지 않습니다. [!DNL Experience Cloud] ID 서비스가 아직 구현되지 않은 사이트의 섹션으로 방문자가 이동하면 Experience Cloud ID가 인식되지 않으며 방문자에게 이전 Analytics 방문자 ID가 지정됩니다. 이를 통해 중복된 방문 수 및 잘못된 기여가 생성될 수 있습니다.

예를 들어 사이트의 지원 섹션에 별도의 CMS에서 관리되는 경우 이 섹션에 대해 다른 Analytics JavaScript 파일을 보유할 수 있습니다. 지원 사이트에 방문자 ID 서비스를 배포하기 전에 기본 사이트에 방문자 ID를 배포하는 경우 새 방문자가 지원 섹션을 방문할 때 이전 Analytics ID를 받게 되며 두 사이트 섹션에 걸쳐 진행되는 방문이 다른 방문으로 보고됩니다.

여러 JavaScript 파일 또는 다른 기술(예: Flash)을 사용하는 사이트에 [!DNL Experience Cloud] ID 서비스를 배포하면 사이트의 모든 부분에서 동시에 해당 ID 서비스를 사용하도록 설정해야 하므로 조정 문제가 발생할 수 있습니다. 유예 기간을 구성하면 새 방문자가 [!DNL Experience Cloud] ID 서비스에서 Analytics 방문자 ID를 계속 받게 되므로 방문자는 ID 서비스를 사용하도록 업그레이드되지 않은 사이트의 섹션에서 일관되게 식별될 수 있습니다.

>[!NOTE]
>
>유예 기간 지원을 위해서는 [!DNL Experience Cloud] ID 서비스의 버전 1.3 이상이 필요합니다.

## 유예 기간이 필요합니까? {#section-fd34c7ff697348a39f49258b7d39eb42}

단일 Analytics JavaScript 파일이 있고 다른 AppMeasurement 라이브러리를 사용하지 않는 경우에는 유예 기간이 필요하지 않을 수 있습니다. 단일 JavaScript 파일로 업데이트를 만들면 새 방문자가 방문 중에 Marketing Cloud ID를 사용하여 일관되게 식별됩니다.

*동일한 보고서 세트*에 데이터를 전송 중인 JavaScript 파일이 여러 개 있거나 사이트에서 Flash 비디오 측정과 같은 기타 기술을 사용하는 경우에는 유예 기간을 구성하는 것이 좋습니다.

## 유예 기간을 활성화하려면 어떻게 해야 합니까? {#section-512d5cd8570e483cbdd8b04457a16ced}

고객 지원 센터에 [](https://helpx.adobe.com/marketing-cloud/contact-support.html)문의하십시오.