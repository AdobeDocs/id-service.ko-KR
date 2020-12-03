---
description: Experience Cloud 방문자 ID와 함께 추가 고객 ID 및 인증 상태와 각 방문자를 연결할 수 있습니다.
keywords: ID Service
seo-description: Experience Cloud 방문자 ID와 함께 추가 고객 ID 및 인증 상태와 각 방문자를 연결할 수 있습니다.
seo-title: 고객 ID 및 인증 상태
title: 고객 ID 및 인증 상태
uuid: 643df363-224a-463e-a332-be59926b47e7
translation-type: tm+mt
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 100%

---


# 고객 ID 및 인증 상태 {#customer-ids-and-authentication-states}

Experience Cloud 방문자 ID와 함께 추가 고객 ID 및 인증 상태와 각 방문자를 연결할 수 있습니다.

## 인증 상태 {#section-68ad4065dfaa437d9070832d6e2bf85c}

`setCustomerIDs` 메서드는 동일한 방문자의 여러 고객 ID를 수락합니다. 따라서 여러 다른 장치에서 개별 사용자를 식별하고 타깃팅하는 데 도움이 됩니다. 예를 들어 이러한 ID를 [고객 속성](https://docs.adobe.com/content/help/ko-KR/core-services/interface/customer-attributes/attributes.html)으로 [!DNL Experience Cloud]에 업로드하고 다른 솔루션에 있는 이 데이터에 액세스할 수 있습니다.

>[!IMPORTANT]
>
>`setCustomerIDs` (고객 ID 동기화)는 고객 특성 및 핵심 서비스 기능에 필요합니다. 고객 ID 동기화는 [!DNL Analytics]의 선택적 식별 방법입니다. [!DNL Target]의 경우 고객 특성이 작동하려면 `Visitor.AuthState.AUTHENTICATED`가 필요합니다. 예제에 대해서는 [핵심 서비스 - 솔루션을 사용하도록 설정하는 방법](https://docs.adobe.com/content/help/ko-KR/core-services/interface/about-core-services/core-services.html)을 참조하십시오.

Experience Cloud Identity 서비스 v1.5 이상부터 `setCustomerIDs`에 선택적 `AuthState` 개체가 있습니다. `AuthState`는 인증 상태(예: 로그인함 또는 로그아웃함)에 따라 방문자를 식별합니다. 표에 나열된 상태 값으로 인증 상태를 설정합니다. 인증 상태가 정수로 반환됩니다.

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 인증 상태 </th> 
   <th colname="col2" class="entry"> 상태 정수 </th> 
   <th colname="col3" class="entry"> 사용자 상태 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 0 </span> </p> </td> 
   <td colname="col3"> <p>알 수 없음 또는 인증되지 않음. </p> <p> <span class="codeph">AuthState</span>가 방문자 ID와 함께 사용되지 않거나 각 페이지 또는 앱 컨텍스트에서 명시적으로 설정되지 않으면 기본적으로 알 수 없음이 적용됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 1 </span> </p> </td> 
   <td colname="col3"> <p>특정 인스턴스, 페이지 또는 앱에 대해 인증됨 </p> <p> <p>주의: 제대로 작동하기 위해서는 <span class="keyword">Target</span>의 고객 속성에 이 상태가 필요합니다. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">2</span> </p> </td> 
   <td colname="col3"> <p>로그아웃됨. </p> </td> 
  </tr> 
 </tbody> 
</table>

## 인증 상태에 대한 사용 사례 {#section-fe9560cc490943b29dac2c4fb6efd72c}

사용자가 웹 속성에서 수행하는 작업과 인증 여부에 따라 사용자에게 인증 상태를 할당할 수 있습니다. 아래 표에서 몇 가지 예를 참조하십시오.

<table id="table_3769E79304014C4F87094B87A8ACE4E0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 인증 상태 </th> 
   <th colname="col2" class="entry"> 사용 사례 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p>이 상태는 다음과 같은 시나리오에 사용할 수 있습니다. </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">이메일을 읽기(이 작업은 독자가 의도한 수신자이지만 이메일을 전송할 수도 있음을 의미함) </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">이메일에서 랜딩 페이지로 클릭스루 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>사용자는 현재 웹 사이트 또는 앱에서 활성 세션으로 인증됩니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>사용자가 인증되었지만 현재 로그아웃되었습니다. 사용자가 인증된 상태에서 연결을 끊고자 했습니다. 사용자가 더 이상 인증된 것으로 취급되고 싶어하지 않습니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

## 고객 ID 및 인증 상태 설정 {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

고객 ID는 다음 예제에 표시된 것처럼 ID 및 인증된 상태 조합이 포함될 수 있습니다.

>[!IMPORTANT]
>
>* ID는 대소문자를 구분합니다.
>* ID에 대해 인코딩이 해제된 값만 사용하십시오.
>* 고객 ID 및 인증 상태는 방문자 ID 쿠키에 저장되지 않습니다. 모든 페이지 또는 애플리케이션 컨텍스트에 대해 설정되어야 합니다.
>* 고객 ID에는 PII(개인 식별 정보)를 포함시켜서는 안 됩니다. PII를 사용하여 방문자(예를 들어 이메일 주소)를 식별하는 경우 대신 이 정보의 해시 버전 또는 암호화 버전을 저장하는 것이 좋습니다. ECID 라이브러리는 사용자 ID 해시를 지원합니다. [setCustomerIDs에 대한 SHA256 해시 지원](/help/reference/hashing-support.md)을 참조하십시오.


```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
/* 
Multiple IDs with only the first ID explicitly assigned an authentication state. 
The second ID is not explicitly assigned an authentication state and is implicitly 
assigned Visitor.AuthState.Unknown by default. 
*/ 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
// Multiple IDs with different authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## 고객 ID 및 인증 상태 반환 {#section-71a610546188478fa9a3185a01d6e83b}

`getCustomerIDs`를 사용하여 고객 ID 및 관련 인증 상태를 반환합니다. 이 메서드는 방문자의 인증 상태를 정수로 반환합니다.

**구문**

`getCustomerIDs`는 다음 구문을 사용하여 데이터를 반환합니다.

```js
{ 
    [customerIDType1]:{ 
        "id":[customerID1], 
        "authState":[authState1] 
    }, 
    [customerIDType2]:{ 
        "id":[customerID2], 
        "authState":[authState2] 
    } 
    ... 
}
```

**예**

반환된 고객 ID 및 인증 상태 데이터는 다음 예와 유사해야 합니다.

```js
Object customerIDs = visitor.getCustomerIDs(); 
  
// No setCustomerIDs call on this instance 
{} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456"}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":0 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456","authState":Visitor.AuthState.AUTHENTICATED}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":1 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT}} 
{ 
    "userid":{ 
        "authState":2 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"dpuuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## SDK 지원 {#section-861c6b3b1ba645dda133dccb22ec7bb0}

[!DNL Experience Cloud] ID 서비스는 Android 및 iOS SDK 코드에서 고객 ID와 인증 상태를 지원합니다. 다음 코드 라이브러리를 참조하십시오.

* [Android SDK 메서드](https://docs.adobe.com/content/help/ko-KR/mobile-services/android/overview.html)
* [iOS SDK 메서드](https://docs.adobe.com/content/help/ko-KR/mobile-services/ios/overview.html)

## Analytics 및 Audience Manager 고객을 위한 알림 {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

선언된 ID를 [!DNL Audience Manager]에 전달하는 경우 `userid` 개체가 데이터 소스와 연결된 통합 코드와 일치해야 합니다. 자세한 내용은 [병합 규칙 코드 구성](https://docs.adobe.com/help/ko-KR/audience-manager/user-guide/features/profile-merge-rules/merge-rules-start.html#configure-merge-rule-code) 설명서의 [!UICONTROL 방문자 ID 서비스] 섹션을 참조하십시오.
