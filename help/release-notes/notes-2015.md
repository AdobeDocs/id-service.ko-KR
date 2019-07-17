---
description: 2015년의 릴리스 노트 및 업데이트입니다.
keywords: ID 서비스
seo-description: 2015년의 릴리스 노트 및 업데이트입니다.
seo-title: 2015 릴리스 노트
title: 2015 릴리스 노트
uuid: 49423699-1e0f-49e4-9135-2ae84b4f92df
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# 2015 릴리스 노트 {#release-notes}

2015년의 릴리스 노트 및 업데이트입니다.

## 버전 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

2015년 11월

COPPA(온라인 아동 개인 정보 보호법 - Children’s Online Privacy Protection Act)에서는 입증할 수 있는 부모의 동의 없이 13세 미만의 어린이로부터 온라인으로 개인 정보를 수집하는 것을 금지합니다. COPPA를 중요하게 생각하는 고객은 원하는 경우 브라우저의 타사 도메인에서 쿠키를 설정하지 못하도록 하는 변수를 자신의 [!DNL Experience Cloud] ID 서비스 코드에 추가할 수 있습니다. See [COPPA Support in the Experience Cloud Identity Service](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). 버전 1.5.3 이상

## 버전 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

2015년 9월

* 사용자가 타사 쿠키를 차단하면 동기화 서비스가 제대로 작동하지 않던 Safari 브라우저 버그를 수정했습니다. (AAM-20764)
* 이제 ID 서비스 호출 시 `d_visid_ver=` 매개 변수에 버전 ID가 포함됩니다. 반환된 ID는 문제 해결 및 지원 문제가 있는 내부 팀을 지원합니다. (AAM-20824)

## 버전 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

2015년 8월

* 동기화하거나 실행할 데이터가 없는 경우 ID 서비스가 iframe을 요청하지 못하게 하던 버그가 해결되었습니다. (AAM-20164)
* ID 서비스가 다중 부분, 최상위 도메인 쿠키를 제대로 설정하지 못하게 하던 버그가 해결되었습니다. 예를 들어 `my_company.co.uk`와 같은 도메인이 있는 경우 일부 상황에서 ID 서비스가 `co.uk`에만 쿠키를 설정합니다. (AN-104683)

   이 문제는 다음 조건을 *모두* 충족하는 일부 클라이언트에만 영향을 미쳤습니다.

   * ID 서비스 사용
   * [유예 기간](../reference/analytics-reference/grace-period.md)을 활성화했거나 **&#x200B;자사 쿠키를 사용하고 제3자 쿠키 차단

   * 다중 부분의 최상위 도메인이 있는 페이지 사용

이 릴리스에서 수정된 설명서 내용은 다음과 같습니다.

* [API 메서드 및 코드 라이브러리](../library/library.md#concept-ff27497375644a898d47984aefb21c97): 컨텐츠 및 텍스트가 재구성되었습니다. 대부분의 경우 각 메서드가 개별 페이지에 설명됩니다.
* [Experience Cloud Identity Service 요구 사항](../reference/requirements.md): 수정된 컨텐츠 및 재구성된 텍스트.

## 버전 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

2015년 7월

[!DNL Experience Cloud] ID 서비스는 여러 ID 및 인증 상태를 지원합니다. 또한 [!DNL Audience Manager] 함수에 사용되는 사용자 ID에 대한 `setCustomerIDs` DPID 매핑이 더 이상 지원되지 않으므로 제거되었습니다. [고객 ID 및 인증 상태](../reference/authenticated-state.md)를 참조하십시오.

## 버전 1.4 {#section-f5c596f355b14da28f45c798df513572}

2015년 5월

버전 1.4부터는, 구성을 설정하는 기본 방법이 `Visitor.getInstance` 함수에 대한 두 번째 매개 변수로 config 개체에 전달됩니다.

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

[Experience Cloud](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)를 참조하십시오.

## 버전 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

2015년 2월

AAM Blob 및 위치 힌트에 대한 요청 처리 제한 시간이 수정되었습니다. 이제 제한 시간이 되면 현재 페이지에 대해 해당 필드는 빈 상태로 남아 있고 모든 콜백이 호출됩니다. 제한 시간은 오류 상태로 취급되므로 다음 페이지에서 다시 시도됩니다. (AN-94473, AN-94474)

## 버전 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

2015년 1월

대/소문자 구분 설정이 다를 수 있는 서로 다른 DOM 구현(HTML과 XHTML)을 설명하기 위해 `<script>` 태그의 생성은 물론, JSONP 요청 `<script>` 태그 컨테이너에 대한 `<head>/<body>` 태그 찾기가 다시 작성되었습니다. (AN-9355)
