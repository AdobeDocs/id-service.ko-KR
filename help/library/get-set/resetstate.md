---
description: '이 기능은 주로 A4T 고객이 단일 페이지 사이트/화면 또는 앱에서 ID 작업 관련 문제를 해결할 수 있도록 설계되었습니다. '
keywords: ID 서비스
seo-description: '이 기능은 주로 A4T 고객이 단일 페이지 사이트/화면 또는 앱에서 ID 작업 관련 문제를 해결할 수 있도록 설계되었습니다. '
seo-title: resetState
title: resetState
uuid: ED 7 BE 76 D-A 7 EE -4 E 51-B 26 C -456 FF 85 FD 096
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# resetState{#resetstate}

이 기능은 주로 A4T 고객이 단일 페이지 사이트/화면 또는 앱에서 ID 작업 관련 문제를 해결할 수 있도록 설계되었습니다. 

## 사용 사례 {#section-840b88a5cdb042488b340cad5d7b22a5}

ID 서비스를 사용하는 A 4 T 고객은 필요할 때 `visitor.resetState()` 이 기능을 사용할 수 있습니다.

* 리디렉션을 통해 한 페이지 또는 화면에서 다른 페이지 또는 화면으로 보조 데이터 ID(SDID) 또는 다른 ID를 전달해야 합니다. 일반적으로 ID 서비스에서는 이 함수가 없는 경우 이 ID를 전달하지 않습니다.
* Ajax 호출을 통해 페이지 또는 앱의 특정 섹션만 업데이트하고 해당 작업을 추적하려면 코드를 사용하십시오. 예를 들어 개체를 클릭하면 특정 섹션만 로드되거나 변경되는 페이지가 있다고 가정합니다. 이 경우 페이지가 다시 로드되지 않으면 ID 서비스에서 다른 ID를 요청할 수 없습니다. 하지만 with `visitor.resetState()`, you can request a new ID under these conditions.

아래 코드 샘플을 참조하십시오.

## 구문 {#section-9e63503e178f4be28ac850abf44d6d91}

**구문:**` visitor.resetState( *`state`*);`

## 코드 샘플 {#section-d75b211bb4ea473887eb284de2ad838b}

ID 서비스 구현은 이 기능을 사용하는 방법에 영향을 줍니다. 예제에 대해서는 아래 표를 참조하십시오.

**서버측 구현**

서버측 구현은 혼합된 서버 및 클라이언트측 구현, ID 서비스 등을 사용하는 4 T 고객을 [!DNL Target][!DNL Analytics]위한 것입니다. 이 방법으로 ID 서비스를 설정한 경우 페이지에 추가해야 `visitor.resetState()` 합니다. ID 서비스를 호출하면 새 ID 및 서버 상태를 자동으로 반환합니다.

**비표준 구현 (** ID 포함)

[비표준 구현](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113)을 사용하여 ID 서비스를 설정한 경우 `visitor.resetState()`()와 함께 전달할 SDID(또는 다른 ID)를 보유할 변수 개체를 구성해야 합니다. 아래 표시된 대로 여기에 [조직 ID](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26)와 전달할 ID가 포함됩니다. 코드는 다음 예와 비슷하게 보일 수 있습니다.

```js
//Instantiate server state variable 
var serverState = { 
     "Insert Experience Cloud organization ID here": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**비표준 구현 (** ID 전달 없음)

이 경우 새 ID `visitor.resetState()` 를 생성하는 데 사용할 수 있습니다. 이 방법은 사용자가 페이지를 새로 고치지 않고 새 화면으로 이동하고 새 ID가 필요한 경우 단일 페이지 앱에서 유용할 수 있습니다.

```js
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
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

DTM(**다이내믹 태그 관리자)**

현재 `visitor.resetState()`()에 대한 DTM 구성 경로가 없습니다.
