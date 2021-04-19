---
description: ECID(Experience Cloud ID 서비스)는 고객 ID 또는 이메일 주소에서 전달하고 해시된 ID 밖으로 전달할 수 있는 SHA-256 해시 알고리즘을 지원합니다. 해시된 식별자를 Experience Cloud로 전송하는 선택적 Javascript 메서드입니다. 고객 ID를 전송하기 전에 고유한 해시 메서드를 계속 사용할 수 있습니다.
keywords: ID 서비스
seo-description: ECID(Experience Cloud ID 서비스)는 고객 ID 또는 이메일 주소에서 전달하고 해시된 ID 밖으로 전달할 수 있는 SHA-256 해시 알고리즘을 지원합니다. 해시된 식별자를 Experience Cloud로 전송하는 선택적 Javascript 메서드입니다. 고객 ID를 전송하기 전에 고유한 해시 메서드를 계속 사용할 수 있습니다.
seo-title: setCustomerIDs에 대한 SHA256 해시 지원
title: setCustomerIDs에 대한 SHA256 해시 지원
exl-id: fd30634e-6435-4d14-8804-649c1ad3aaaa
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '666'
ht-degree: 100%

---

# `setCustomerIDs`에 대한 SHA256 해시 지원 {#hashing-support}

ECID(Experience Cloud ID 서비스)는 고객 ID 또는 이메일 주소에서 전달하고 해시된 ID 밖으로 전달할 수 있는 SHA-256 해시 알고리즘을 지원합니다. 해시된 식별자를 Experience Cloud로 전송하는 선택적 Javascript 메서드입니다. 고객 ID를 전송하기 전에 고유한 해시 메서드를 계속 사용할 수 있습니다.
아래 섹션에 설명된 대로 setCustomerIDs를 사용하여 해시 지원을 구현하는 방법은 두 가지가 있습니다.

* [ECID에서 setCustomerIDs 메서드 사용](/help/reference/hashing-support.md#use-setcustomerids-method)
* [Adobe Experience Platform Launch에서 동작 추가](/help/reference/hashing-support.md#add-action-launch)

## ECID에서 `setCustomerIDs` 메서드 사용 {#use-setcustomerids-method}

첫 번째 메서드는 [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) 메서드를 사용하여 활용합니다.

ECID 라이브러리는 해싱하기 전에 customerIDs에 데이터 표준화를 수행합니다. 이 과정에서는 양쪽 끝에서 customerIDs의 공백을 트리밍하고 모든 문자를 소문자로 변환합니다. 예를 들어, 이메일 주소의 경우 &quot; ecid@adobe.com &quot;은 &quot;ecid@adobe.com&quot;이 됩니다.

SHA-256 해시를 사용하여 단일 고객 ID(위에서 언급한 이메일 주소)를 설정하는 방법에 대한 아래의 코드 예를 참조하십시오.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

Experience Cloud 방문자 ID와 함께 추가 고객 ID, 인증 상태 및 해시 유형(SHA-256)을 각 방문자와 연결할 수 있습니다. 해시 유형을 제공하지 않으면 해시 없음으로 간주됩니다.

`setCustomerIDs` 메서드는 동일한 방문자의 여러 고객 ID를 수락합니다. 따라서 여러 다른 장치에서 개별 사용자를 식별하고 타깃팅하는 데 도움이 됩니다. 예를 들어 이러한 ID를 [고객 속성](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html)으로 Experience Cloud에 업로드하고 다른 솔루션에 있는 이 데이터에 액세스할 수 있습니다.

고객 ID, 인증된 상태 및 해시 유형은 나중에 사용할 수 있게 쿠키에 저장되지 *않습니다*. 대신, 고객 ID, 인증된 상태 및 해시 유형은 아래와 같이 [`getCustomerIDs`](/help/library/get-set/getcustomerids.md)를 사용하여 검색할 수 있도록 인스턴스 변수에 저장해야 합니다.

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

`setCustomerIDs` 메서드를 사용하면 해시된 고객 ID가 포함된 `d_cid_ic` 쿼리 매개 변수의 추가로 Experience Cloud ID 서비스, `dpm.demdex.net`가 호출됩니다. 샘플 호출은 아래와 같이 표시될 수 있습니다. 명확하게 하기 위해 줄 바꿈을 추가했습니다.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

`d_cid_ic` 매개 변수 및 인증 상태에 대한 설명은 아래 표를 참조하십시오.

| 매개 변수 | 설명 |
|------------|----------|
| `d_cid_ic` | 통합 코드, DPUUID(고유 사용자 ID) 및 인증된 상태 ID를 ID 서비스에 전달합니다. 통합 코드 및 DPUUID를 인쇄되지 않는 제어 문자 %01</code>와 구분합니다. <br> 예:d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>인증 상태</b> <br> d_cid_ic 매개 변수에서 선택적 ID입니다. 정수로 표시되며, 아래와 같이 인증 상태에 따라 사용자를 식별합니다. <br> <ul><li>0(알 수 없음 또는 인증되지 않음)</li><li>1(현재 이 인스턴스/페이지/앱 컨텍스트에 대해 인증됨)</li><li>2(로그아웃됨)</li></ul> <br> 예: <br> <ul><li>알 수 없음: ...d_cid=123%01456%01<b>0</b></li><li>인증됨: ...d_cid=123%01456%01<b>1</b></li><li>로그아웃됨: ...d_cid=123%01456%01<b>2</b></li></ul> |

## Adobe Experience Platform Launch에서 동작 추가 {#add-action-launch}

Experience Platform Launch는 Adobe의 차세대 태그 관리 기능입니다. [Launch 제품 설명서](https://docs.adobe.com/content/help/en/launch/using/overview.html)에서 Launch에 대해 자세히 알아보십시오.

Launch에서 작업을 추가하려면 Adobe Launch에서 [규칙 설명서](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html)를 읽고 아래의 화면 캡처를 참조하십시오.

![](/help/reference/assets/hashing-support.png)

<br> 

구성을 확인한 후 Launch에서 다음과 같이 데이터를 개체에 래핑합니다.

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

첫 번째 섹션에 설명된 `setCustomerIDs` 메서드와 유사하게, `d_cid_ic` 쿼리 매개 변수의 추가로 Experience Cloud ID 서비스가 호출됩니다.
