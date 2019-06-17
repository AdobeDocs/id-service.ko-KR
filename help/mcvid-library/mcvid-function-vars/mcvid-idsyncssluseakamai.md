---
description: 대상 게시 템플릿이 HTTPS 연결에 대해 Akamai를 사용하는지를 지정합니다.
keywords: ID 서비스
seo-description: 대상 게시 템플릿이 HTTPS 연결에 대해 Akamai를 사용하는지를 지정합니다.
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501 CCC 37-C 3 AB -4454-BFCF -3 E 3 C 3 E 8 B 5 CA 3
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# idSyncSSLUseAkamai{#idsyncssluseakamai}

대상 게시 템플릿이 HTTPS 연결에 대해 Akamai를 사용하는지를 지정합니다.

`idSyncSSLUseAkamai` 구성은 파트너별로 활성화되어 있습니다.

**구문: ** `idSyncSSLUseAkamai: true`

**코드 샘플**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```
