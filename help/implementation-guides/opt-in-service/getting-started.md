---
description: Experience Cloud 솔루션(옵트인에서 카테고리라고도 함)에 사용되는 단일 참조 지점으로 옵트인 서비스를 구현하여 방문자의 디바이스에 쿠키를 작성할지 여부를 결정합니다.
title: 옵트인 서비스 설정
exl-id: 6e8a6531-9924-4523-a842-cb4614a7a7a0
source-git-commit: 070390ec0534c9066d717fe52ff572f34c110137
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 100%

---

# 옵트인 서비스 설정{#setting-up-opt-in-service}

Experience Cloud 솔루션(옵트인에서 카테고리라고도 함)에 사용되는 단일 참조 지점으로 옵트인 서비스를 구현하여 방문자의 디바이스에 쿠키를 작성할지 여부를 결정합니다.

옵트인 서비스는 ECID(Experience Cloud ID)와 함께 번들로 제공되는 JavaScript 라이브러리이며, 전역 `adobe` 오브젝트에서 `adobe.optIn` 오브젝트로 Visitor JS에 있습니다. 설치된 옵트인 서비스를 사용하면 방문자가 Adobe 솔루션에 한꺼번에 옵트인할 수 있는지 여부 또는 각 솔루션의 권한을 얻기 위해 솔루션을 순서대로 표시할지 여부를 지정할 수 있습니다. 옵트인 서비스 동의 관리 기능을 사용하여 특정 개인정보 보호 요구 사항에 맞게 다양한 구성을 구현할 수 있습니다.

옵트인 서비스를 사용하면 방문자가 Adobe 솔루션에 한꺼번에 옵트인할 수 있는지 여부 또는 각 솔루션의 권한을 얻기 위해 솔루션을 순서대로 표시할지 여부를 지정할 수 있습니다. 고객이 승인 프로세스를 완료하고 기록하면 모든 Adobe 솔루션에서 CMP 방문자 승인을 검색하여 관련된 동의 호출에 응답할 수 있습니다.

