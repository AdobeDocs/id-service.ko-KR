---
description: 이 ID 서비스는 조직 ID, Experience Cloud AMCV 쿠키 및 demdex 쿠키를 사용하여 사이트 방문자에 대한 고유하고 영구적인 식별자를 만들어 저장합니다. 이러한 쿠키를 사용하면 ID 서비스에서 다른 도메인의 방문자를 추적하고 다른 Experience Cloud 솔루션 간에 데이터 공유를 사용할 수 있습니다.
keywords: Playstation;ID 서비스
seo-description: 이 ID 서비스는 조직 ID, Experience Cloud AMCV 쿠키 및 demdex 쿠키를 사용하여 사이트 방문자에 대한 고유하고 영구적인 식별자를 만들어 저장합니다. 이러한 쿠키를 사용하면 ID 서비스에서 다른 도메인의 방문자를 추적하고 다른 Experience Cloud 솔루션 간에 데이터 공유를 사용할 수 있습니다.
seo-title: 쿠키 및 Experience Cloud Identity 서비스
title: 쿠키 및 Experience Cloud Identity 서비스
uuid: c5cbd235-37ee-4605-8792-b1a991e190ad
translation-type: ht
source-git-commit: 7d7ecdf65cca67539b1b63c8811a0bad04c694c3

---


# 쿠키 및 Experience Cloud Identity 서비스{#cookies-and-the-experience-cloud-id-service}

이 ID 서비스는 조직 ID, Experience Cloud AMCV 쿠키 및 demdex 쿠키를 사용하여 사이트 방문자에 대한 고유하고 영구적인 식별자를 만들어 저장합니다. 이러한 쿠키를 사용하면 ID 서비스에서 다른 도메인의 방문자를 추적하고 다른 Experience Cloud 솔루션 간에 데이터 공유를 사용할 수 있습니다.

## ID 서비스 쿠키 이해 {#section-f438168beaec409ab8b2cc58bd021e26}

이 ID 서비스는 올바르게 작동하기 위해 AMCV, AMCVS 및 demdex 쿠키를 사용합니다. 이러한 쿠키는 ID 서비스에 사용된 데이터를 저장하는 파일입니다. 이러한 ID 서비스 쿠키는 위험하거나 악의적이지 않고, 브라우저의 서비스 또는 웹 사이트에 저장된 다른 자사 또는 타사 쿠키와 다르지 않으며, 자사 및 타사 쿠키를 제어하는 동일한 규칙을 따릅니다. ID 서비스에서 사용하는 쿠키에 대한 자세한 정보는 아래의 다음 섹션을 참조하십시오.

### ID 서비스 쿠키에서 수행할 수 있는 작업

* 사이트 방문자에 대한 고유한 ID(MID) 설정 및 저장.
* ID 서비스가 데이터를 수집하고 다른 Experience Cloud 솔루션과 공유할 수 있도록 이 고유한 ID 유지.
* 도메인에서 사용자 추적. 그러나 이 작업을 수행하려면 다른 도메인을 소유하고 있고 이 도메인에 ID 서비스 코드가 배포되어 있어야 합니다.

### ID 서비스 쿠키에서 수행할 수 없는 작업

* 컴퓨터 바이러스 저장, 전송 또는 실행.
* 이메일 주소와 같은 PII(개인식별정보)에 액세스 또는 저장.
* 컴퓨터 하드웨어 또는 소프트웨어 제어.
* 컴퓨터를 불안정하게 만들거나 성능 문제를 일으킴.
* ID 서비스를 사용하지 않는 사이트에서 사용자 추적.

## AMCV 쿠키 {#section-c55af54828dc4cce89f6118655d694c8}

ID 서비스에서 설정한 쿠키의 다음 특성입니다.

**이름**

AMCV 쿠키 이름은 `AMCV_<variable name>@AdobeOrg` 구문을 따릅니다. 이름에서 `<variable name>` 요소는 Experience Cloud 조직 ID 부분에 대한 자리 표시자입니다. 이 ID는 ID 서비스 코드에서 `Visitor.getInstance` 함수에 의해 DCS로 전달됩니다.

전체 형식의 쿠키 이름은 다음과 비슷합니다.

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**내용**

AMCV 쿠키에는 Experience Cloud 방문자 ID 또는 MID가 포함되어 있습니다. MID는 `mid|<Experience Cloud ID>` 구문 뒤에 오는 키-값 쌍에 저장됩니다.

전체 형식의 키-값 쌍은 다음과 비슷합니다.

```
mid|20265673158980419722735089753036633573
```

이 영구 식별자는 솔루션 간 데이터 공유를 가능하게 합니다.

**도메인**

AMCV 쿠키는 자사 브라우저의 도메인에 설정됩니다. 즉, 사용자가 현재 방문한 사이트 도메인에 설정됩니다. 따라서 ID 서비스 코드 및 기타 Experience Cloud 코드 라이브러리는 AMCV 쿠키에 저장된 MID를 읽을 수 있습니다.

