---
description: IAB TCF(Transparency and Consent Framework)를 위한 옵트인의 Audience Manager 플러그인과 CMP(동의 관리 플랫폼)를 연결합니다.
title: IAB 프레임워크에서 옵트인 서비스 사용
exl-id: 9ac9b232-0797-4e77-a611-9cf5d17a5cb7
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 89%

---

# IAB 프레임워크에서 옵트인 서비스 사용{#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>다음 문서는 IAB 2.0에만 적용됩니다. 사용자는 IAB 2.0에서 작업하려면 Visitor.js 버전 5.0을 사용해야 합니다.

CMP(동의 관리 플랫폼)을 옵트인의 IAB 투명도 및 TCF(Transparency and Consent Framework) 플러그인과 연결합니다.

[IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/)를 사용하는 Adobe Audience Manager 고객은 CMP(동의 관리 플랫폼)을 옵트인의 IAB TCF 플러그인과 연결할 수 있습니다. 옵트인은 CMP 내에 설정된 방문자 환경 설정에 따라 개별 Adobe 솔루션 라이브러리를 비활성화할 수 있는 ECID JavaScript 라이브러리 내에 포함된 기능입니다. 옵트인의 IAB TCF 플러그인이 ECID 라이브러리로 구현되면 IAB TCF를 지원하는 CMP의 방문자 환경 설정이 자동으로 옵트인에 매핑됩니다. 이러한 환경 설정은 동의를 받으면 Audience Manager 기반 라이브러리(DIL 및 ECID) 및 연관된 호출을 활성화합니다.

## IAB를 지원하는 CMP 구현 {#section-9fd2403b548947dbb1921ac6ff9d0c82}

옵트인을 IAB TCF와 통합하려면 다음을 완료해야 합니다.

1. IAB를 지원하고 IAB 공급업체로 등록된 CMP를 구현하거나, IAB TCF 사양을 구현하는 내부 CMP를 개발하고 IAB TCF에 CMP로 등록합니다.
1. Adobe JS를 로드하기 전에 `__tcfapi`를 정의/로드합니다.

자세한 내용은[Interactive Advertising Bureau 문서](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md)를 참조하십시오.

## ECID Javascript 라이브러리 내에서 옵트인의 IAB TCF 플러그인 활성화 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>옵트인은 ECID 4.0+에서만 사용할 수 있습니다.

Adobe Experience Platform Launch를 사용하여 사이트에 대해 옵트인의 IAB TCF 플러그인을 구현합니다. 옵트인용 IAB를 수동으로 활성화하는 경우, 방문자 개체 내에서 다음 설정이 true로 설정되어 있는지 확인하십시오.

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

설정이 올바르게 구성되면 CMP 및 IAB TCF의 동의 기준에 따라 ECID 및 DIL 라이브러리가 활성화/비활성화됩니다.

>[!IMPORTANT]
>
>쿠키를 배포하고 ID 동기화를 시작하거나 처리하려면 Audience Manager는 *purpose 1, 10에 대한 동의와 공급업체 동의*&#x200B;가 필요합니다. [여기](https://docs.adobe.com/help/ko-KR/audience-manager/user-guide/overview/gdpr/aam-iab-plugin.html)에 나와 있는 Audience Manager 설명서에서 옵트인의 IAB TCF 플러그인에 대해 자세히 알아보십시오.

옵트인과 IAB TCF 플러그인을 확인하는 방법에 대해서는 [여기](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)에 나와 있는 유효성 검사 안내서의 사용 사례 4를 확인하십시오.

## 관련 설명서 {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB TCF(Transparency and Consent Framework)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - IAB 표준에 대한 자세한 정보
* [Adobe 옵트인](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - 플랫폼 솔루션의 동의 관리에 필요한 구성 요소인 옵트인에 대한 자세한 정보
* [Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=ko-KR)에서 IAB TCF(Transparency and Consent Framework) 지원
* [개인정보 보호 선택 사항](https://www.adobe.com/kr/privacy/opt-out.html#customeruse) - 사용자 처리 시 다른 개인정보 보호 옵션은 다른 전역 옵트아웃 도구를 사용하여 모든 데이터 수집을 옵트아웃하는 기능입니다. 전역 옵트아웃이 옵트인 및 IAB TCF 확인보다 우선함
