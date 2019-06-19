---
description: 옵트인 라이브러리 및 구성 설정 참조용 API입니다.
seo-description: 옵트인 라이브러리 및 구성 설정 참조용 API입니다.
seo-title: 옵트인 참조
title: 옵트인 참조
uuid: D 5023 A 34-2 F 3 E -464 D-B 21 F -579 B 2 F 416 CE 6
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671

---


# 옵트인 참조{#opt-in-reference}

옵트인 라이브러리 및 구성 설정 참조용 API입니다.

동의 설정은 옵트인 기능에 카테고리로 제공됩니다.

```
adobe.OptInCategories = { 
    "AAM": "aam", 
    "ANALYTICS": "aa", 
    "ECID": "ecid", 
    "TARGET": "target" 
}
```

## 옵트인 구성 매개 변수 {#section-d66018342baf401389f248bb381becbf}

이 섹션에서는 API를 사용하여 옵트인을 구성하는 방법을 설명합니다. 대부분의 구성 및 구현은 Launch 확장을 사용하여 수행할 수 있습니다.

옵트인 구성은 전역 개체를 인스턴스화하는 방문자 JavaScript `getInstance()` 함수에 `adobe` 제공됩니다. 다음은 옵트인 서비스와 관련된 방문자 JS 구성을 나열합니다.

**`doesOptInApply (boolean or function that evaluates to a boolean)`**:

false이면 방문자가 선택하지 않아도 됩니다. 카테고리 선택 여부에 상관없이 Experience Cloud에서 쿠키를 작성합니다. 이 구성은 옵트인을 전체적으로 활성화하거나 비활성화합니다.

**`preOptInApprovals (Object <adobe.OptInCategories enum: boolean>)`**

방문자가 구성 기본값이라고 하는 환경 설정을 아직 설정하지 않은 경우 승인 또는 거부할 카테고리를 정의합니다.

**`previousPermissions (Object<adobe.OptInCategories enum: boolean>)`**

방문자가 명시적으로 설정한 환경 설정입니다. 이 구성의 권한은 조직 기본값을 덮어씁니다(`previousPermissions`가 `preOptInApprovals`를 덮어씀).

**`isOptInStorageEnabled (boolean)`**

자사 쿠키(현재 고객의 도메인 내에 있음)에 권한을 저장하기 위해 옵트인 활성화

(선택 사항) **`optInCookiesDomain (string)`**

옵트인 쿠키에 사용할 자사 도메인 또는 하위 도메인(`isOptInStorageEnabled`가 true인 경우)

(선택 사항) **`optInStorageExpiry (integer)`**

기본 만료일 13개월을 재정의할 시간(초)

## 동의 매개 변수 변경 {#section-c3d85403ff0d4394bd775c39f3d001fc}

방문자는 사용자 사이트를 경험하는 동안 언제든지 환경 설정을 처음으로 지정하거나 CMP를 사용하여 환경 설정을 변경할 수 있습니다. Visitor JS가 초기 설정으로 초기화되면 다음 기능을 사용하여 방문자의 권한을 변경할 수 있습니다.

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

