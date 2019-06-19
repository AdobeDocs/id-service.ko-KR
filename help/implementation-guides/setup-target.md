---
description: 이 지침은 Experience Platform Identity Service를 사용하고 DTM (다이내믹 태그 관리) 를 사용하지 않으려는 Target 고객을 위한 것입니다. 하지만 ID 서비스를 구현하려면 DTM을 사용하는 것이 좋습니다. DTM은 구현 작업 과정을 간소하게 하고 올바른 코드 배치 및 시퀀스를 자동으로 보장합니다.
keywords: ID 서비스
seo-description: 이 지침은 Experience Platform Identity Service를 사용하고 DTM (다이내믹 태그 관리) 를 사용하지 않으려는 Target 고객을 위한 것입니다. 하지만 ID 서비스를 구현하려면 DTM을 사용하는 것이 좋습니다. DTM은 구현 작업 과정을 간소하게 하고 올바른 코드 배치 및 시퀀스를 자동으로 보장합니다.
seo-title: Target에 대한 경험 플랫폼 ID 서비스 구현
title: Target에 대한 경험 플랫폼 ID 서비스 구현
uuid: cb 3581 fa -4 c 4 b -43 aa-bb 8 e -8 db 85 a 6 a 1 ef 2
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Target에 대한 경험 플랫폼 ID 서비스 구현{#implement-the-experience-cloud-id-service-for-target}

이 지침은 Experience Platform Identity Service를 사용하고 DTM (다이내믹 태그 관리) 를 사용하지 않으려는 Target 고객을 위한 것입니다. 하지만 ID 서비스를 구현하려면 DTM을 사용하는 것이 좋습니다. DTM은 구현 작업 과정을 간소하게 하고 올바른 코드 배치 및 시퀀스를 자동으로 보장합니다.

>[!IMPORTANT]
>
>* [시작하기 전에 요구 사항을 읽어보십시오](../reference/requirements.md).
>* 프로덕션 환경에서 구현하기 전에 개발 환경에서 이 코드를 구성하고 테스트하십시오.
>



## 1 단계: ID 서비스 코드 받기 {#section-b32ba0548aa546a79dd38be59832a53e}

코드 라이브러리가 [!DNL ID Service]`VisitorAPI.js` 필요합니다. 이 코드를 받으려면 [고객 지원 센터](https://helpx.adobe.com/marketing-cloud/contact-support.html)에 문의하십시오.

## 2 단계: Visitor. getinstance 함수를 ID 서비스 코드에 추가 {#section-287ef2958e9f43858fe9d630ae519e22}

**1부: 아래의 Visitor.getInstance 함수 복사**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**2부: 함수 코드를 VisitorAPI.js 파일에 추가**

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

## 3 단계: Experience Cloud 조직 ID를 Visitor. getinstance에 추가 {#section-522b1877be9243c39b222859b821f0ce}

`Visitor.getInstance` 함수에서 조직 ID `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` 로 [!DNL Experience Cloud] 대체합니다. 조직 ID를 모를 경우 [!DNL Experience Cloud] 관리 페이지에서 찾을 수 있습니다. [관리 - 핵심 서비스](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html)도 참조하십시오. 편집한 함수는 아래 예제와 비슷합니다.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*조직 ID에서 문자의 대소문자를* 변경하지 마십시오. ID는 대/소문자를 구분하므로 제공된 그대로 정확히 사용해야 합니다.

## 4 단계: 페이지에 방문자 API 코드 추가 {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

파일에 `VisitorAPI.js` 대한 참조하기 전에 `<head>` 사이트에 파일을 `mbox.js` 배포합니다. [!DNL Experience Cloud] ID 서비스는 첫 [!DNL Target] 번째 네트워크 호출이 생성되기 전에 실행해야 합니다. 테스트 및 확인 후에 이 코드를 프로덕션으로 이동합니다.

## 5 단계: ID 서비스 코드 테스트 및 배포 {#section-e81ee439bb8a4c2abea43d76f3112e9c}

다음과 같이 테스트하고 배포할 수 있습니다.

**테스트 및 확인**

ID 서비스 구현을 테스트하려면

* 페이지가 호스팅된 도메인의 AMCV 쿠키를 확인합니다.
* 요청이 `mboxMCGVID`[!DNL Target] 요청에 나타나고 [!DNL Experience Cloud] ID (MID) 가 포함되어 있는지 확인합니다.

AMCV 쿠키 및 MID에 대한 자세한 내용은 [쿠키 및 Experience Platform Identity Service](../introduction/cookies.md) 를 참조하십시오.

**배포**

테스트를 통과한 후에 코드를 배포하십시오.
