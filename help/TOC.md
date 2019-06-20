---
cloud: platform-cloud
product: ID 서비스
audience: 최종 사용자
user-guide-title: Experience Cloud ID 서비스 도움말
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Experience Cloud ID Service Help {#using}

+ [ID 서비스 도움말](home.md)
+ 개요 {#intro}
   + [개요](introduction/overview.md)
   + [ID 서비스 정보](introduction/about-id-service.md)
   + [쿠키 및 ID 서비스](introduction/cookies.md)
   + [ID 서비스가 ID를 요청 및 설정하는 방식](introduction/id-request.md)
   + [동기화 및 일치 비율 이해](introduction/match-rates.md)
+ Implementation guides {#implementation-guides}
   + [구현 안내서](implementation-guides/implementation-guides.md)
   + [구현 방법](implementation-guides/implementation-methods.md)
   + [Launch를 사용한 구현](implementation-guides/ecid-implement-with-launch.md)
   + [DTM을 사용한 구현](implementation-guides/standard.md)을 참조하십시오
   + [Analytics에 대해 구현](implementation-guides/setup-analytics.md)
   + [Target 용으로 구현](implementation-guides/setup-target.md)
   + [Analytics 및 Audience Manager에 대해 구현](implementation-guides/setup-aam-analytics.md)
   + [Analytics, Audience Manager 및 Target 용으로 구현](implementation-guides/setup-aam-analytics-target.md)
   + [Target의 서버측 구현 및 A4T에 ID 서비스 사용](implementation-guides/ecid-a4t-target.md)
   + [ID 서비스와 직접 통합](implementation-guides/direct-integration.md)
   + [직접 통합 사용 사례](implementation-guides/direct-integration-examples.md)
   + [ID 서비스 테스트 및 확인](implementation-guides/test-verify.md)
   + Opt-in Documentation {#opt-in-service}
      + [옵트인 서비스 개요](implementation-guides/opt-in-service/optin-overview.md)
      + [옵트인 서비스 설정](implementation-guides/opt-in-service/getting-started.md)
      + [옵트인 서비스 유효성 확인](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Launch로 옵트인 구성](implementation-guides/opt-in-service/launch.md)
      + [DTM으로 옵트인 구성](implementation-guides/opt-in-service/optin-dtm.md)
      + [옵트인 사용 사례](implementation-guides/opt-in-service/use-cases.md)
      + [옵트인 참조](implementation-guides/opt-in-service/api.md)
      + [(베타) IAB Framework와 함께 옵트인 서비스 사용](implementation-guides/opt-in-service/iab.md)
+ ID 서비스 API {#id-service-api}
   + [ID 서비스 API 개요](library/library.md)
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
      + [isCoopSafe](library/function-vars/coopsafe.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
      + [secureCookie](library/function-vars/securecookie.md)
      + [useCORSOnly](library/function-vars/use-cors-only.md)
      + [whitelistParentDomain 및 whitelistIframeDomains](library/function-vars/whitelistdomain.md)
   + 메서드{#methods}에서 사용할 수 있습니다 
      + [메서드](library/get-set/get-set.md)
      + [appendSupplementalDataIDTo](library/get-set/appendsupplementaldataidto.md)
      + [appendVisitorIDsTo(도메인 간 추적)](library/get-set/appendvisitorid.md)
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
   + Analytics 참조 {#analytics-reference}
      + [분석 참조 개요](reference/analytics-reference/analytics-reference.md)
      + [Analytics 및 Experience Cloud ID 설정](reference/analytics-reference/analytics-ids.md)
      + [Analytics ID 작업 순서](reference/analytics-reference/analytics-order-of-operations.md)
      + [ID 서비스 마이그레이션 의사 결정 지점](reference/analytics-reference/migration-decisions.md)
      + [ID 서비스 마이그레이션 시나리오](reference/analytics-reference/migration-scenarios.md)
      + [분석 및 ID 요청](reference/analytics-reference/legacy-analytics.md)
      + [데이터 수집 CNAME 및 도메인 간 추적](reference/analytics-reference/cname.md)
      + [JavaScript와 혼합된 서버측 구현](reference/analytics-reference/server-side.md)
      + [ID 서비스 유예 기간](reference/analytics-reference/grace-period.md)
   + [컨텐츠 보안 정책 및 ID 서비스](reference/csp.md)
   + [ID 서비스의 COPPA 지원](reference/coppa.md)
   + [ID 서비스에서 CORS 지원](reference/cors.md)
   + [고객 ID 및 인증 상태](reference/authenticated-state.md)
   + [Safari ITP World의 ECID 라이브러리 메서드](reference/ecid-library-methods.md)
   + [AMCV 쿠키 또는 ID 서비스에서 지역 및 사용자 ID 가져오기](reference/regions.md)
   + [ID 서비스 요구 사항](reference/requirements.md)
   + [비디오 하트비트 및 ID 서비스](reference/heartbeat.md)
   + [데이터 워크벤치 및 ID 서비스](reference/dwb.md)
+ FAQ {#faqs}
   + [FAQ 개요](faq-intro/faq-intro.md)
   + [ID 서비스 FAQ](faq-intro/faq.md)
   + [Analytics 및 ID 서비스 FAQ](faq-intro/analytics-faq.md)
   + [기타 Experience Cloud 솔루션에 대한 FAQ](faq-intro/other-faq.md)
+ Release notes for ID Service {#release-notes}
   + [2019 릴리스 노트](release-notes/release-notes.md)
   + [2018 릴리스 노트](release-notes/notes-2018.md)
   + [2017 릴리스 노트](release-notes/notes-2017.md)
   + [2016 릴리스 노트](release-notes/notes-2016.md)
   + [2015 릴리스 노트](release-notes/notes-2015.md)