목록의 모든 카테고리에 대해 방문자를 승인하거나 옵트인하는 함수입니다. shouldWaitForComplete 매개 변수에 대한 자세한 내용은 [옵트인 워크플로우](../../implementation-guides/opt-in-service/getting-started.md#section-70cd243dec834c8ea096488640ae20a5)를 참조하십시오.

**`adobe.optIn.deny(categories, shouldWaitForComplete)`**

지정된 모든 카테고리에 대해 방문자를 거부하거나 옵트아웃하는 함수입니다.

**`adobe.optIn.approveAll()`**:

방문자가 만들 사이트에 대한 요청이 표현된 경우, 방문자 담요가 사용자 사이트에서 쿠키를 만들거나, 쿠키를 `approveAll()` 만들거나, 응답을 기준으로 쿠키를 만들 수 있는 권한을 `denyAll()`부여하거나 거부합니다.

**`adobe.optIn.denyAll()`**:

방문자가 만들 사이트에 대한 요청이 표현된 경우, 방문자 담요가 사용자 사이트에서 쿠키를 만들거나, 쿠키를 `approveAll()` 만들거나, 응답을 기준으로 쿠키를 `denyAll()`만들도록 허용하십시오.

## 옵트인 워크플로우 매개 변수 {#section-2c5adfa5459c4e72b96d2693123a53c2}

옵트인은 환경 설정이 한 번에 하나씩 제공되는 워크플로우처럼, 두 개 이상의 요청 주기를 통해 권한을 수집할 수 있는 워크플로우를 지원합니다. 다음 함수를 사용하여 * 설정에 *true`shouldWaitForComplete`를 제공하면 솔루션에서 한 개 솔루션 또는 전체 카테고리의 서브 세트에 대한 동의를 수집한 다음, 다음 솔루션 또는 카테고리의 서브 세트에 대한 동의를 수집할 수 있습니다. 첫 번째 호출부터 `adobe.optIn.status` , 속성은 흐름의 끝에서 호출될 때까지 `adobe.optIn.complete()` 대기합니다. 호출되면 상태는 *완료*로 설정됩니다.

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

목록의 모든 카테고리에 대해 방문자를 승인하거나 옵트인하는 함수입니다. 

`adobe.optIn.deny(categories, shouldWaitForComplete)`

지정된 모든 카테고리에 대해 방문자를 거부하거나 옵트아웃하는 함수입니다.

`adobe.optIn.complete()`

방문자의 환경 설정을 설정하기 위해 approve() 및 deny()에 대한 이전 호출 집계를 한 개의 요청으로 트리거하는 함수입니다. 아래 옵트인 변경을 구독할 때(`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe` 참조) 콜백은 이 함수를 호출할 때만 트리거됩니다.

## 방문자 옵트인 권한 매개 변수 {#section-7fe57279b5b44b4f8fe47e336df60155}

다음 권한 함수 중 하나를 사용하여 언제든지 방문자의 옵트인 권한을 수집합니다.

`adobe.optIn.permissions`

방문자가 부여하거나 거부한 모든 Experience Cloud 솔루션을 카테고리로 나열하는 개체입니다.

`adobe.optIn.isApproved(categories)`

모든 카테고리가 승인된 경우 이 함수는 true를 반환합니다.

`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe)`

권한 목록을 비동기적으로 검색합니다. 권한 부여/거부 프로세스가 완료되면 권한 목록과 함께 콜백이 호출됩니다. *에 대해 *true`shouldAutoSubscribe` 값을 제공하면 옵트인 변경 사항을 전달하기 위해 콜백이 등록됩니다. 다음은 `adobe.OptIn`의 속성입니다.

**`permissions`**

방문자 예에 의해 허용되거나 거부된 모든 Experience Cloud 솔루션을 카테고리로 나열하는 개체: `{ aa: true, ecid: false, aam: true... }`

**`status`**

* pending
* changed
* complete

**`doesOptInApply`**

초기화에 제공한 구성을 나타내는 True 또는 False

**`isPending`**

상태 값에 따라 True 또는 False. 옵트인은 권한을 명시적으로 승인하거나 거부하지 않은 방문자에 대해 이 속성을 true로 보고함

**`isComplete`**

상태 값에 따라 True 또는 False. 옵트인은 워크플로우 스타일 동의가 시작되었지만 완료되지 않은 경우, 이 속성에 대해 false를 보고할 수 있습니다.

## 옵트인 개체의 메서드 {#section-e0417801a82548d199d833010033e433}

**`approve(categories, shouldWaitForComplete)`**

**`categories`**: 승인할 하나 이상의 카테고리. 예를 들면 다음과 같습니다. `adobe.optIn.approve([adobe.OptInCategories.AAM, adobe.OptInCategories.ECID])`**`shouldWaitForComplete`**
: (선택 사항) 부울 매개 변수, 기본적으로 false 입니다. true를 전달하면 `adobe.optIn.complete()`()를 호출할 때까지 옵트인이 승인 프로세스를 완료하지 않습니다. 이 프로세스는 워크플로우와 유사합니다.

```
<codeblock>
  adobe.optIn.approve(adobe.OptInCategories.ANALYTICS, 
         true); adobe.optIn.approve(adobe.OptInCategories.ECID, true); 
         adobe.optIn.complete() 
</codeblock>
```

**`deny(categories, shouldWaitForComplete)`**

* 1개 이상의 카테고리를 전달하여 승인되었는지 확인합니다.
* 카테고리가 전달되지 않은 경우 사용 가능한 모든 카테고리가 선택됩니다.

**`isApproved(categories)`**

고객이 하나 이상의 카테고리를 승인하는지 확인합니다.

**`isPreApproved(categories)`**

고객이 하나 이상의 카테고리를 사전 승인했는지 확인합니다. (하나 이상의 카테고리가 `preOptInApprovals` 구성에서 전달된 경우).

**`fetchPermissions(callback, shouldAutoSubscribe)`**

권한 목록을 검색할 비동기 API입니다. 권한 부여/거부 프로세스가 완료되면 권한 목록과 함께 콜백이 호출됩니다. **`shouldAutoSubscribe`:** 도우미 유틸리티는 이 콜백을 향후 모든 이벤트에 자동으로 구독합니다. 옵트인에서 승인 또는 거부가 트리거될 때마다 콜백이 호출됨을 의미합니다. 이 방법을 사용하면 이벤트를 직접 구독하지 않아도 항상 업데이트됩니다.

**예**

`fetchPermissions`

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using `optIn.isApproved()` to check for permissions because it abstracts  
       out the details of knowing exactly how the `permissions` list looks like. 
 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

// OR: You can pass in `shouldAutoSubscribe` as true, your callback will be used to subscribe  
to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
} 
 
optIn.fetchPermissions(callback, true);
```

**`complete()`:**

>[!NOTE]
>
>매개 변수를 통과하거나 거부할 `shouldWaitForComplete` 경우에만 사용할 수 있습니다. 이 API는 승인 프로세스를 완료합니다. 예: `adobe.optIn.complete()`.

**`approveAll()`:**

기존의 모든 카테고리를 승인합니다.

**`denyAll()`**

기존의 모든 카테고리를 거부합니다.

## 옵트인 개체의 이벤트 {#section-06f25b33cab54bafb053183e937fb710}

**`complete`:**

승인 프로세스가 완료되면 이벤트 트리거를 완료합니다. 이 이벤트 트리거를 전달하지 않고 `shouldWaitForComplete``approveAll`승인/거부를 `denyAll`호출하는 경우 또는 `shouldWaitForComplete`를 전달하는 경우 `complete`가 호출되면 이 이벤트가 트리거됩니다.

**예**

```
<codeph>
  adobe.optIn.on("complete", callback); 
</codeph>
```
