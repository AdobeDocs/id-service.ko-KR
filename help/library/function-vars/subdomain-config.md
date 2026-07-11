---
description: 이러한 구성을 사용하여 방문자 ID 서비스 호출에 사용된 기본 도메인 이름을 고유한 하위 도메인 이름으로 변경합니다.
keywords: 방문자 ID 서비스
title: audienceManagerServer 및 audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
TQID: https://experienceleague.adobe.com/a5KVErDX4putY8d9vGf-uAwswNzE0Maf-JEyfmQxhbg
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 234
ht-degree: 44%

---

# audienceManagerServer 및 audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

이러한 구성을 사용하여 방문자 ID 서비스 호출에 사용된 기본 도메인 이름을 고유한 하위 도메인 이름으로 변경합니다.

**구문:**

* `audienceManagerServer: " *`하위 도메인 이름`*.demdex.net"`
* `audienceManagerServerSecure: " *`하위 도메인 이름`*.demdex.net"`

**용도**

일반적으로 방문자 ID 서비스는 `dpm.demdex.net`에 Adobe을 호출합니다. 너무 일반적이거나 &quot;서드파티&quot;처럼 보이기 때문에 이 대상을 호출하지 않는 경우도 있을 수 있습니다. 방문자 ID 서비스 호출을 퍼스트 파티 호출처럼 보이도록 하려면 이러한 구성을 사용하여 Audience Manager 하위 도메인 이름을 아래 표시된 대로 `demdex.net`에 추가하십시오. `dpm.demdex.net` 호출에 대한 자세한 내용은 [Demdex 도메인에 대한 호출 이해](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=ko-KR)를 참조하십시오.

**요구 사항**

이러한 구성을 위해서는 다음을 사용해야 합니다.

* 회사 레코드의 Audience Manager 하위 도메인 이름. 컨설턴트로부터 이 이름을 확인하거나 가져옵니다.
* IMS 조직 ID와 연결된 하위 도메인 이름.
* *두* 구성 매개 변수 모두 하위 도메인 이름이 같습니다.

**코드 샘플**

이 예에서는 미디어 엔터테인먼트 회사가 `dpm.demdex.net`을 호출하는 것에 대해 법적인 우려를 표명했다고 가정해 보겠습니다. Audience Manager에서 이 회사 레코드의 하위 도메인 이름은 Music1입니다. 다음 코드 샘플은 이러한 고객별 하위 도메인 이름으로 방문자 ID 서비스 데이터 호출을 브랜딩하는 방법을 보여 줍니다.

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE",{ 
     ... 
     //Configure Visitor ID Service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

