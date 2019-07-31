---
description: Experience Cloud Identity 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.
keywords: ID 서비스
seo-description: Experience Cloud Identity 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.
seo-title: 2019 릴리스 노트
title: 2019 릴리스 노트
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 4532d09cc9b4d83fa62c13bd1adac7abdae222b1

---


# 2019 릴리스 노트 {#release-notes}

Experience Cloud Identity 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.

## 2019 릴리스 노트 {#topic-1b9a1c3ec5044e1c987785950f697e25}

[!DNL Experience Cloud] ID 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.

## 버전 4.4 {#version-4point4}

**새로운 기능**

[Setcustomerids에 대한 SHA 256 해싱 지원](/help/reference/hashing-support.md). ECID (Experience Cloud ID Service) 는 고객 ID 또는 이메일 주소를 전달하고 해시된 ID를 전달할 수 있는 SHA -256 해시 알고리즘을 지원합니다.

**수정 사항, 개선 사항, 개선 사항**

* We made a configuration update to `cookieDomain`. The ECID library now filters out the empty string `cookieDomain` in `initConfig` and uses the top level cookie domain, which is returned by the getDomain method. (CORE-29223)
* We fixed a bug related to `getVisitorValues` in `localVisitor`. (CORE-31287)
* We fixed a bug where there was an inconsistency for the MCOPTOUT value in the Safari browser, returned by the `getVisitorValue` method. (CORE-29719)
* We updated the Opt-in library by adding `optIn.off` to unsubscribe from events.
* We fixed a bug related to the setTimeout function, where `setTimeout` violated the Content Security Policy (CSP) on some customer sites. (CORE-30623)

## 버전 4.3 {#version-4point3}

**ITP 2.1**&#x200B;지원. 추적 서버가 퍼스트 파티 CNAME에 설정된 경우 새 쿠키 (s_ ECID) 가 ECID 값으로 배치됩니다. ECID 라이브러리는 7 일 넘게 ID를 지속하는 값을 참조합니다. See [ECID library methods in a Safari ITP world](/help/reference/ecid-library-methods.md).

**Securecookie 구성에 대한 버그 수정.**

## 버전 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**옵트인 서비스**&#x200B;입니다. 옵트인은 Experience Cloud 라이브러리에서 방문자 웹 페이지에 쿠키를 생성할 수 있는지 여부를 제어할 수 있는 ECID(Experience Cloud ID)의 확장 프로그램입니다. [Experience Platform Launch](https://docs.adobelaunch.com/)를 사용하면 Analytics, Target, Audience Manager 및 기타 모든 Experience Cloud 솔루션을 활성화하여 Experience Cloud 솔루션에 대한 방문자 옵트인 동의 수집을 간소화할 수 있습니다.

## 버전 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| 항목 | 설명 |
|---|---|
| 문자열을 전달한 경우 `disableIdSyncs` 플래그가 작동하지 않습니다. | 수정되었습니다. `getInstance` 함수의 `disableidSyncs` 매개 변수에 설정된 값이 이제 적용됩니다. |
| 타사 iFrames에서 ECID를 가져오지 않음 | Safari Mobil의 ECID 및 작동하지 않는 여러 iFrames의 ECID가 수정되었습니다. |

