---
description: Adobe 방문자 ID 서비스를 통해 CX 엔터프라이즈 애플리케이션 및 서비스에 공통된 ID 프레임워크를 사용할 수 있습니다. ECID라고 하는 고유한 영구 ID를 사이트 방문자에게 할당하여 작동합니다.
keywords: 방문자 ID 서비스, ECID
title: Adobe 방문자 ID 서비스
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
TQID: https://experienceleague.adobe.com/xzEgzuN2NnyOnhCPocQikOXHFRU6zmLWLGdrJL4C3GM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 467
ht-degree: 24%

---

# Adobe 방문자 ID 서비스 {#experience-cloud-id-service}

>[!BEGINSHADEBOX]

방문자 ID 서비스가 [Experience Platform ID 서비스](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=ko-KR)가 **아님**&#x200B;입니다. 방문자 ID 서비스는 이 안내서에서 설명한 `VisitorAPI.js` JavaScript 라이브러리로서 Adobe Analytics, Audience Manager 및 Target에 대한 ECID를 설정합니다. 장치 및 시스템 간의 ID를 통합 고객 프로필로 확인하는 Adobe Experience Platform 서비스를 찾는 경우 대신 [Experience Platform ID 서비스 개요](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=ko-KR)를 참조하세요.

>[!ENDSHADEBOX]

Adobe 방문자 ID 서비스를 통해 CX 엔터프라이즈 애플리케이션 및 서비스에 공통된 ID 프레임워크를 사용할 수 있습니다. ECID라고 하는 고유한 영구 ID를 사이트 방문자에게 할당하여 작동합니다.

## ID의 주요 엔티티 이해

Adobe이 방문자를 고유하게 식별하고 ID 정보를 확인하는 데 어떻게 도움이 되는지 더 잘 이해하려면 아래 분류를 읽어 보십시오.

* **방문자 ID 서비스**: 방문자 ID 서비스 **이(가) ECID 설정을 담당합니다**. 자세한 내용은 [방문자 ID 서비스 개요](./introduction/overview.md)를 참조하십시오.
* **ECID**: ECID는 Adobe Experience Platform 및 Adobe CX 엔터프라이즈 응용 프로그램에서 사용자와 장치를 식별하는 데 사용되는 공유 ID 네임스페이스입니다. ECID에 대한 자세한 내용은 [ECID 개요](https://experienceleague.adobe.com/ko/docs/experience-platform/identity/features/ecid)를 참조하십시오.
* **Experience Platform Identity Service**: Experience Platform Identity Service는 디바이스와 시스템 간에 ID를 연결하여 고객 및 고객 행동에 대한 포괄적인 보기를 제공합니다. 자세한 내용은 [Experience Platform Identity Service 개요](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=ko-KR)를 참조하십시오.

## 시작하기

* [방문자 ID 서비스 개요](introduction/overview.md): 방문자 ID 서비스의 기능과 CX Enterprise에 어떻게 적합한지 알아봅니다.
* [방문자 ID 서비스에 대한 요구 사항](reference/requirements.md): 방문자 ID 서비스를 구현하기 전에 솔루션과 코드 라이브러리가 사전 요구 사항을 충족하는지 확인하십시오.
* [구현 메서드](implementation-guides/implementation-methods.md): [태그](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=ko-KR)를 사용하는 표준 구현과 비표준 직접 통합 메서드를 비교합니다.

## 설명서 살펴보기

**구현**

* [구현 안내서](implementation-guides/implementation-guides.md)
* [방문자 ID 서비스와 직접 통합](implementation-guides/direct-integration.md)
* [옵트인 서비스 개요](implementation-guides/opt-in-service/optin-overview.md)
* [방문자 ID 서비스 테스트 및 확인](implementation-guides/test-verify.md)

**API 참조**

* [방문자 ID 서비스 API 개요](library/library.md)
* [getVisitorValues](library/get-set/getvisitorvalues.md)
* [idSyncContainerID](library/function-vars/idsyncontainerid.md)

**FAQ**

* [방문자 ID 서비스 FAQ](faq-intro/faq.md)
* [기타 CX 엔터프라이즈 솔루션에 대한 FAQ](faq-intro/other-faq.md)

## 추가 리소스

* GitHub의 [ECID JavaScript 라이브러리 릴리스](https://github.com/Adobe-Marketing-Cloud/id-service/releases)
* [방문자 ID 서비스에 대한 릴리스 노트](release-notes/notes-2022.md)
* [Adobe 개인 정보 보호 센터](https://www.adobe.com/kr/privacy.html)
* [Adobe CX Enterprise 설명서](https://experienceleague.adobe.com/docs/home.html?lang=ko-KR)

