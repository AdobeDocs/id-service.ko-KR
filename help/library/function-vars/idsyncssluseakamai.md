---
description: 대상 게시 템플릿이 HTTPS 연결에 대해 Akamai를 사용하는지를 지정합니다.
keywords: 방문자 ID 서비스
title: idSyncSSLUseAkamai
exl-id: 74c24eb5-bf3d-4e6b-ac7d-1a37d940d77f
TQID: https://experienceleague.adobe.com/bFdWlHB0fNXOYQ6qIg6kx7pku6iZlqhx13Yu-i3nm5E
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 41
ht-degree: 100%

---

# idSyncSSLUseAkamai{#idsyncssluseakamai}

대상 게시 템플릿이 HTTPS 연결에 대해 Akamai를 사용하는지를 지정합니다.

`idSyncSSLUseAkamai` 구성은 파트너별로 활성화되어 있습니다.

**구문:** `idSyncSSLUseAkamai: true`

**코드 샘플**

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```

