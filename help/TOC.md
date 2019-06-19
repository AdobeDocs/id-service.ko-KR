---
cloud: experience-cloud
product: ID 서비스
audience: 최종 사용자
user-guide-title: ID 서비스 도움말
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# ID 서비스 도움말 {#using}

+ [Experience Cloud ID 서비스](home.md)
+ 개요 {#mcvid-introduction}
   + [개요](mcvid-introduction/mcvid-overview.md)
   + [ID 서비스 정보](mcvid-introduction/mcvid-about-id-service.md)
   + [쿠키 및 ExExperience Cloud ID 서비스](mcvid-introduction/mcvid-cookies.md)
   + [Experience Cloud ID 서비스가 ID 요청 및 설정](mcvid-introduction/mcvid-id-request.md)
   + [ID 동기화 및 일치 비율 이해](mcvid-introduction/mcvid-match-rates.md)
+ 구현 안내서 {#implementation-guides}
   + [구현 안내서](mcvid-implementation-guides/mcvid-implementation-guides.md)
   + [구현 방법](mcvid-implementation-guides/mcvid-implementation-methods.md)
   + [Launch를 사용한 구현](mcvid-implementation-guides/ecid-implement-with-launch.md)
   + [다이내믹 태그 관리를 사용한 구현](mcvid-implementation-guides/mcvid-standard.md)
   + [Analytics용 Experience Cloud ID 서비스 구현](mcvid-implementation-guides/mcvid-setup-analytics.md)
   + [Target용 Experience Cloud ID 서비스 구현](mcvid-implementation-guides/mcvid-setup-target.md)
   + [Analytics 및 Audience Manager용 Experience Cloud ID 서비스 구현](mcvid-implementation-guides/mcvid-setup-aam-analytics.md)
   + [Analytics, Audience Manager 및 Target용 Experience Cloud ID 서비스 구현](mcvid-implementation-guides/mcvid-setup-aam-analytics-target.md)
   + [Target의 서버측 구현 및 A4T에 Experience Cloud ID 서비스 사용](mcvid-implementation-guides/ecid-a4t-target.md)
   + [Experience Cloud ID 서비스와 직접 통합](mcvid-implementation-guides/mcvid-direct-integration.md)
   + [직접 통합 사용 사례](mcvid-implementation-guides/ecid-direct-integration-examples.md)
   + [Experience Cloud ID 서비스 테스트 및 확인](mcvid-implementation-guides/mcvid-test-verify.md)
   + 옵트인 설명서 {#opt-in-service}
      + [옵트인 서비스 개요](mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md)
      + [옵트인 서비스 설정](mcvid-implementation-guides/opt-in-service/getting-started.md)
      + [옵트인 서비스 유효성 확인](mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Launch로 옵트인 구성](mcvid-implementation-guides/opt-in-service/launch.md)
      + [DTM으로 옵트인 구성](mcvid-implementation-guides/opt-in-service/optin-dtm.md)
      + [옵트인 사용 사례](mcvid-implementation-guides/opt-in-service/use-cases.md)
      + [옵트인 참조](mcvid-implementation-guides/opt-in-service/api.md)
      + [(베타) IAB Framework와 함께 옵트인 서비스 사용](mcvid-implementation-guides/opt-in-service/iab.md)
+ ID 서비스 API {#id-service-api}
   + [ID 서비스 API 개요](mcvid-library/mcvid-library.md)
   + 구성 {#configurations}
      + [구성 개요](mcvid-library/mcvid-function-vars/mcvid-function-vars.md)
      + [audienceManagerServer 및 audienceManagerServerSecure](mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md)
      + [cookieDomain](mcvid-library/mcvid-function-vars/mcvid-cookiedomain.md)
      + [cookieLifetime](mcvid-library/mcvid-function-vars/mcvid-cookielifetime.md)
      + [disableIdSyncs](mcvid-library/mcvid-function-vars/mcvid-disableidsync.md)
      + [disableThirdPartyCalls](mcvid-library/mcvid-function-vars/mcvid-disablethirdpartycalls.md)
      + [disableThirdPartyCookies](mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](mcvid-library/mcvid-function-vars/mcvid-idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md)
      + [idSyncSSLUseAkamai](mcvid-library/mcvid-function-vars/mcvid-idsyncssluseakamai.md)
      + [isCoopSafe](mcvid-library/mcvid-function-vars/mcvid-coopsafe.md)
      + [loadTimeout](mcvid-library/mcvid-function-vars/mcvid-loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md)
      + [resetBeforeVersion](mcvid-library/mcvid-function-vars/mcvid-resetbeforeversion.md)
      + [sdidParamExpiry](mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md)
      + [secureCookie](mcvid-library/mcvid-function-vars/mcvid-securecookie.md)
      + [useCORSOnly](mcvid-library/mcvid-function-vars/mcvid-use-cors-only.md)
      + [whitelistParentDomain 및 whitelistIframeDomains](mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md)
   + 메서드{#methods}에서 사용할 수 있습니다 
      + [메서드](mcvid-library/mcvid-get-set/mcvid-get-set.md)
      + [appendSupplementalDataIDTo](mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md)
      + [appendVisitorIDsTo(도메인 간 추적)](mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md)
      + [callTimeOut 메서드](mcvid-library/mcvid-get-set/mcvid-timeout-functions.md)
      + [URL 또는 데이터 소스별 ID 동기화](mcvid-library/mcvid-get-set/mcvid-idsync.md)
      + [getInstance](mcvid-library/mcvid-get-set/mcvid-getinstance.md)
      + [getAnalyticsVisitorID](mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md)
      + [getCustomerIDs](mcvid-library/mcvid-get-set/mcvid-getcustomerids.md)
      + [setCustomerIDs](mcvid-library/mcvid-get-set/mcvid-setcustomerids.md)
      + [getMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-getmcvid.md)
      + [getLocationHint](mcvid-library/mcvid-get-set/mcvid-getlocationhint.md)
      + [getVisitorValues](mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-client-side-id.md)
      + [resetState](mcvid-library/mcvid-get-set/mcvid-resetstate.md)
+ 참조 {#reference}
   + [참조 개요](mcvid-reference/mcvid-reference.md)
   + Analytics 참조 {#analytics-reference}
      + [분석 참조 개요](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-reference.md)
      + [Analytics 및 Experience Cloud ID 설정](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md)
      + [Analytics ID 작업 순서](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-order-of-operations.md)
      + [Experience Cloud ID 서비스 마이그레이션 의사 결정 지점](mcvid-reference/mcvid-analytics-reference/mcvid-migration-decisions.md)
      + [Experience Cloud ID 서비스 마이그레이션 시나리오](mcvid-reference/mcvid-analytics-reference/mcvid-migration-scenarios.md)
      + [Analytics 및 Experience Cloud ID 요청](mcvid-reference/mcvid-analytics-reference/mcvid-legacy-analytics.md)
      + [데이터 수집 CNAME 및 도메인 간 추적](mcvid-reference/mcvid-analytics-reference/mcvid-cname.md)
      + [JavaScript와 혼합된 서버측 구현](mcvid-reference/mcvid-analytics-reference/mcvid-server-side.md)
      + [ID 서비스 유예 기간](mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md)
   + [컨텐츠 보안 정책 및 Experience Cloud ID 서비스](mcvid-reference/mcvid-csp.md)
   + [Experience Cloud ID 서비스의 COPPA 지원](mcvid-reference/mcvid-coppa.md)
   + [Experience Cloud ID 서비스의 CORS 지원](mcvid-reference/mcvid-cors.md)
   + [고객 ID 및 인증 상태](mcvid-reference/mcvid-authenticated-state.md)
   + [Safari ITP World의 ECID 라이브러리 메서드](mcvid-reference/ecid-library-methods.md)
   + [AMCV 쿠키 또는 ID 서비스에서 지역 및 사용자 ID 가져오기](mcvid-reference/mcvid-regions.md)
   + [Experience Cloud ID 서비스 요구 사항](mcvid-reference/mcvid-requirements.md)
   + [비디오 하트비트 및 Experience Cloud ID 서비스](mcvid-reference/mcvid-heartbeat.md)
   + [Data Workbench 및 Experience Cloud ID 서비스](mcvid-reference/mcvid-dwb.md)
+ FAQ {#faqs}
   + [FAQ 개요](mcvid-faq-intro/ecid-faq-intro.md)
   + [ID 서비스 FAQ](mcvid-faq-intro/ecid-faq.md)
   + [Analytics 및 ID 서비스 FAQ](mcvid-faq-intro/ecid-analytics-faq.md)
   + [기타 Experience Cloud 솔루션에 대한 FAQ](mcvid-faq-intro/ecid-other-faq.md)
+ ID 서비스 릴리스 노트 {#release-notes}
   + [2019 릴리스 노트](mcvid-release-notes/mcvid-release-notes.md)
   + [2018 릴리스 노트](mcvid-release-notes/mcvid-notes-2018.md)
   + [2017 릴리스 노트](mcvid-release-notes/mcvid-notes-2017.md)
   + [2016 릴리스 노트](mcvid-release-notes/mcvid-notes-2016.md)
   + [2015 릴리스 노트](mcvid-release-notes/mcvid-notes-2015.md)