## 사전 요구 사항 {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID 버전 4.0.

   최신 ECID 릴리스를 [다운로드](https://github.com/Adobe-Marketing-Cloud/id-service/releases)하십시오.

1. 지원 라이브러리:

   * ECID 4.0 이상
   * AppMeasurement 2.11 이상
   * DIL 9.0
   * AT.js 버전 1.7.0
   * AT.js Launch 확장 버전 9.0
   * Analytics의 경우, 확장 1.6이 있는 App Measurement 2.11
   * Target의 경우, 확장 0.9.1

1. 옵트인과 함께 사용할 동의 관리 프레임워크에 숙달되도록 하고 추가 전제 조건을 파악하십시오.

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. 귀사의 개인정보 보호 요구 사항은 GDPR 준수를 유지하기 위해 선택한 방법에 따라 특정됩니다. 귀사의 개인정보 보호 팀이 동의 전 상태에서 사용할 수 있는 라이브러리를 알고 있어야 합니다.

[Adobe Experience Platform의 태그](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)를 사용하는 경우 [옵트인 확장 기능](../../implementation-guides/opt-in-service/launch.md)을 활용하여 옵트인 서비스를 구성하십시오.

## 옵트인 카테고리 {#section-9ab0492ab4414f0ca16dc08d3a905f47}

방문자의 옵트인 환경 설정은 각 솔루션이 카테고리로 표시되는 Adobe Experience Cloud 솔루션을 기준으로 합니다. 카테고리는 `adobe.OptInCategories` 오브젝트에서 제공하며, 예를 들어 여기서는 ECID 구성 요소를 `adobe.OptInCategories`. `ECID` 구문을 사용하는 키-값 쌍으로 전달됩니다. 다음은 `adobe.OptInCategories`에 대한 정의입니다.

옵트인 설정은 카테고리별로 유지 관리되며, 각 Experience Cloud 솔루션은 카테고리로 나타냅니다.

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

옵트인 서비스를 사용하면 사이트에서 사용되는 각 Adobe 솔루션에 대한 방문자의 권한 환경 설정을 지정할 수 있습니다. 이 오브젝트에는 방문자 설정을 승인된 카테고리별로 저장하고 순차적 흐름을 지원하는 라이브러리가 포함되어 있습니다. 여기서 승인 프로세스는 한 번에 하나씩 각 카테고리에 대한 &quot;확인&quot; 또는 &quot;거부&quot; 환경 설정을 수신합니다. 전체 또는 개별 솔루션으로 옵트인할 솔루션/카테고리를 설정할 수 있습니다.
모든 Adobe 솔루션의 클라이언트측 라이브러리는 옵트인 서비스에 종속되며, 솔루션에 권한이 부여되지 않은 경우 쿠키를 생성하지 않습니다. 옵트인은 현재 방문자에 대한 동의 설정을 제공하고 업데이트하는 다양한 방법을 지원합니다. 이 섹션에서는 옵트인 서비스 환경 설정을 지정하는 예를 제공합니다. 함수 및 매개변수의 전체 목록은 [옵트인 API 참조](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867)를 참조하십시오.

옵트인 서비스 구성은 전역 `adobe` 오브젝트를 인스턴스화하는 Visitor JS `getInstance()` 함수에 제공됩니다. 다음은 옵트인 서비스에 대한 Visitor JS [구성 설정](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) 목록입니다.

**전역 `Visitor` 오브젝트의 초기화에서 옵트인 구성 예제**

```
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
var preOptInApprovalsConfig = {}; 
preOptInApprovals[adobe.OptInCategories.ANALYTICS] = true; 
  
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
// If you are storing the OptIn permissions on your side (in a cookie you manage or in a CMP), 
// you have to provide those permissions through the previousPermissions config. 
// previousPermissions will overwrite preOptInApprovals. 
var previousPermissionsConfig = {}; 
previousPermissionsConfig[adobe.OptInCategories.AAM] = true; 
previousPermissionsConfig[adobe.OptInCategories.ANALYTICS] = false; 
  
Visitor.getInstance("YOUR_ORG_ID", { 
    "doesOptInApply": true, // NOTE: This can be a function that evaluates to true or false. 
    "preOptInApprovals": preOptInApprovalsConfig, 
    "previousPermissions": previousPermissionsConfig, 
    "isOptInStorageEnabled": true 
});
```

**동의 변경 처리**

방문자는 귀하의 사이트에서 경험하는 동안 언제든지 처음으로 기본 설정을 지정하거나 CMP를 사용하여 기본 설정을 변경할 수 있습니다. 방문자 JS가 초기 설정으로 초기화되면 방문자의 권한을 변경할 수 있습니다. 동의 함수 관리 목록에 대해서는 [동의 변경](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc)을 참조하십시오.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## 옵트인 워크플로 {#section-70cd243dec834c8ea096488640ae20a5}

옵트인 서비스는 두 개 이상의 요청 주기를 통해 권한을 수집할 수 있고 환경 설정이 한 번에 하나씩 제공되는 워크플로를 지원합니다. 다음 함수를 사용하여 `shouldWaitForComplete`에 대해 *true*&#x200B;를 제공하면 솔루션에서 한 개 카테고리 또는 전체 카테고리의 서브 세트에 대한 동의를 수집한 후 다음 카테고리 또는 카테고리의 서브 세트에 대한 동의를 수집할 수 있습니다. `adobe.optIn.status` 속성은 첫 번째 호출부터 `adobe.optIn.complete()`가 흐름 끝에서 호출될 때까지 *보류*&#x200B;됩니다. 호출되면 상태는 *complete*&#x200B;로 설정됩니다.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

[워크플로 구성 설정](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2)을 참조하십시오.

## 방문자의 옵트인 권한 검사 {#section-f136a9024e054d84881e6667fb7c94eb}

방문자가 자신의 권한을 변경할 때 옵트인 서비스의 변경 사항과 동의 저장 내용을 동기화하기 위해서는 결과 권한에 대한 통찰력이 필요합니다. [권한 함수](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155)를 사용하여 방문자의 기본 설정을 검사하십시오. 예:

**fetchPermissions 샘플**

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using optIn.isApproved() to check for permissions because it abstracts out the details of knowing exactly how the permissions list looks like. 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

OR: You can pass in shouldAutoSubscribe as true, your callback will be used to subscribe to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
}

optIn.fetchPermissions(callback, true);
```

이와 관련된 자세한 내용 및 이 설명서에 언급된 함수, 속성 또는 구성에 대해서는 [API 설명서](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867)를 참조하십시오.

## 방문자 환경 설정 저장 {#section-ef2884ae67e34879bf7c7c3372706c9f}

옵트인 서비스는 개발 환경 또는 CRM을 사용할 수 없는 환경에 맞게 동의 환경 설정을 저장하는 옵션을 제공합니다. 구성 속성 `isOptInStorageEnabled`를 *true*&#x200B;로 지정하면 옵트인 서비스를 트리거하여 도메인 내에 방문자의 시스템에 대한 쿠키를 생성합니다.

`adobe.optIn` 오브젝트는 상태를 저장하지 않으며, 저장 메커니즘을 제공하지 않습니다. 사용자 정의 데이터를 저장할 수 있는 경우 기존 동의 관리 플랫폼(CMP)에서 Adobe 동의 설정을 관리하기 위한 옵션입니다. 또는 방문자 브라우저의 쿠키에 방문자 기본 설정을 저장할 수 있습니다. 사용자의 환경 설정을 옵트인 서비스에 제공하는 두 가지 옵션이 있습니다.

* 사용자 동의 지속성 솔루션이 방문자의 브라우저에서 CMP이든, 쿠키이든 간에 방문자 환경 설정을 적시에 검색할 수 있도록 허용하는 경우, 방문자 초기화 중에 그러한 환경 설정을 옵트인 서비스에 제공할 수 있습니다.
* 그러나 검색이 오래 걸릴 수 있는 경우 또는 비동기 프로세스로 최상의 서비스를 제공할 수 있는 경우에는 그러한 설정이 성공적으로 로드되면 서비스의 `approve()` 함수를 사용하여 설정을 제공할 수 있습니다.
