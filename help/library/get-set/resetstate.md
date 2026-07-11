---
description: 이 기능은 주로 A4T 고객이 단일 페이지 사이트/화면 또는 앱에서 ID 작업 관련 문제를 해결할 수 있도록 설계되었습니다.
keywords: 방문자 ID 서비스
title: resetState
exl-id: 8e8cb299-bb89-4bc1-8841-3091ce0cbd81
TQID: https://experienceleague.adobe.com/ud8yTufRC6V5T58oh20G65MYNTCZvMlK5FdHVrrZFpU
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 377
ht-degree: 54%

---

# resetState{#resetstate}

이 기능은 주로 A4T 고객이 단일 페이지 사이트/화면 또는 앱에서 ID 작업 관련 문제를 해결할 수 있도록 설계되었습니다.

## 사용 사례 {#section-840b88a5cdb042488b340cad5d7b22a5}

방문자 ID 서비스를 사용하는 A4T 고객은 다음을 수행해야 하는 경우 `visitor.resetState()` 함수를 사용할 수 있습니다.

* 리디렉션을 통해 한 페이지 또는 화면에서 다른 페이지 또는 화면으로 SDID(Supplemental Data ID) 또는 기타 ID를 전달합니다. 일반적으로 방문자 ID 서비스는 이 함수가 없으면 이 ID를 전달하지 않습니다.
* Ajax 호출을 통해 페이지 또는 앱의 특정 섹션만 업데이트하는 코드를 사용합니다. 그리고 해당 작업을 추적하고 싶습니다. 예를 들어 개체를 클릭하면 특별 섹션만 로드하거나 변경하는 페이지가 있다고 가정해 보겠습니다. 이 경우 페이지가 다시 로드되지 않으면 방문자 ID 서비스는 다른 ID를 요청할 수 없습니다. 그러나 `visitor.resetState()`를 사용하면 이러한 조건에서 새 ID를 요청할 수 있습니다.

아래 코드 샘플을 참조하십시오.

## 구문 {#section-9e63503e178f4be28ac850abf44d6d91}

**구문:** `visitor.resetState( *`상태`*);`

## 코드 샘플 {#section-d75b211bb4ea473887eb284de2ad838b}

방문자 ID 서비스 구현은 이 함수를 사용하는 방법에 영향을 줍니다. 예시는 아래 테이블을 참조하십시오.

**서버측 구현**

서버측 구현은 Target, Analytics 및 방문자 ID 서비스에 대한 서버측과 클라이언트측 구현이 혼합된 A4T 고객을 위한 것입니다. 이 메서드를 사용하여 방문자 ID 서비스를 설정한 경우 `visitor.resetState()`을(를) 페이지에 추가하면 됩니다. 방문자 ID 서비스를 호출하면 새 ID와 서버 상태가 자동으로 반환됩니다.

**비표준 구현** (ID가 있음)

[비표준 구현](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113)을 사용하여 방문자 ID 서비스를 설정한 경우 `visitor.resetState()`과(와) 함께 전달할 SDID(또는 다른 ID)를 보유할 변수 개체를 구성해야 합니다. 아래 표시된 대로 여기에 [IMS 조직 ID](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26)와 전달할 ID가 포함됩니다. 코드는 다음 예와 비슷하게 보일 수 있습니다.

```js
//Instantiate server state variable 
var serverState = { 
     "INSERT-IMS-ORG-ID-HERE": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**비표준 구현** (ID를 전달하지 않음)

이 경우 `visitor.resetState()`를 사용하여 새 ID를 생성할 수 있습니다. 사용자가 페이지를 새로 고치지 않고 새 화면으로 이동하며 새 ID가 필요할 때 단일 페이지 앱에서 유용할 수 있는 방법입니다.

```js
 
//Instantiate Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE", { 
     ... 
}); 
 
//Request a supplemental Data ID for consumer1 and consumer2: 
var sdid1 = visitor.getSupplementalDataID("consumer1"); // sdid1: 1234 
var sdid2 = visitor.getSupplementalDataID("consumer2"); // sdid2: 1234 
 
//User navigates to a new screen in a single-page app, without refreshing the page. 
//To reset the Supplemental Data ID internal, call resetState without passing any parameters. 
//This way we will not be recycling the `1234` ID anymore. Instead Visitor will generate a new supplemental Data ID going forward. 
visitor.resetState(); 
 
//Request a supplemental Data ID for consumer3 and consumer4: 
var sdid1 = visitor.getSupplementalDataID("consumer3"); // sdid1: 5678 
 
var sdid2 = visitor.getSupplementalDataID("consumer4"); // sdid2: 5678
```

