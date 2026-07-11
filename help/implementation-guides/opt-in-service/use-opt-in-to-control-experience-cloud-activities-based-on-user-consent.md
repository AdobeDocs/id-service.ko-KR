---
title: 사용자 동의에 따라 옵트인을 사용하여 CX 엔터프라이즈 활동 제어
description: Adobe 옵트인 개체는 Adobe 방문자 ID 서비스의 확장으로, 최종 사용자의 동의에 따라 웹페이지에서 쿠키를 생성하거나, 비콘을 시작할 수 있는 CX Enterprise 솔루션을 제어할 수 있도록 설계되었습니다.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
TQID: https://experienceleague.adobe.com/YfYkXzK8wKw6JC3-EB2ljIOfXGXQV5r6Nw2-XYsGW6c
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
source-wordcount: 518
ht-degree: 28%

---

# 사용자 동의에 따라 CX 엔터프라이즈 활동 제어

Adobe [!UICONTROL Opt-in] 개체는 Adobe 방문자 ID 서비스의 확장으로, 최종 사용자의 동의에 따라 웹페이지에서 쿠키를 생성하거나, 비콘을 시작할 수 있는 CX Enterprise 솔루션을 제어할 수 있도록 설계되었습니다.

## [!UICONTROL Opt-In]의 기본 사항

개인정보 보호 규정의 중요한 측면은 개인 데이터가 누구에 의해 어떻게 사용될 수 있는지에 대한 사용자 동의의 획득 및 양도입니다. 최신 버전의 방문자 ID 서비스에는 최종 사용자의 동의 여부에 따라 CX 엔터프라이즈 솔루션 태그의 조건부 실행(예: 사전 및 사후 동의)을 제공하는 기능이 포함되어 있습니다. 다음 이미지에 이 프로세스가 표시됩니다.

![[!UICONTROL Opt-in]의 작동 방식에 대한 다이어그램](assets/opt-in.png)

[!UICONTROL Opt-in]은(는) 다음과 같이 작동합니다.

**부울 변수를 통해 방문자 ID 서비스에서 [!UICONTROL Opt-in]을(를) 사용하도록 설정한 경우, 해당 솔루션에 대한 동의를 받을 때까지 CX 엔터프라이즈 솔루션 라이브러리가 태그를 실행하거나 쿠키를 설정하는 작업이 지연됩니다.**

[!UICONTROL Opt-in]을(를) 사용하면 사용자 동의 전에 태그 실행 여부를 결정할 수 있으며, 이 동의 정보(최종 사용자가 제공한 동의와 함께)가 저장되어 이후의 히트에서 사용할 수 있습니다. 동의 저장은 [!UICONTROL Opt-in] 옵션에서 사용하거나 CMP와 통합하여 동의 선택을 저장하도록 할 수 있습니다.

## [!UICONTROL Opt-In] 사용 및 구성

[!UICONTROL Opt-in]은(는) 태그를 사용하여 가장 쉽게 구성할 수 있습니다. 다음의 짧은 비디오에서 방법을 확인하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/41135/?captions=kor&quality=12)

태그를 사용하지 않는 경우 [설명서](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=ko&lank=ko-KR)와 같이 글로벌 방문자 개체의 초기화에서 [!UICONTROL Opt-in]의 구성을 설정할 수 있습니다.

## 페이지에서 [!UICONTROL Opt-In] 구현

이러한 모든 설정 및 백엔드 항목은 사이트 방문자에게 동의 옵션을 제공하는 인터페이스를 제공하기 위한 것입니다. UI는 사용자가 작성할 수도 있고, CMP(동의 관리 플랫폼) 파트너를 사용하여 만들 수도 있습니다.

[!UICONTROL Opt-in]을(를) 사용하여 동의를 수집하도록 UI를 설정할 때, [!UICONTROL Opt-in]에 연결할 API를 호출하고 일부 또는 모든 Adobe CX 엔터프라이즈 솔루션에 동의하도록 구성해야 합니다. 이러한 API에 대한 자세한 내용은 [옵트인 참조 설명서](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=ko&lank=ko-KR)를 참조하십시오. 옵트인에 대한 추가 정보는 주변 문서 페이지에도 있습니다.

## [!UICONTROL Opt-In] 데모

다음 비디오에서는 페이지에서 작동하는 [!UICONTROL Opt-in]에 대한 빠른 데모 및 CX 엔터프라이즈 솔루션의 쿠키 설정과 비콘 시작 등의 여부를 결정하는데 어떤 영향을 미칠 수 있는지 확인할 수 있습니다.

>[!VIDEO](https://video.tv.adobe.com/v/41137/?captions=kor&quality=12)

**참고:** 이 문서를 작성할 때 모든 CX 엔터프라이즈 응용 프로그램의 라이브러리에 [!UICONTROL Opt-in]이(가) 내장된 것은 아닙니다. 현재 [!UICONTROL Opt-in]에 대해 지원되는 라이브러리는 다음과 같습니다.

* 방문자 ID 서비스
* Analytics
* Audience Manager
* Target

