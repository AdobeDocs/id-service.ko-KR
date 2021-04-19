---
title: Google Chrome SameSite 레이블 설정 변경
seo-title: Google Chrome SameSite 레이블 설정 변경
description: Adobe ECID(ID 서비스) 라이브러리에 대한 문서입니다.
seo-description: Adobe ECID(ID 서비스) 라이브러리에 대한 문서입니다.
exl-id: f20b25a4-c9bc-41b9-8e49-79b8424e62a0
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '1079'
ht-degree: 100%

---

# Google Chrome SameSite 레이블 설정 변경 {#google-chrome-samesite-labelling-changes}

SameSite 속성은 브라우저에 첫 번째 및 타사 시나리오에서 쿠키를 실행하는 시기와 방법을 알려줍니다. SameSite 속성은 다음 세 값 중 하나를 보유할 수 있습니다. `strict`, `lax` 또는 `none`. Chrome, Firefox, Edge, Safari 및 Opera는 2017년 11월부터 `strict` 및 `lax`을 지원했으며 2018년에 `none`가 도입되었습니다. 그러나 일부 이전 브라우저는 이 설정을 지원하지 않습니다.

2020년 2월에 Google은 Chrome 80을 출시하고 쿠키에 지정된 SameSite 속성 값이 없을 때 기본 설정을 `none`에서 `lax`로 변경했습니다. 이 설정은 쿠키를 &quot;교차 사이트&quot;라고도 하는 타사 컨텍스트에서 사용할 수 없도록 합니다. 다음의 타사 쿠키는 `SameSite=none`으로 설정하고 보안으로 레이블이 명시되어야 합니다.

지정된 SameSite 속성 값이 없는 쿠키는 기본적으로 `lax`로 설정됩니다.

SameSite 속성에 대한 자세한 내용은 [쿠키 표준 문서](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1)를 참조하십시오.

## SameSite 속성 값

| SameSite 속성 값 | 설명 |
| ------ | ------------ |
| `strict` | 이 설정을 사용하는 쿠키는 참조 페이지와 랜딩 페이지가 모두 쿠키와 동일한 도메인에 속해 있는 경우에만 전송됩니다. |
| `lax` | 이 설정을 사용하는 쿠키는 브라우저의 URL에 표시된 도메인이 쿠키의 도메인과 일치하는 경우에만 전송됩니다. 이는 Chrome에서 쿠키의 새로운 기본값입니다. |
| `none` | 이 설정을 사용하는 쿠키는 &quot;교차 사이트&quot;와 같은 외부 또는 타사 액세스에 사용할 수 있습니다. 이 변경 전에 `none`이 쿠키에 대한 기본 SameSite 설정이었으므로 이 설정을 사용하면 쿠키가 일반적으로 작동했던 방식과 가장 유사하게 동작합니다. 하지만 Google에서는 이제 이 설정을 사용하는 모든 쿠키가 보안 플래그를 지정해야 합니다. 즉, 쿠키는 HTTPS를 통한 요청만 작성하여 전송됩니다. 보안 플래그가 없는 모든 교차 사이트 쿠키는 Google에서 거부됩니다. |

## Adobe Experience Cloud 고객으로서 알아야 할 사항

**JavaScript 업데이트 필요 없음**

Adobe 제품은 이미 적합한 속성을 사용하여 타사 쿠키를 설정하는 서버측 업데이트를 발표했습니다. 고객은 JavaScript 라이브러리 업데이트를 필요로 하지 않습니다.

**타사 종단점이 HTTPS를 사용하고 있는지 확인**

모든 고객은 JavaScript 구성이 Adobe 서비스 호출에 HTTPS를 사용하고 있는지 확인해야 합니다. Target, Audience Manager 및 ECID(Experience Cloud Identity Service)가 해당 HTTPS 종단점으로 타사 HTTP 호출을 리디렉션하여 지연을 증가시킬 수 있습니다. 이는 구성을 변경할 필요가 없음을 의미합니다. Analytics에만 적용되는 리디렉션으로 인해 데이터 손실이 발생할 수 있으므로 Analytics 고객은 HTTPS만 사용하도록 구현을 업데이트해야 합니다.

**올바르게 레이블이 지정된 쿠키는 의도한 대로 데이터를 수집해야 합니다.**

쿠키에 올바르게 레이블이 지정되는 한, 브라우저는 이를 차단하는 조치를 취하지 않습니다. 소비자는 특정 유형의 쿠키를 차단할 수 있지만 현재 이는 옵트인 설정으로만 보입니다.

**업데이트된 레이블이 없는 기존 타사 쿠키는 무시됩니다.**

Chrome 80이 SameSite=를 적용하기 전에 만들어진 타사 쿠키`none` 및 보안 플래그 설정은 이러한 플래그가 없으면 Chrome 80에서 무시됩니다.

기존 Adobe 타사 쿠키에는 이러한 플래그가 없으므로 사용자가 Chrome 80으로 업그레이드하거나 해당 쿠키가 손실되기 전에 Edge Server에서 업데이트해야 합니다. Edge Server 업데이트는 쿠키가 사용되는 모든 웹 사이트를 사용자가 방문할 때 자동으로 수행됩니다.

대부분의 Adobe 제품은 이미 쿠키에 적절한 플래그가 할당되어 있습니다. 예외 사항은 타사 데이터 수집을 사용하고 ECID를 사용하지 않는 Analytics 구현입니다. 고객은 새 방문자의 일시적인 소량 증가를 경험할 수도 있습니다. 그렇지 않았다면 재방문자가 되었을 것이기 때문입니다.

