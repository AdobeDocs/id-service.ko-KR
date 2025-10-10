---
description: 웹 사이트에서 옵트인을 활성화한 후에는 유효성 검사 메서드를 사용하여 브라우저의 개발자 도구로 서비스가 예상대로 작동하는지 테스트합니다.
title: 옵트인 서비스 확인
exl-id: f0bcb32a-ccad-40a4-b031-2584e4136ace
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 91%

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

페이지를 로드하기 전에 캐시와 쿠키를 지우십시오.

Chrome에서 웹 페이지를 마우스 오른쪽 버튼으로 클릭하고 검사를 선택합니다. 위의 스크린샷에서와 같이 *네트워크* 탭을 선택하여 브라우저로부터의 요청을 확인합니다.

위의 예에서는 페이지에 ECID, AAM, Analytics 및 Target과 같은 Adobe JS 태그가 설치되어 있습니다.

**옵트인이 예상대로 작동하는지 입증하는 방법:**

Adobe 서버로의 요청이 표시되지 않아야 합니다.

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>방문자의 옵트아웃 상태를 검색하는 데 사용되는 읽기 전용 엔드포인트인 `http://dpm.demdex.net/optOutStatus`에 대한 호출이 표시될 수 있습니다. 이 끝점으로 인해 서드파티 쿠키가 생성되지 않으며 페이지로부터 정보를 수집하지 않습니다.

Adobe 태그에서 만든 쿠키(`AMCV_{{YOUR_ORG_ID}}`, `mbox`, `demdex`, `s_cc`, `s_sq`, `everest_g_v2`, `everest_session_v2`)가 표시되지 않습니다.

Chrome에서 *애플리케이션* 탭으로 이동하여 *스토리지* 아래의 *쿠키* 섹션을 확장한 다음 웹 사이트의 도메인 이름을 선택합니다.

![](assets/use_case_1_2.png)

## 사용 사례 2: 옵트인 및 스토리지 활성화 {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

사용 사례 2의 유일한 차이점은 방문자가 제공한 옵트인 권한이 포함된 *새 쿠키*(**adobeujs-optin**&#x200B;가 표시된다는 것입니다.

## 사용 사례 3: 옵트인 활성화 및 Adobe Analytics 사전 승인 {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Adobe Analytics는 사전 옵트인 승인을 받았으므로 네트워크 탭에 추적 서버에 대한 요청이 표시됩니다.

![](assets/use_case_3_1.png)

그리고 애플리케이션 탭에 Analytics 쿠키가 표시됩니다.

![](assets/use_case_3_2.png)

## 사용 사례 4: 옵트인 및 IAB 활성화 {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**페이지에서 현재 IAB 동의를 보는 방법:**

개발자 도구를 열고 *콘솔* 탭을 선택합니다. 다음 코드 조각을 붙여넣고 Enter를 누르십시오.

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

다음은 용도 1, 2 및 5가 승인되고 Audience Manager 공급업체 ID가 승인된 경우의 출력 예입니다.

* demdex.net/id: 이 호출의 존재는 ECID가 demdex.net에서 ID를 요청했음을 증명합니다.
* demdex.net/event: 이 호출의 존재는 DIL 데이터 수집 호출이 예상대로 작동하고 있음을 증명합니다.
* demdex.net/dest5.html: 이 호출의 존재는 ID 동기화가 트리거되고 있음을 증명합니다.

![](assets/use_case_4_1.png)

다음 중 하나가 유효하지 않으면 Adobe 서버에 대한 요청과 Adobe 쿠키가 표시되지 않습니다.

* 용도 1, 2 또는 5가 승인되지 않았습니다.
* Audience Manager 공급업체 ID가 승인되지 않았습니다.