그렇지만 AMCV 쿠키는 자사 도메인에 설정되므로 다른 도메인 간 사용자를 추적하고 식별하는 데는 사용할 수 없습니다. 대신, ID 서비스는 조직 ID 및 demdex ID에 의존하여 사이트 방문자가 다른 도메인으로 이동할 때 올바른 MID를 반환합니다.

## AMCVS 쿠키 {#section-92a9454f1ac645948f9059b9fad928bf}

**이름**

AMCVS 쿠키 이름은 `AMCVS_####@AdobeOrg` 구문을 따릅니다. 이름에서 #### 요소는 Experience Cloud 조직 ID 부분에 대한 자리 표시자입니다. 이 ID는 ID 서비스 코드에서 `theVisitor.getInstance` 함수에 의해 DCS로 전달됩니다.

전체 형식의 쿠키 이름은 다음과 비슷합니다.

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**내용**

AMCVS 쿠키는 세션이 초기화되었음을 나타내는 플래그로 사용됩니다. 이 값은 항상 `1`이며, 세션이 종료되면 중단됩니다.

**도메인**

AMCVS 쿠키는 자사 브라우저의 도메인에 설정됩니다. 즉, 사용자가 현재 방문한 사이트 도메인에 설정됩니다.

![](assets/AMCVS-cookie.png)

## Demdex 쿠키 {#section-7ff7d96d6e4141b08a84a75a63d7814c}

다음 표에는 demdex 쿠키의 중요한 몇 가지 속성과 속성에 대한 정의가 나와 있습니다.

<table id="table_18E3CAF3550E4BB6A199736AACE39202"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 특성 </th> 
   <th colname="col2" class="entry"> 설명 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>이름</b> </p> </td> 
   <td colname="col2"> <p>쿠키 이름은 "demdex"입니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>내용</b> </p> </td> 
   <td colname="col2"> <p>demdex 쿠키에는 DCS가 생성하는 demdex ID가 포함되어 있습니다. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>도메인</b> </p> </td> 
   <td colname="col2"> <p>demdex 쿠키는 브라우저의 타사 demdex.net 도메인에 설정됩니다. 이 도메인은 사용자가 현재 방문한 사이트와는 별개입니다. </p> <p>자사 AMCV 쿠키와 달리, demdex 쿠키 및 ID는 도메인이 달라져도 유지됩니다. demdex ID 및 조직 ID는 ID 서비스에서 올바른 방문자 ID를 가진 사이트 방문자를 반환하고 식별할 수 있는 공통 값입니다. </p> </td> 
  </tr> 
 </tbody> 
</table>

관련 정보는 [Demdex 도메인에 대한 호출 이해](https://marketing.adobe.com/resources/help/ko_KR/aam/demdex-calls.html)를 참조하십시오.

## Experience Cloud ID 생성 {#section-15f69c0bac394b4b9966a23fbc586d17}

Experience Cloud ID(MID)는 조직 ID 및 demdex ID에서 수학적으로 파생됩니다. 이러한 ID가 일관되게 유지되는 한, 특정 사용자에 대한 올바른 MID를 생성하는 것은 단순히 수학 문제에 불과합니다. 동일한 조직 ID 및 demdex ID를 사용할 경우 매번 동일한 MID 값을 얻게 됩니다. 이 경우 ID 서비스에서 사용자가 ID 서비스 코드를 사용하여 제어하고 구성한 도메인의 방문자를 추적할 수 있습니다.

ID 서비스는 페이지가 로드될 때 MID를 생성하기 시작합니다. 이 프로세스 중에 `visitorAPI.js` 코드 라이브러리에서 제공한 코드는 ID 서비스에 대한 이벤트 호출에 조직 ID를 보냅니다. ID 서비스에서 MID 및 demdex ID를 생성하고 각각 AMCV 및 demdex 쿠키에 반환합니다.

## 쿠키 플래그

다음 표에서는 Experience Cloud 쿠키의 플래그에 대해 설명합니다.

| 쿠키(설정) | httpOnly | Secure | SameSite |
|--- |--- |--- |--- |
| demdex(http 응답) | 아니요 | 예 | "없음" |
| AMCV(Javascript) | 아니요 | 구성 가능 | 설정 해제(기본값 Lax) |
| AMCVS(Javascript) | 아니요 | 구성 가능 | 설정 해제(기본값 Lax) |

*참고: 보안 속성으로 AMCV 및 AMCVS 쿠키를 구성하는 방법에 대한 자세한 내용은[secureCookie](https://docs.adobe.com/content/help/ko-KR/id-service/using/id-service-api/configurations/securecookie.html)항목을 참조하십시오.*

## 다음 단계 {#section-8db1727a63bc4ff68b495f270315d453}

[Experience Cloud Identity 서비스에서 ID를 요청하고 설정하는 방법...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)을 참조하십시오.
