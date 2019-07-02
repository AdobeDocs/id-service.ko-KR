---
description: 웹 사이트에서 옵트인을 활성화한 후에는 유효성 검사 메서드를 사용하여 브라우저의 개발자 도구로 서비스가 예상대로 작동하는지 테스트합니다.
seo-description: 웹 사이트에서 옵트인을 활성화한 후에는 유효성 검사 메서드를 사용하여 브라우저의 개발자 도구로 서비스가 예상대로 작동하는지 테스트합니다.
seo-title: 옵트인 서비스 확인
title: 옵트인 서비스 확인
uuid: 1743360a-d757-4e50-8697-0fa92b302cbc
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# 옵트인 서비스 확인{#validating-opt-in-service}

웹 사이트에서 옵트인을 활성화한 후에는 유효성 검사 메서드를 사용하여 브라우저의 개발자 도구로 서비스가 예상대로 작동하는지 테스트합니다.

## 사용 사례 1: 옵트인 활성화 {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

페이지를 로드하기 전에 캐시 및 쿠키를 지웁니다.

Chrome에서 웹 페이지를 마우스 오른쪽 버튼으로 클릭하고 검사를 선택합니다. 위의 스크린샷과 마찬가지로 *Network* 탭을 선택하여 브라우저에서 요청한 사항을 확인합니다.

위의 예에서는 ECID, AAM, Analytics 및 Target 페이지에 다음 Adobe JS 태그를 설치했습니다.

**옵트인이 예상대로 작동하는지 입증하는 방법:**

Adobe 서버에 대한 요청은 표시되지 않습니다.

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>방문자의 옵트아웃 상태를 검색하는 데 사용되는 읽기 전용 엔드포인트인 `http://dpm.demdex.net/optOutStatus`에 대한 호출이 표시될 수 있습니다. 이 엔드포인트로 인해 모든 타사 쿠키가 작성되지 않으며, 페이지에서 정보가 수집되지 않습니다.

Adobe 태그(AMCV_{{YOUR_ORG_ID}}, mbox, demdex, s_cc, s_sq, everest_g_v2, everest_session_v2)에 의해 작성된 쿠키는 표시되지 않습니다.

Chrome에서 *Application* 탭으로 이동하고 *Storage* 아래에 있는 *Cookies* 섹션을 확장한 다음 웹 사이트의 도메인 이름을 선택합니다.

![](assets/use_case_1_2.png)

## 사용 사례 2: 옵트인 및 저장 공간 활성화 {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

사용 사례 2의 유일한 차이점은 방문자가 제공한 옵트인 권한이 포함되는 *새 쿠키*인 **adobeujs-optin** 이 표시된다는 것입니다.

## 사용 사례 3: 옵트인 활성화 및 Adobe Analytics 사전 승인 {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Adobe Analytics는 승인을 받은 사전 옵트인이므로 다음과 같이 Network 탭에 추적 서버에 대한 요청이 표시됩니다.

![](assets/use_case_3_1.png)

그리고 Application 탭에는 Analytics 쿠키가 표시됩니다.

![](assets/use_case_3_2.png)

## 사용 사례 4: 옵트인 및 IAB 활성화 {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**페이지에서 현재 IAB 동의를 보는 방법:**

개발자 도구를 열고 *콘솔* 탭을 선택합니다. 다음 코드 조각을 붙여 넣고 Enter 키를 누릅니다.

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

다음은 목적 1, 2 및 5가 승인되고 Audience Manager 공급업체 ID가 승인되는 경우의 출력 예입니다.

* demdex.net/id: 이 호출이 있으면 ECID가 demdex.net에서 ID를 요청했음을 입증하는 것입니다.
* demdex.net/event: 이 호출이 있으면 DIL 데이터 수집 호출이 예상대로 작동하고 있음을 입증하는 것입니다.
* demdex.net/dest5.html: 이 호출이 있으면 ID 동기화가 트리거되고 있음을 입증하는 것입니다.

![](assets/use_case_4_1.png)

다음 중 하나가 올바르지 않으면 Adobe 서버에 대한 요청이 표시되지 않으며 Adobe 쿠키가 없는 것입니다.

* 목적 1, 2 또는 5가 승인되지 않습니다.
* Audience Manager 공급업체 ID가 승인되지 않습니다.