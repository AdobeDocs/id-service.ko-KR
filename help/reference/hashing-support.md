---
description: ECID (Experience Cloud ID Service) 는 고객 ID 또는 이메일 주소를 전달하고 해시된 ID를 전달할 수 있는 SHA -256 해시 알고리즘을 지원합니다. 해시된 식별자를 Experience Cloud로 전송하는 선택적 Javascript 메서드입니다. 고객 ID를 전송하기 전에 자신의 해싱을 계속 사용할 수 있습니다.
keywords: ID 서비스
seo-description: ECID (Experience Cloud ID Service) 는 고객 ID 또는 이메일 주소를 전달하고 해시된 ID를 전달할 수 있는 SHA -256 해시 알고리즘을 지원합니다. 해시된 식별자를 Experience Cloud로 전송하는 선택적 Javascript 메서드입니다. 고객 ID를 전송하기 전에 자신의 해싱을 계속 사용할 수 있습니다.
seo-title: Setcustomerids에 대한 SHA 256 해싱 지원
title: Setcustomerids에 대한 SHA 256 해싱 지원
translation-type: tm+mt
source-git-commit: ac1131be75fd04b51cd1d646086e1802a43afb18

---


# SHA256 Hashing Support for `setCustomerIDs` {#hashing-support}

ECID (Experience Cloud ID Service) 는 고객 ID 또는 이메일 주소를 전달하고 해시된 ID를 전달할 수 있는 SHA -256 해시 알고리즘을 지원합니다. 해시된 식별자를 Experience Cloud로 전송하는 선택적 Javascript 메서드입니다. 고객 ID를 전송하기 전에 자신의 해싱을 계속 사용할 수 있습니다.
아래 섹션에 설명된 대로 Setcustomerids를 사용하여 해싱 지원을 구현하는 방법은 두 가지가 있습니다.

* [ECID에서 setcustomerids 메서드를 사용합니다.](/help/reference/hashing-support.md#use-setcustomerids-method)
* [Adobe Experience Platform Launch에서 작업 추가](/help/reference/hashing-support.md#add-action-launch)

## Use the `setCustomerIDs` method in ECID {#use-setcustomerids-method}

The first method leverages using the [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) method.

해싱하기 전에 Ecid 라이브러리는 customerids에서 데이터 표준화를 수행합니다. 이 과정에서는 두 끝의 Customerids의 공백을 트리밍하고 모든 문자를 소문자로 변환합니다. 예를 들어, 이메일 주소의 경우: " ecid@adobe.com "이" ecid@adobe.com "becomes

SHA -256 해싱을 사용하여 단일 고객 ID (위에 언급된 이메일 주소) 를 설정하는 방법은 아래의 코드 예를 참조하십시오.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

Experience Cloud 방문자 ID와 함께 추가 고객 ID, 인증 상태 및 해시 유형 (SHA -256) 를 각 방문자와 연결할 수 있습니다. 해시 유형을 제공하지 않는 경우 해싱 없음으로 간주됩니다.

`setCustomerIDs` 메서드는 동일한 방문자의 여러 고객 ID를 수락합니다. 따라서 여러 다른 장치에서 개별 사용자를 식별하고 타깃팅하는 데 도움이 됩니다. 예를 들어 이러한 ID를 [고객 속성](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html)으로 Experience Cloud에 업로드하고 다른 솔루션에 있는 이 데이터에 액세스할 수 있습니다.

Customer IDs, authenticated states and hash type *are not* stored in a cookie to be used later. Instead, Customer IDs, authenticated states and hash type should be stored in an instance variable, to be retrieved using [`getCustomerIDs`](/help/library/get-set/getcustomerids.md), as shown below:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

`setCustomerIDs` 이 방법을 사용하면 해시된 고객 ID가 포함된 `dpm.demdex.net``d_cid_ic` 쿼리 매개 변수가 추가되면서 Experience Cloud ID 서비스에 대한 호출이 호출됩니다. 샘플 호출은 아래와 같이 표시될 수 있습니다. 명확성을 위해 줄 바꿈이 추가되었습니다.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

See the table below for a description of the `d_cid_ic` parameter and authentication state.

| 매개 변수 | 설명 |
|------------|----------|
| `d_cid_ic` | 통합 코드, 고유 사용자 ID (DPUUID) 및 인증된 상태 ID를 ID 서비스로 전달합니다. Separate the Integration Code and DPUUID with the non-printing control character, <code>%01</code>: <br> Example: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>인증 상태</b> <br> d_ cid_ ic 매개 변수의 선택적 ID 입니다. Expressed as an integer, it identifies users according to their authentication status as shown below: <br> <ul><li>0 (알 수 없거나 인증되지 않음)</li><li>1 (현재 이 인스턴스/페이지/앱 컨텍스트에 대해 인증됨)</li><li>2(로그아웃됨)</li></ul> <br> 예: <br> <ul><li>알 수 없음: ...d_cid=123%01456%01<b>0</b></li><li>인증됨: ...d_cid=123%01456%01<b>1</b></li><li>로그아웃됨: ...d_cid=123%01456%01<b>2</b></li></ul> |

## Add an Action in Adobe Experience Platform Launch {#add-action-launch}

경험 플랫폼 Launch는 Adobe의 차세대 태그 관리 기능입니다. [Launch 제품 설명서의 Launch에 대한 자세한](https://docs.adobe.com/content/help/en/launch/using/overview.html)내용을 살펴보십시오.

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

![](/help/reference/assets/hashing-support.png)

<br> 

구성을 확인하면 론치가 다음과 같이 데이터를 객체로 래핑합니다.

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

다음은 코드 샘플입니다.

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Similarly to the `setCustomerIDs` method described in the first section, this results in a call to the Experience Cloud ID Service, with the addition of the `d_cid_ic` query parameter.