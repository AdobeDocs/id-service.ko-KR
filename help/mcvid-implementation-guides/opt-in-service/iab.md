---
description: 동의 관리 플랫폼 (CMP) 를 옵트인 IAB 플러그인과 연결합니다.
seo-description: 동의 관리 플랫폼 (CMP) 를 옵트인 IAB 플러그인과 연결합니다.
seo-title: (베타) IAB Framework와 함께 옵트인 서비스 사용
title: (베타) IAB Framework와 함께 옵트인 서비스 사용
uuid: 8 df 39 d 9 c-c 016-490 e-b 4 db-d 02 e 4044 b 480
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# (베타) IAB Framework와 함께 옵트인 서비스 사용{#beta-using-opt-in-services-with-iab-framework}

동의 관리 플랫폼 (CMP) 를 옵트인 IAB 플러그인과 연결합니다.

[IAB 투명도 및 동의 프레임워크 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) 를 사용하는 Audience Manager 고객은 동의 관리 플랫폼 (CMP) 를 옵트인 IAB 플러그인과 연결할 수 있습니다. 옵트인은 CMP 내에 설정된 방문자 기본 설정에 따라 개별 Adobe 솔루션 라이브러리를 비활성화할 수 있는 ECID JavaScript 라이브러리 내에 포함된 기능입니다. IAB 플러그인을 ECID 라이브러리로 구현하면 IAB 호환 CMP의 방문자 기본 설정이 옵트인에 자동으로 매핑됩니다. 이러한 기본 설정은 동의할 때 Audience Manager 기반 라이브러리 (DIL 및 ECID) 와 관련 호출을 활성화합니다.

## IAB를 지원하는 CMP 구현 {#section-9fd2403b548947dbb1921ac6ff9d0c82}

옵트인을 IAB 동의와 통합하려면 다음을 완료해야 합니다.

1. IAB를 지원하고 [IAB 공급업체로 등록된](https://vendorlist.consensu.org/vendorlist.json) CMP를 구현하거나, IAB 사양을 구현하는 내부 CMP를 개발하고 IAB 유럽에 CMP로 등록합니다.
1. Adobe JS를 `__cmp` 로드하기 전에를 정의/로드합니다.

자세한 내용은[Interactive Advertising Bureau 문서](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md)를 참조하십시오.

## ECID Javascript 라이브러리 내에서 IAB 플러그인 활성화 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>옵트인은 ECID 4.0 + 에서만 사용할 수 있습니다.

사이트에 대한 옵트인과 IAB 플러그인을 모두 구현하려면 Adobe Launch를 사용하십시오. Launch 확장을 설정하는 방법을 자세히 알아보려면 [ECID 옵트인 확장에 대한 설명서](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/)를 읽어 보십시오.

옵트인에 대한 IAB를 수동으로 활성화할 때 Visitor 개체 내에 다음 설정이 true로 지정되어 있는지 확인하십시오.

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

설정이 올바르게 구성되어 있으면 CMP 및 IAB 프레임워크의 동의 기준에 따라 ECID 및 DIL 라이브러리가 활성화/비활성화됩니다.

>[!IMPORTANT]
>
>쿠키를 배포하고 ID 동기화를 시작하거나 처리하려면 Audience Manager는 *purposes 1, 2, 5에 대한 동의와 공급업체 동의*가 필요합니다. Adobe Audience Manager 설명서의 IAB 플러그인** [여기를](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)참조하십시오**.

옵트인과 IAB 플러그인을 모두 확인하는 방법에 대해서는 [**여기**](../../mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)에 나와 있는 유효성 검사 가이드의 사용 사례 4를 확인하십시오 .

## 관련 설명서 {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB TCF(Transparency and Consent Framework)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - IAB 표준에 대한 자세한 정보
* [Adobe 옵트인](../../mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - 플랫폼 솔루션의 동의 관리에 필요한 구성 요소인 옵트인에 대한 자세한 정보
* [Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)의 IAB TCF(Transparency and Consent Framework) 지원
* [개인 정보 보호 선택 사항](https://www.adobe.com/privacy/opt-out.html#customeruse) - 사용자 처리 시 다른 개인 정보 보호 옵션은 다른 전역 옵트아웃 도구를 사용하여 모든 데이터 수집을 옵트아웃하는 기능입니다. 전역 옵트아웃이 옵트인 및 IAB 확인보다 우선함
