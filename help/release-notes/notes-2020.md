---
description: Experience Cloud ID 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.
keywords: ID 서비스
title: 2020 릴리스 정보
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: ht
source-wordcount: '213'
ht-degree: 100%

---

# Experience Cloud 릴리스 정보 - 2020 {#release-notes}

Experience Cloud ID 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.

## 버전 5.1.1

* VisitorJS가 iFrame에 로드될 때 AMCV 쿠키를 `SameSite=None`(으)로 설정하는 패치가 수정되었습니다.

## 버전 5.1.0

* AMCV 쿠키에 대한 `sameSiteCookie` 속성을 지정하기 위해 `SameSite` 구성을 추가합니다. 이 구성은 `SameSite` 속성에 대해 다음 값을 지원합니다.
   * `Strict`
   * `Lax`
   * `None`

이러한 속성 값에 대한 자세한 내용은 [web.dev](https://web.dev/samesite-cookies-explained/) 및 [Chromium Projects의 SameSite 업데이트](https://www.chromium.org/updates/same-site/)를 참조하십시오.

## 버전 5.0.1

* 새 IAB 동의 문자열이 Adobe Data 데이터 수집 에지로 전송될 때 `d_cf` 플래그를 포함하는 패치가 수정되었습니다.

## 버전 5.0.0

* Visitor 5.0.0 릴리스에는 `IAB 2.0`에 대한 지원이 포함됩니다.

## 버전 4.6

* 기본적으로 `loadSSL` 플래그가 설정되었습니다. ID 서비스에 대한 모든 호출은 기본적으로 `https`에 있습니다.  고객은 `non-ssl` 페이지에서 http로 ID 서비스를 호출하려는 경우 false로 설정할 수 있습니다.
* `ESLint`에서 보고한 문제를 수정하기 위해 `Internet-Explorer (IE)` 버전을 감지하는 데 사용되는 기능을 업데이트했습니다.
ECID에 optIn `pre-approval`이 부여되고 나중에 업데이트되는 경우 `Internet-Explorer (IE) 11`의 성능 문제를 수정했습니다.

## 버전 4.5

* ECID는 버전 4.5부터 `setCustomerIDs` 메서드에 전송된 모든 빈 ID를 거부합니다.
* 옵트인이 `doesOptInApply=false` 및 `isIabContext=true`로 구성되었을 때 발생하는 문제를 수정했습니다.

모든 제품에 대한 월별 릴리스 정보는 [Experience Cloud 릴리스 정보](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=ko-KR)를 확인하십시오.