**대상 및 마켓 플레이스 파트너에 대해 가능한 쿠키 일치 감소(Audience Manager에만 해당)**

Adobe는 쿠키를 업데이트할 수 있는 권한을 가지지만 Adobe는 파트너에게 필요한 변경을 강요할 수 없습니다. 쿠키 일치 기능은 이러한 업데이트를 하지 않은 대상 파트너 또는 마켓 플레이스 파트너를 사용하는 Audience Manager 고객의 경우 감소될 수 있습니다.

**Analytics에 친숙한 타사 쿠키(Analytics `s_vi` 쿠키만 해당)**

일부 Analytics 구현에서는 Analytics CNAME 별칭을 사용하여 해당 CNAME의 도메인에 `s_vi` 쿠키를 만들 수 있도록 설정합니다. CNAME가 웹 사이트와 동일한 도메인에 있는 경우 자사 쿠키로 지정됩니다. 그러나 여러 도메인을 소유하고 있고 모든 도메인에서 데이터 수집에 동일한 CNAME을 사용하는 경우 다른 도메인에서 타사 쿠키로 지정됩니다.

Chrome에서 새로운 기본 SameSite 설정이 되는 `lax`를 사용하여 CNAME가 더 이상 다른 도메인에서 보이지 않습니다.

변경 사항을 수용하기 위해 이제 Analytics에서 명시적으로 `s_vi` 쿠키의 SameSite 값을 `lax`로 설정합니다. 친숙한 타사 컨텍스트에서 이 쿠키를 사용하려면 SameSite 값을 `none`로 설정합니다. 즉, 항상 HTTPS를 사용해야 합니다. 보안 CNAME에 대해 SameSite 값을 변경하려면 고객 지원 팀에 문의하십시오.

>[!IMPORTANT]
>
>이 작업은 ECID를 사용하는 Analytics 고객, 각 도메인에 대해 별도의 CNAME를 사용하는 고객 또는 타사 Analytics 데이터 수집만 사용하는 고객에게 필요하지 않습니다.

## Adobe 표준 방문자 쿠키

아래 표에는 일반적인 방문자 표준 쿠키만 나열되어 있습니다. 추가 쿠키 구성은 제품별 설명서를 참조하거나 Adobe 담당자에게 문의하십시오.

### ECID

| 쿠키 | 유형 | SameSite 속성 | 보안 속성 |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | 클라이언트측 자사 | 부가 가치가 없는 *Chrome의 기본값은 `lax` 설정 | 구성 가능 |
| AMCVS_###@AdobeOrg | 클라이언트측 자사 | 부가 가치가 없는 *Chrome의 기본값은 `lax` 설정 | 구성 가능 |
| s_ecid | 서버측 자사 | SameSite==`lax` | 설정되지 않음 |

### Audience Manager

| 쿠키 | 유형 | SameSite 속성 | 보안 속성 |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | 타사 | `none` | 보안 설정 |
| Dextp | 타사 | `none` | 보안 설정 |

### Analytics

| 쿠키 | 유형 | SameSite 속성 | 보안 속성 |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> `CNAME`를 사용하는 경우 서버측 자사 </li> <li>2o7.net 또는 omtrdc.net을 사용하는 경우 타사</li></ul> | <ul><li>자사인 경우 `lax`</li> <li>타사인 경우 `none`</li></ul> *고객은 자사 도메인의 고객 지원 티켓을 통해 설정을 편집할 수 있습니다.* | `none` 및 HTTPS 요청을 사용 중인 경우 설정 |
| s_fid | 클라이언트측 자사 | 부가 가치가 없는 *Chrome의 기본값은 `lax` 설정 | 설정되지 않음 |

### Target

| 쿠키 | 유형 | SameSite 속성 | 보안 속성 |
| ------ | ---- | ------------------ | ---------------- |
| mbox | 자사 | 부가 가치가 없는 *Chrome의 기본값은 `lax` 설정 | 설정되지 않음 |

### Ad Cloud

| 쿠키 | 유형 | SameSite 속성 | 보안 속성 |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | 타사 | `none` *Google Chrome 및 Chromium 기반 브라우저에서만* | `none` 및 HTTPS 요청을 사용 중인 경우 설정 |
| data_adcloud | 자사 | 부가 가치가 없는 *Chrome의 기본값은 `lax` 설정 | 설정되지 않음 |
| ev_tm | 타사 | `none` *Google Chrome 및 Chromium 기반 브라우저에서만* | `none` 및 HTTPS 요청을 사용 중인 경우 설정 |

### Bizible

| 쿠키 | 유형 | SameSite 속성 | 보안 속성 |
| ------ | ---- | ------------------ | ---------------- |
| _buid | 타사 | `none` | Secure |

### Marketo Munchkin

| 쿠키 | 유형 | SameSite 속성 | 보안 속성 |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | 클라이언트측 자사 | 부가 가치가 없는 *Chrome의 기본값은 `lax` 설정 | 외부 페이지에 대해 구성 가능 |

> !![IMPORTANT] Adobe 타사 쿠키가 서버측에서 설정됨

자세한 내용은 [Target의 Google Chrome SameSite 정책](https://docs.adobe.com/content/help/ko-KR/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html)에 대한 문서를 참조하십시오.
