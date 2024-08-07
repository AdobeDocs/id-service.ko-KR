---
description: 이러한 구성을 사용하여 Experience Cloud ID 서비스 호출에 사용된 기본 도메인 이름을 고유한 하위 도메인 이름으로 변경합니다.
keywords: ID 서비스
title: audienceManagerServer 및 audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 100%

---

# audienceManagerServer 및 audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

이러한 구성을 사용하여 Experience Cloud ID 서비스 호출에 사용된 기본 도메인 이름을 고유한 하위 도메인 이름으로 변경합니다.

**구문:**

* ` audienceManagerServer: " *`하위 도메인 이름`*.demdex.net"`
* ` audienceManagerServerSecure: " *`하위 도메인 이름`*.demdex.net"`

**용도**

일반적으로 [!DNL Experience Cloud] ID 서비스는 `dpm.demdex.net`에서 [!DNL Adobe]를 호출합니다. 너무 일반적이거나 &quot;서드파티&quot;처럼 보이기 때문에 이 대상을 호출하지 않는 경우도 있을 수 있습니다. ID 서비스 호출을 퍼스트 파티 호출처럼 보이도록 하려면 이러한 구성을 사용하여 [!DNL Audience Manager] 하위 도메인 이름을 아래 표시된 대로 `demdex.net`에 추가합니다. `dpm.demdex.net` 호출에 대한 자세한 내용은 [Demdex 도메인에 대한 호출 이해](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=ko-KR)를 참조하십시오.

**요구 사항**

이러한 구성을 위해서는 다음을 사용해야 합니다.

* 회사 레코드의 [!DNL Audience Manager] 하위 도메인 이름. 컨설턴트로부터 이 이름을 확인하거나 가져옵니다.
* [!UICONTROL 조직 ID]와 연관된 하위 도메인 이름입니다.
* *두* 구성 매개 변수 모두 하위 도메인 이름이 같습니다.

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
