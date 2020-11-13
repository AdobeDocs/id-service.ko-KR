---
title: 사용자 동의에 따라 옵트인을 사용하여 Experience Cloud 활동 제어
description: Adobe 옵트인 개체는 최종 사용자 동의를 바탕으로 웹 페이지에서 쿠키를 생성하거나 비콘을 시작할 수 있는지 여부와 어떤 Experience Cloud 솔루션을 제어할 수 있는지 제어하는 데 도움이 되는 Adobe Experience Platform ID 서비스의 확장입니다.
translation-type: tm+mt
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# 사용자 동의에 따라 Experience Cloud 활동 제어

Adobe [!UICONTROL 옵트인] 개체는 최종 사용자 [!UICONTROL 동의를 바탕으로 웹 페이지에서 쿠키를 만들 수 있는지 또는 비콘을 시작할 수 있는지 여부를 제어하는 데 도움이 되는 Adobe]Experience Platform ID서비스의 확장입니다.

## 옵트인 [!UICONTROL 의 기본 사항]

개인 정보 보호 규정의 중요한 부분은 개인 데이터를 어떻게 사용하고 누가 사용하는지에 대한 사용자 동의 취득 및 양도가 있습니다. 최신 버전의 [!UICONTROL ID 서비스] 기능에는 사용자(UI)와 Adobe 솔루션 사이에 배치되고 최종 사용자의 동의 여부를 기준으로 Adobe Experience Cloud 솔루션 태그의 조건부 실행(예: 사전 및 사후 동의)을 제공하는 기능이 포함되어 있습니다. 다음 이미지에 표시됩니다.

![옵트인 [!UICONTROL 작동 방식] 다이어그램](assets/opt-in.png)

[!UICONTROL 옵트인은] 기본적으로 안내원입니까 아니면 키마스터입니까? 당신이 결정해요

요컨대 이렇다.

**Identity Service에서 [!UICONTROL 옵트인] (부울 변수를 통해)이 활성화되어 있으면, Experience Cloud 솔루션 라이브러리가 태그의 실행 또는 쿠키 설정을 지연하여 해당 솔루션에 대한 동의를 받을 때까지 지연됩니다.**

[!UICONTROL 옵트인] 기능을 사용하면 사용자 동의 *전에* 태그가 실행되는지, 그리고 나서 이 동의 정보(최종 사용자가 제공한 동의와 함께)가 저장되는지를 결정할 수 있으므로 이후 히트에서 사용할 수 있습니다. 동의 저장은 [!UICONTROL 옵트인] 옵션에서 사용하거나 CMP와 통합하여 동의 내용을 저장하도록 할 수 있습니다.

## 옵트인 [!UICONTROL 활성화 및 구성]

[!UICONTROL 또한, 옵트인은] Adobe Experience Platform Launch을 통해 손쉽게 구성할 수 있습니다. 다음 짧은 비디오에서 방법을 확인하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Experience Platform Launch을 사용하지 않는 경우 설명서에 표시된 대로 글로벌 방문자 개체 [!UICONTROL 의 초기화에]옵트인 [의 구성을 설정할 수](https://marketing.adobe.com/resources/help/en_US/mcvid/getting-started.html)있습니다.

## 페이지에서 [!UICONTROL 옵트인] 구현

이러한 모든 설정 및 백엔드 작업은 사이트 방문자에게 동의 옵션을 제공하는 인터페이스를 제공하기 위한 것입니다. 이 UI는 사용자가 작성할 수도 있고, CMP(동의 관리 플랫폼) 파트너를 사용하여 UI를 만들 수도 있습니다.

동의 수집에 [!UICONTROL 옵트인을] 사용하기 위해 UI를 설정할 때 옵트인에 연결할 API를 호출하고 일부 또는 전체 Adobe Experience Cloud 솔루션에 대해 동의를 하도록 [!UICONTROL 알려야] 합니다. 이러한 API에 대한 자세한 내용은 [옵트인 참조 설명서를 참조하십시오](https://marketing.adobe.com/resources/help/en_US/mcvid/api.html). 옵트인에 대한 추가 정보는 주변 설명서 페이지에도 있습니다.

## [!UICONTROL 옵트인] 데모

다음 비디오에서는 페이지에서 작동하는 [!UICONTROL 옵트인] 기능에 대한 빠른 데모 및 Experience Cloud 솔루션이 쿠키 설정, 비콘 시작 등에 영향을 줄 수 있는지 여부를 확인하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**참고:** 이 문서를 작성할 때 모든 Experience Cloud 솔루션에 대해 [!UICONTROL 옵트인] 기능이 라이브러리에 내장되어 있지 않습니다. 현재 옵트인에 대해 지원되는 [!UICONTROL 라이브러리는] 다음과 같습니다.

* ID 서비스
* Analytics
* Audience Manager
* [!DNL Target]
