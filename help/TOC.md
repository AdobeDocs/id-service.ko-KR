---
audience: end-user
user-guide-title: Adobe 방문자 ID 서비스 도움말
breadcrumb-title: 방문자 ID 서비스 안내서
user-guide-description: Adobe 방문자 ID 서비스는 CX Enterprise의 모든 솔루션에서 방문자를 식별하는 범용 영구 ID를 제공합니다. CX 엔터프라이즈 솔루션 및 서비스의 기존 ID 생성 코드를 대체하는 데 도움이 됩니다.
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 7621dc8925235bd3cf159a404741bd02fc9b6a77
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 45%

---


# Adobe 방문자 ID 서비스 도움말 {#using}

+ [방문자 ID 서비스 도움말](home.md)
+ 개요 {#intro}
   + [개요](introduction/overview.md)
   + [방문자 ID 서비스 정보](introduction/about-id-service.md)
   + [쿠키 및 방문자 ID 서비스](introduction/cookies.md)
   + [방문자 ID 서비스에서 ID를 요청하고 설정하는 방법](introduction/id-request.md)
   + [동기화 및 일치율 이해하기](introduction/match-rates.md)
+ 구현 {#implementation}
   + [구현 방법](implementation-guides/implementation-methods.md)
   + [구현 안내서](implementation-guides/implementation-guides.md)
   + [태그를 사용한 구현](implementation-guides/ecid-implement-with-launch.md)
   + [Analytics 구현](https://experienceleague.adobe.com/ko/docs/analytics/implementation/id/overview){target=_blank}
   + [Target 구현](implementation-guides/setup-target.md)
   + [Analytics 및 Audience Manager 구현](implementation-guides/setup-aam-analytics.md)
   + [Analytics, Audience Manager 및 Target 구현](implementation-guides/setup-aam-analytics-target.md)
   + [Target의 서버측 구현 및 A4T에 방문자 ID 서비스 사용](implementation-guides/ecid-a4t-target.md)
   + [방문자 ID 서비스와 직접 통합](implementation-guides/direct-integration.md)
   + [직접 통합 사용 사례](implementation-guides/direct-integration-examples.md)
   + [방문자 ID 서비스 테스트 및 확인](implementation-guides/test-verify.md)
   + 옵트인 서비스 {#opt-in-service}
      + [옵트인 서비스 개요](implementation-guides/opt-in-service/optin-overview.md)
      + [옵트인 서비스 설정](implementation-guides/opt-in-service/getting-started.md)
      + [옵트인 서비스 확인](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [태그를 사용하여 옵트인 구성](implementation-guides/opt-in-service/launch.md)
      + [사용자 동의에 따라 CX 엔터프라이즈 활동 제어](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [옵트인 사용 사례](implementation-guides/opt-in-service/use-cases.md)
      + [옵트인 참조](implementation-guides/opt-in-service/api.md)
      + [IAB 프레임워크에서 옵트인 서비스 사용](implementation-guides/opt-in-service/iab.md)
+ 방문자 ID 서비스 API {#id-service-api}
   + [방문자 ID 서비스 API 개요](library/library.md)
   + 구성 {#configurations}
      + [구성 개요](library/function-vars/function-vars.md)
      + [audienceManagerServer 및 audienceManagerServerSecure](library/function-vars/subdomain-config.md)
      + [cookieDomain](library/function-vars/cookiedomain.md)
      + [cookieLifetime](library/function-vars/cookielifetime.md)
      + [disableIdSyncs](library/function-vars/disableidsync.md)
      + [disableThirdPartyCalls](library/function-vars/disablethirdpartycalls.md)
      + [disableThirdPartyCookies](library/function-vars/disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](library/function-vars/idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](library/function-vars/idsyncontainerid.md)
      + [idSyncSSLUseAkamai](library/function-vars/idsyncssluseakamai.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
      + [보안 및 SameSite 구성](library/function-vars/secure-samesite-config.md)
      + [secureCookie](library/function-vars/securecookie.md)
      + [useCORSOnly](library/function-vars/use-cors-only.md)
      + [whitelistParentDomain 및 whitelistIframeDomains](library/function-vars/whitelistdomain.md)
   + 메서드에서 사용할 수 있습니다 {#methods}
      + [메서드에서 사용할 수 있습니다](library/get-set/get-set.md)
      + [appendSupplementalDataIDTo](library/get-set/appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (도메인 간 추적)](library/get-set/appendvisitorid.md)
      + [callTimeOut 메서드](library/get-set/timeout-functions.md)
      + [URL 또는 데이터 소스별 ID 동기화](library/get-set/idsync.md)
      + [getInstance](library/get-set/getinstance.md)
      + [getAnalyticsVisitorID](library/get-set/getanalyticsvisitorid.md)
      + [getCustomerIDs](library/get-set/getcustomerids.md)
      + [setCustomerIDs](library/get-set/setcustomerids.md)
      + [getMarketingCloudVisitorID](library/get-set/getmcvid.md)
      + [getLocationHint](library/get-set/getlocationhint.md)
      + [getVisitorValues](library/get-set/getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](library/get-set/client-side-id.md)
      + [resetState](library/get-set/resetstate.md)
+ 참조 {#reference}
   + [참조 개요](reference/reference.md)
   + [Google Chrome SameSite 레이블 설정 변경](reference/chrome-samesite-labelling.md)
   + [컨텐츠 보안 정책 및 방문자 ID 서비스](reference/csp.md)
   + [방문자 ID 서비스의 COPPA 지원](reference/coppa.md)
   + [방문자 ID 서비스의 CORS 지원](reference/cors.md)
   + [고객 ID 및 인증 상태](reference/authenticated-state.md)
   + [Safari ITP 환경의 ECID 라이브러리 메서드](reference/ecid-library-methods.md)
   + [고유 방문자 식별](reference/unique-vis-method.md)
   + [AMCV 쿠키 또는 방문자 ID 서비스에서 지역 및 사용자 ID 가져오기](reference/regions.md)
   + [방문자 ID 서비스 요구 사항](reference/requirements.md)
   + [비디오 하트비트 및 방문자 ID 서비스](reference/heartbeat.md)
   + [setCustomerIDs에 대한 SHA256 해시 지원](reference/hashing-support.md)
+ FAQ {#faqs}
   + [FAQ 개요](faq-intro/faq-intro.md)
   + [방문자 ID 서비스 FAQ](faq-intro/faq.md)
   + [기타 CX 엔터프라이즈 솔루션에 대한 FAQ](faq-intro/other-faq.md)
+ 방문자 ID 서비스에 대한 릴리스 노트 {#release-notes}
   + [2022 릴리스 정보](release-notes/notes-2022.md)
   + [2021 릴리스 정보](release-notes/notes-2021.md)
   + [2020 릴리스 정보](release-notes/notes-2020.md)
   + [2019 릴리스 정보](release-notes/notes-2019.md)
   + [2018 릴리스 정보](release-notes/notes-2018.md)
   + [2017 릴리스 정보](release-notes/notes-2017.md)
   + [2016 릴리스 정보](release-notes/notes-2016.md)
   + [2015 릴리스 정보](release-notes/notes-2015.md)
