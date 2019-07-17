---
description: 이러한 구성을 사용하여 Experience Cloud Identity Service 호출에 사용되는 기본 도메인 이름을 자신의 하위 도메인 이름으로 변경합니다.
keywords: ID 서비스
seo-description: 이러한 구성을 사용하여 Experience Cloud Identity Service 호출에 사용되는 기본 도메인 이름을 자신의 하위 도메인 이름으로 변경합니다.
seo-title: audienceManagerServer 및 audienceManagerServerSecure
title: audienceManagerServer 및 audienceManagerServerSecure
uuid: e21cacbf-5151-4d34-b0f7-9e90275f4c7c
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# audienceManagerServer 및 audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

이러한 구성을 사용하여 Experience Cloud Identity Service 호출에 사용되는 기본 도메인 이름을 자신의 하위 도메인 이름으로 변경합니다.

**구문:**

* ` audienceManagerServer: " *`하위 도메인 이름`*.demdex.net"`
* ` audienceManagerServerSecure: " *`하위 도메인 이름`*.demdex.net"`

**용도**

일반적으로 [!DNL Experience Cloud] ID 서비스는 `dpm.demdex.net`에서 [!DNL Adobe]를 호출합니다. 너무 일반적이거나 "타사"처럼 보이기 때문에 이 대상을 호출하지 않는 경우도 있을 수 있습니다. ID 서비스 호출을 퍼스트 파티 호출처럼 보이도록 하려면 이러한 구성을 사용하여 [!DNL Audience Manager] 하위 도메인 이름을 아래 표시된 대로 `demdex.net`에 추가합니다. `dpm.demdex.net` 호출에 대한 자세한 내용은 [Demdex 도메인 호출 이해](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)를 참조하십시오.

**요구 사항**

이러한 구성을 사용하려면 다음을 사용해야 합니다.

* 회사 레코드의 [!DNL Audience Manager] 하위 도메인 이름. 컨설턴트로부터 이 이름을 확인하거나 가져옵니다.
* [!DNL Organization ID]와 연관된 하위 도메인 이름.
* 하위 도메인 이름이 동일한 *두* 구성 매개 변수.

**코드 샘플**

이 예에서는 미디어 엔터테인먼트 회사가 `dpm.demdex.net`을 호출하는 것에 대해 법적인 우려를 표명했다고 가정해 보겠습니다. [!DNL Audience Manager]에서 이 회사 레코드의 하위 도메인 이름은 Music1입니다. 다음 코드 샘플은 이러한 고객별 하위 도메인 이름으로 ID 서비스 데이터 호출을 브랜딩하는 방법을 보여 줍니다.

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
     ... 
     //Configure ID service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

