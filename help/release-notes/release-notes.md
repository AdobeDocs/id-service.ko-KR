---
description: Experience Cloud ID 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.
keywords: ID Service
seo-description: Experience Cloud ID 서비스에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.
seo-title: 2020년 릴리스 노트
title: 2020년 릴리스 노트
translation-type: ht
source-git-commit: c4da0f3da99a96d2be7421f49e0e88286d0505e0

---


# Experience Cloud 릴리스 노트 - 2020 {#release-notes}

Experience Cloud ID 서비스(ECID)에 대한 기능 릴리스, 업데이트 또는 변경 사항입니다.

## 버전 4.6

* 기본적으로 `loadSSL` 플래그가 설정되었습니다. ID 서비스에 대한 모든 호출은 기본적으로 `https`에 있습니다.  고객은 `non-ssl` 페이지에서 http로 ID 서비스를 호출하려는 경우 false로 설정할 수 있습니다.
* `ESLint`에서 보고한 문제를 수정하기 위해 `Internet-Explorer (IE)` 버전을 감지하는 데 사용되는 기능을 업데이트했습니다.
ECID에 optIn `pre-approval`이 부여되고 나중에 업데이트되는 경우 `Internet-Explorer (IE) 11`의 성능 문제를 수정했습니다.

## 버전 4.5

* ECID는 버전 4.5부터 `setCustomerIDs` 메서드에 전송된 모든 빈 ID를 거부합니다.
* 옵트인이 `doesOptInApply=false` 및 `isIabContext=true`로 구성되었을 때 발생하는 문제를 수정했습니다.
