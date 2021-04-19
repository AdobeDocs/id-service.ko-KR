---
description: 이러한 지침은 Experience Cloud Identity 서비스를 사용하고 DTM(Dynamic Tag Management)은 사용하지 않으려는 Target 고객을 대상으로 합니다. 그러나 DTM을 사용하여 ID 서비스를 구현하는 것이 매우 좋습니다. DTM을 사용하면 구현 워크플로우를 간소화할 수 있고, 올바른 코드 배치 및 순서를 자동으로 확인할 수 있습니다.
keywords: ID 서비스
seo-description: 이러한 지침은 Experience Cloud Identity 서비스를 사용하고 DTM(Dynamic Tag Management)은 사용하지 않으려는 Target 고객을 대상으로 합니다. 그러나 DTM을 사용하여 ID 서비스를 구현하는 것이 매우 좋습니다. DTM을 사용하면 구현 워크플로우를 간소화할 수 있고, 올바른 코드 배치 및 순서를 자동으로 확인할 수 있습니다.
seo-title: Target용 Experience Cloud Identity 서비스 구현
title: Target용 Experience Cloud Identity 서비스 구현
uuid: cb3581fa-4c4b-43aa-bb8e-8db85a6a1ef2
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '461'
ht-degree: 100%

---

# Target용 Experience Cloud Identity 서비스 구현{#implement-the-experience-cloud-id-service-for-target}

이러한 지침은 Experience Cloud Identity 서비스를 사용하고 DTM(Dynamic Tag Management)은 사용하지 않으려는 Target 고객을 대상으로 합니다. 그러나 DTM을 사용하여 ID 서비스를 구현하는 것이 매우 좋습니다. DTM을 사용하면 구현 워크플로우를 간소화할 수 있고, 올바른 코드 배치 및 순서를 자동으로 확인할 수 있습니다.

>[!IMPORTANT]
>
>* [시작하기 전에 요구 사항을 읽어보십시오](../reference/requirements.md).
>* 프로덕션 환경에서 구현하기 전에 개발 환경에서 이 코드를 구성하고 테스트하십시오.


## 1단계: ID 서비스 코드 가져오기 {#section-b32ba0548aa546a79dd38be59832a53e}

[!UICONTROL ID 서비스]에는 `VisitorAPI.js` 코드 라이브러리가 필요합니다. 이 코드를 받아보려면 [고객 지원 센터](https://helpx.adobe.com/kr/marketing-cloud/contact-support.html)에 문의하십시오.

## 2단계: ID 서비스 코드에 Visitor.getInstance 함수 추가 {#section-287ef2958e9f43858fe9d630ae519e22}

**1부: 아래 Visitor.getInstance 함수 복사**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**2부: VisitorAPI.js 파일에 함수 코드 추가**

`Visitor.getInstance` 함수를 파일 끝, 코드 블록 뒤에 추가합니다. 편집한 파일은 다음과 같습니다.

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## 3단계: Visitor.getInstance에 Experience Cloud 조직 ID 추가 {#section-522b1877be9243c39b222859b821f0ce}

`Visitor.getInstance` 함수에서 `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE`를 [!DNL Experience Cloud] 조직 ID로 바꿉니다. 조직 ID를 모를 경우 [!DNL Experience Cloud] 관리 페이지에서 찾을 수 있습니다. 또한, [관리 - 핵심 서비스](https://docs.adobe.com/content/help/ko-KR/core-services/interface/manage-users-and-products/admin-getting-started.html)도 참조하십시오. 편집한 함수는 아래 예제와 비슷합니다.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>조직 ID의 대/소문자를 변경하지 *마십시오*. ID는 대/소문자를 구분하므로 제공된 그대로 정확히 사용해야 합니다.

## 4단계: 페이지에 방문자 API 코드 추가 {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

`mbox.js` 파일 참조 전 `<head>` 태그의 사이트에 `VisitorAPI.js` 파일을 배포합니다. [!DNL Experience Cloud] ID 서비스는 첫 번째 [!DNL Target] 네트워크 호출이 생성되기 전에 실행해야 합니다. 테스트 및 확인 후에 이 코드를 프로덕션으로 이동합니다.

## 5단계: ID 서비스 코드 테스트 및 배포 {#section-e81ee439bb8a4c2abea43d76f3112e9c}

다음과 같이 테스트하고 배포할 수 있습니다.

**테스트 및 확인**

ID 서비스 구현을 테스트하려면:

* 페이지가 호스팅된 도메인에서 AMCV 쿠키를 확인합니다.
* `mboxMCGVID`가 [!DNL Target] 요청에 표시되는지 그리고 MID([!DNL Experience Cloud] ID)를 포함하는지 확인합니다.

AMCV 쿠키 및 MID에 대한 자세한 내용은 [쿠키 및 Experience Cloud Identity 서비스](../introduction/cookies.md)를 참조하십시오.

**배포**

테스트를 통과한 후 코드를 배포합니다.
