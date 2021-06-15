---
description: 대상 게시 템플릿이 HTTPS 연결에 대해 Akamai를 사용하는지를 지정합니다.
keywords: ID 서비스
title: idSyncSSLUseAkamai
exl-id: 74c24eb5-bf3d-4e6b-ac7d-1a37d940d77f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '39'
ht-degree: 100%

---

# idSyncSSLUseAkamai{#idsyncssluseakamai}

대상 게시 템플릿이 HTTPS 연결에 대해 Akamai를 사용하는지를 지정합니다.

`idSyncSSLUseAkamai` 구성은 파트너별로 활성화되어 있습니다.

**구문:** `idSyncSSLUseAkamai: true`

**코드 샘플**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```
