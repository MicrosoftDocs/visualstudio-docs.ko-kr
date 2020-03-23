---
title: '시나리오: 시각화 및 모델링을 사용하여 설계 변경 | 마이크로 소프트 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70cc3c81c426ec55d0afb36360155786ec97d937
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301238"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>시나리오: 시각화 및 모델링을 사용하여 디자인 변경
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 시각화 및 모델링 도구를 사용하여 소프트웨어 시스템이 사용자의 요구를 충족하는지 확인합니다. UML(Unified Modeling Language) 다이어그램, 코드 맵, 레이어 다이어그램 및 클래스 다이어그램과 같은 도구를 사용하여 다음을 수행합니다.

 각 도구를 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

- 사용자의 요구 사항 및 비즈니스 프로세스를 분명하게 설명합니다.

- 기존 코드를 시각화하고 탐색합니다.

- 기존 시스템의 변경 내용을 설명합니다.

- 시스템이 요구 사항을 충족하는지 확인합니다.

- 코드와 디자인의 일관성을 유지합니다.

  이 연습의 내용은 다음과 같습니다.

- 어떻게 하면 이러한 도구를 소프트웨어 프로젝트에 유용하게 사용할 수 있는지 설명합니다.

- 개발 접근 방식과 관계없이 예제 시나리오에서 이러한 도구를 사용하는 방법을 보여 줍니다.

  이러한 도구 및 도구가 지원하는 시나리오에 대한 자세한 내용은 다음을 참조하세요.

- [아키텍처 분석 및 모델링](../modeling/analyze-and-model-your-architecture.md)

- [코드 시각화](../modeling/visualize-code.md)

- [앱용 모델 만들기](../modeling/create-models-for-your-app.md)

## <a name="scenario-overview"></a><a name="ScenarioOverview"></a>시나리오 개요
 이 시나리오에서는 Dinner Now 및 Lucerne Publishing이라는 가상 회사 두 개의 소프트웨어 개발 수명 주기에 따른 에피소드를 설명합니다. Dinner Now는 시애틀에서 웹 기반 음식 배달 서비스를 제공합니다. 고객은 Dinner Now 웹 사이트에서 음식을 주문하고 결제할 수 있습니다. 주문은 배달을 위해 해당 현지 음식점에 전송됩니다. 뉴욕에 있는 회사인 Lucerne Publishing은 오프라인과 온라인으로 여러 가지 비즈니스를 운영합니다. 예를 들어 고객이 음식점 리뷰를 게시할 수 있는 웹 사이트를 운영합니다.

 Lucerne은 최근에 Dinner Now를 인수했고, 다음과 같이 변경하고자 합니다.

- Dinner Now에 음식점 리뷰 기능을 추가하여 웹 사이트를 통합합니다.

- Dinner Now의 결제 시스템을 Lucerne 시스템으로 바꿉니다.

- 전체 지역으로 Dinner Now 서비스를 확장합니다.

  Dinner Now는 SCRUM 및 eXtreme 프로그래밍을 사용합니다. 강도 높은 테스트 검사를 수행하지만 지원되지 않는 코드가 거의 없습니다. 작지만 실제로 작동하는 시스템 버전을 만들고, 기능을 점차 추가하여 위험을 최소화합니다. 짧게 자주 반복하는 방식으로 코드를 개발합니다. 이를 통해 변경 사항을 자신 있게 포함하고, 코드를 자주 리팩터링하며, "BDUF(Big Design Up Front)"를 피합니다.

  Lucerne은 매우 크고 복잡한 시스템 모음을 유지 관리하며 시스템의 일부는 40년 이상 사용하고 있습니다. 레거시 코드의 복잡성과 범위 때문에 변경하는 데 매우 신중합니다. 더 철저한 개발 프로세스를 따르면서 기본적으로 세부 솔루션을 디자인하고 개발 중에 발생하는 디자인 및 변경을 문서화하고자 합니다.

  두 팀에서는 모두 사용자의 요구를 충족하는 시스템을 개발하도록 도와주는 Visual Studio의 모델링 다이어그램을 사용합니다. 작업을 계획, 구성 및 관리하도록 도와주는 다른 도구와 함께 Team Foundation Server를 사용합니다.

  Team Foundation Server에 대한 자세한 내용은 다음을 참조하세요.

- [작업 계획 및 추적](#PlanningTracking)

- [업데이트된 코드 테스트, 유효성 검사 및 체크 인](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a> 소프트웨어 개발에서 아키텍처 및 모델링 다이어그램의 역할
 다음 표에서는 소프트웨어 개발 수명 주기의 여러 다양한 단계에서 이들 도구가 수행할 수 있는 역할에 대해 설명합니다.

||**사용자 요구 사항 모델링**|**비즈니스 프로세스 모델링**|**시스템 아키텍처 및 디자인**|**코드 시각화 및 탐색**|**확인**|
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|
|사용 사례 다이어그램(UML)|√|√|||√|
|동작 다이어그램(UML)|√|√|√||√|
|클래스 다이어그램(UML)|√|√|√||√|
|구성 요소 다이어그램(UML)|√|√|√||√|
|시퀀스 다이어그램(UML)|√|√|√||√|
|DSL(도메인별 언어) 다이어그램|√|√|√|||
|레이어 다이어그램, 레이어 유효성 검사|||√|√|√|
|코드 맵|||√|√|√|
|클래스 디자이너(코드 기반)||||√||

 UML 다이어그램과 레이어 다이어그램을 그리려면 모델링 프로젝트를 기존 솔루션이나 새 솔루션의 파트로 만들어야 합니다. 이들 다이어그램은 모델링 프로젝트에서 만들어야 합니다. UML 다이어그램의 항목은 일반 모델의 파트고, UML 다이어그램은 해당 모델의 뷰입니다. 레이어 다이어그램의 항목은 모델링 프로젝트에 있지만 일반 모델에 저장되지 않습니다. 코드에서 생성된 코드 맵 및 .NET 클래스 다이어그램은 모델링 프로젝트 외부에 있습니다.

 다음을 참조하세요.

- [UML 모델링 프로젝트 및 다이어그램 만들기](../modeling/create-uml-modeling-projects-and-diagrams.md)

- [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)

- [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)

- [방법: 프로젝트에 클래스 다이어그램 추가(클래스 디자이너)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [Visual Studio용 모델링 SDK - 도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

  아키텍처의 대체 뷰를 표시하기 위해 서로 다른 여러 다이어그램에서 같은 모델의 특정 요소를 다시 사용할 수 있습니다. 예를 들어 행위자로 작동할 수 있도록 구성 요소를 다른 구성 요소 다이어그램 또는 시퀀스 다이어그램으로 끌 수 있습니다. [UML 모델 및 다이어그램 편집을](../modeling/edit-uml-models-and-diagrams.md)참조하십시오.

  두 팀에서는 모두 레이어 유효성 검사를 사용하여 개발 중인 코드와 디자인의 일관성이 유지되는지 확인합니다.

  다음을 참조하세요.

- [코드와 디자인에 일관성 유지](#ValidatingCode)

- [논리적 아키텍처 설명: 레이어 다이어그램](#DescribeLayers)

- [레이어 다이어그램에 대해 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)

  > [!NOTE]
  > 일부 Visual Studio 버전에서는 시각화 및 모델링을 위해 코드 맵과 UML 다이어그램의 레이어 유효성 검사 및 읽기 전용 버전을 지원합니다. 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="understanding-and-communicating-information-about-the-system"></a><a name="UnderstandingCommunicating"></a> 시스템에 대한 정보 이해 및 전달
 Visual Studio 모델링 다이어그램을 사용하는 데는 미리 정의된 순서가 없으므로 요구나 접근 방식에 맞게 사용할 수 있습니다. 일반적으로 팀에서는 프로젝트 내내 모델을 반복적으로 자주 다시 확인합니다. 각 다이어그램은 개발 중인 시스템의 다양한 측면을 이해, 설명 및 전달하도록 도와주는 특정 기능을 제공합니다.

 Dinner Now 및 Lucerne은 다이어그램을 공통 언어로 사용하여 서로 소통하고 프로젝트 이해 관계자와 소통합니다. 예를 들어 Dinner Now는 다이어그램을 사용하여 다음 작업을 수행합니다.

- 기존 코드를 시각화합니다.

- 신규 또는 업데이트된 사용자 스토리에 대해 Lucerne과 소통합니다.

- 신규 또는 업데이트된 사용자 스토리를 지원하는 데 필요한 변경 사항을 파악합니다.

  Lucerne은 다이어그램을 사용하여 다음 작업을 수행합니다.

- Dinner Now의 비즈니스 프로세스를 알아봅니다.

- 시스템 디자인을 이해합니다.

- 신규 또는 업데이트된 사용자 요구 사항에 대해 Dinner Now와 소통합니다.

- 시스템에 대한 업데이트를 문서화합니다.

  다이어그램은 Team Foundation Server와 통합되므로 팀에서는 작업을 더 쉽게 계획, 관리 및 추적할 수 있습니다. 예를 들어 모델을 사용하여 테스트 사례 및 개발 작업을 식별하고 작업을 예측합니다. Lucerne은 Team Foundation Server 작업 항목을 모델 요소에 연결하여 진행 상황을 모니터링하고 시스템이 사용자 요구 사항을 충족하는지 확인할 수 있습니다. 예를 들어 사용 사례를 테스트 사례 작업 항목에 연결하여 모든 테스트를 통과할 때 사용 사례가 처리되는지 확인할 수 있습니다.

  팀에서는 변경 내용을 체크 인하기 전에 레이어 유효성 검사 및 자동화된 테스트를 포함하는 빌드를 실행하여 테스트 및 디자인에 대해 코드의 유효성을 검사합니다. 이렇게 하면 업데이트된 코드가 디자인과 충돌하지 않고 코드로 인해 이전에 작동한 기능이 중단되지 않는지 확인할 수 있습니다.

  다음을 참조하세요.

- [비즈니스 프로세스에서 시스템 역할 이해](#UnderstandingBPMandSystemDesign)

- [신규 또는 업데이트된 사용자 요구 사항 설명](#DescribingURM)

- [모델에서 테스트 만들기](#CreatingTests)

- [기존 시스템의 변경 사항 식별](#DeterminingChanges)

- [Keeping code consistent with the design](#ValidatingCode)

- [모델 작성 및 사용에 대한 일반적인 팁](#GeneralTips)

- [작업 계획 및 추적](#PlanningTracking)

- [업데이트된 코드 테스트, 유효성 검사 및 체크 인](#TestValidateCheckInCode)

### <a name="understanding-the-role-of-the-system-in-the-business-process"></a><a name="UnderstandingBPMandSystemDesign"></a>비즈니스 프로세스에서 시스템의 역할 이해
 Lucerne은 Dinner Now의 비즈니스 프로세스를 자세히 알아보고자 합니다. 다음 다이어그램을 만들어 Dinner Now의 현재 상태를 더 쉽고 분명하게 설명합니다.

|**다이어그램**|**설명 내용**|
|-----------------|-------------------|
|*사용 사례 다이어그램(UML)*<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)|- 디너 나우 시스템이 지원하는 활동<br />- 활동을 수행하는 사람 및 외부 시스템<br />- 각 활동을 지원하는 시스템의 주요 구성 요소<br />- 현재 시스템의 범위를 벗어난 비즈니스 프로세스의 일부(예: 음식 배달)|
|*동작 다이어그램(UML)*<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 활동 다이어그램: 참조](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML 활동 다이어그램: 지침](../modeling/uml-activity-diagrams-guidelines.md)|고객이 주문을 만들 때 발생하는 단계 흐름|
|*클래스 다이어그램(UML)*<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)|논의에 사용되는 비즈니스 엔터티와 용어 및 해당 엔터티 간 관계. 예를 들어, 주문 및 메뉴 항목은 이 시나리오에서 어휘 부분입니다.|

 예를 들어 Lucerne은 다음 사용 사례 다이어그램을 만들어서 Dinner Now 웹 사이트에서 수행되는 작업 및 작업을 수행하는 사람을 파악합니다.

 ![UML 사용 사례 다이어그램](../modeling/media/uml-usecase.png "UML_UseCase")

 **UML 사용 사례 다이어그램**

 다음 동작 다이어그램에서는 고객이 Dinner Now 웹 사이트에서 주문을 만들 때 발생하는 단계 흐름을 설명합니다. 이 릴리스에서 주석 요소는 역할을 식별하고 선은 역할별 단계를 구성하는 *스윔 레인*을 만듭니다.

 ![UML 활동 다이어그램](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")

 **UML 활동 다이어그램**

 다음 클래스 다이어그램에서는 주문 프로세스에 참가하는 엔터티를 설명합니다.

 ![UML 클래스 다이어그램](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")

 **UML 클래스 다이어그램**

### <a name="describing-new-or-updated-user-requirements"></a><a name="DescribingURM"></a>신규 또는 업데이트된 사용자 요구 사항 설명
 Lucerne은 고객이 음식점 리뷰를 읽고 게시할 수 있도록 Dinner Now 시스템에 기능을 추가하고자 합니다. Dinner Now와 함께 이 새로운 요구 사항을 설명하고 논의할 수 있도록 다음 다이어그램을 업데이트합니다.

|**다이어그램**|**설명 내용**|
|-----------------|-------------------|
|*사용 사례 다이어그램(UML)*<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)|"음식점 리뷰 쓰기"에 대한 새 사용 사례|
|*동작 다이어그램(UML)*<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 활동 다이어그램: 참조](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML 활동 다이어그램: 지침](../modeling/uml-activity-diagrams-guidelines.md)|고객이 음식점 리뷰를 쓰려고 할 때 발생하는 단계|
|*클래스 다이어그램(UML)*<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)|리뷰를 저장하는 데 필요한 데이터|

 예를 들어 다음 사용 사례 다이어그램에는 새 요구 사항을 나타내기 위한 새 "리뷰 쓰기" 사용 사례가 포함됩니다. 더 쉽게 식별할 수 있도록 이 사용 사례는 다이어그램에서 주황색으로 강조 표시됩니다.

 ![UML 사용 사례 다이어그램](../modeling/media/uml-writerev.png "UML_WriteRev")

 **UML 사용 사례 다이어그램**

 다음 동작 다이어그램에는 새 사용 사례의 단계 흐름을 설명하기 위해 새 요소가 주황색으로 표시됩니다.

 ![UML 활동 다이어그램](../modeling/media/uml-writereview.png "UML_WriteReview")

 **UML 활동 다이어그램**

 다음 클래스 다이어그램에는 팀에서 세부 정보를 논의할 수 있도록 새 리뷰 클래스 및 이 클래스와 다른 클래스의 관계가 포함됩니다. 고객 및 음식점에는 여러 리뷰가 포함될 수 있습니다.

 ![UML 클래스 다이어그램](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")

 **UML 클래스 다이어그램**

### <a name="creating-tests-from-models"></a><a name="CreatingTests"></a>모델에서 테스트 만들기
 두 팀에서는 모두 변경하기 전에 시스템 및 해당 구성 요소에 대한 전체 테스트가 필요하다는 데 동의합니다. Lucerne에는 시스템 및 구성 요소 수준 테스트를 수행하는 특수 팀이 있습니다. Dinner Now에서 만든 테스트를 다시 사용하고 UML 다이어그램을 사용하여 해당 테스트를 구성합니다.

- 각 사용 사례는 하나 이상의 테스트로 표현됩니다. 사용 사례 다이어그램의 요소는 Team Foundation Server의 테스트 사례 작업 항목에 연결됩니다.

- 동작 다이어그램 또는 시스템 수준 시퀀스 다이어그램의 각 흐름은 하나 이상의 테스트에 연결됩니다. 테스트 팀에서는 동작 다이어그램을 통해 가능한 모든 경로를 테스트하는지 체계적으로 확인합니다.

- 테스트를 설명하는 데 사용된 용어는 사용 사례, 클래스 및 동작 다이어그램에 정의된 용어를 기준으로 합니다.

  요구 사항이 변경되고 다이어그램이 업데이트되어 해당 변경 내용을 반영하면 테스트도 업데이트됩니다. 요구 사항은 테스트에 통과할 때만 충족된 것으로 간주합니다. 가능하거나 적합할 경우 테스트는 구현이 시작되기 전에 정의되며 UML 다이어그램을 기반으로 합니다.

  다음을 참조하세요.

- [모델에서 테스트 개발](../modeling/develop-tests-from-a-model.md)

- [UML 모델 유효성 검사](../modeling/validate-your-uml-model.md)

### <a name="identifying-changes-to-the-existing-system"></a><a name="DeterminingChanges"></a> Identifying Changes to the Existing System
 Dinner Now는 새 요구 사항을 충족하기 위한 비용을 예측해야 합니다. 비용은 부분적으로 이 변경이 시스템의 다른 부분에 얼마나 영향을 미치는지에 따라 달라집니다. 이 흐름을 이해하는 데 도움이 되도록 Dinner Now 개발자 한 명이 기존 코드에서 다음 맵 및 다이어그램을 만듭니다.

|**맵 또는 다이어그램**|**보여 줍니다**|
|------------------------|---------------|
|*코드 맵*<br /><br /> 다음을 참조하세요.<br /><br /> -   [솔루션 전반에 걸쳐 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)<br />-   [코드 맵 찾아보기 및 재정렬](../modeling/browse-and-rearrange-code-maps.md)<br />-   [DGML 파일을 편집하여 코드 맵 사용자 지정](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|코드의 종속성 및 기타 관계.<br /><br /> 예를 들어 Dinner Now는 어셈블리 및 해당 종속성을 살펴보기 위해 먼저 어셈블리 코드 맵을 검토할 수 있습니다. 맵을 분석하여 해당 어셈블리의 네임스페이스 및 클래스를 살펴볼 수 있습니다.<br /><br /> Dinner Now에서 맵을 만들어서 코드의 특정 영역 및 다른 관계 종류를 살펴볼 수도 있습니다. 솔루션 탐색기를 사용하여 관심 있는 영역 및 관계를 찾고 선택합니다.|
|*코드 기반 클래스 다이어그램*<br /><br /> [방법: 프로젝트에 클래스 다이어그램 추가(클래스 디자이너)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)을 참조하세요.|코드의 기존 클래스|

 예를 들어 개발자는 코드 맵을 만듭니다. 범위를 조정하여 새 시나리오가 영향을 미치는 영역에 초점을 맞춥니다. 맵에서 다음 영역이 선택되고 강조 표시됩니다.

 ![네임스페이스 종속성 그래프](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")

 **네임스페이스 코드 맵**

 개발자는 선택된 네임스페이스를 확장하여 클래스, 메서드 및 관계를 표시합니다.

 ![확장된 네임스페이스 종속성 그래프](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")

 **그룹 간 링크가 표시된 확장된 네임스페이스 코드 맵**

 개발자는 코드를 검사하여 영향을 받는 클래스 및 메서드를 찾습니다. 변경할 때 각 변경이 미치는 영향을 확인하기 위해 각 변경 후에 코드 맵을 다시 생성합니다. [코드 시각화를](../modeling/visualize-code.md)참조하십시오.

 구성 요소 또는 상호 작용과 같은 시스템의 다른 부분에 대한 변경 내용을 설명하기 위해 팀에서는 화이트보드에 이들 요소를 그릴 수 있습니다. 두 팀 모두가 세부 정보를 캡처, 관리 및 이해할 수 있도록 Visual Studio에서 다음 다이어그램을 그릴 수도 있습니다.

|**다이어그램**|**설명 내용**|
|------------------|-------------------|
|*동작 다이어그램(UML)*<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 활동 다이어그램: 참조](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML 활동 다이어그램: 지침](../modeling/uml-activity-diagrams-guidelines.md)|고객이 음식점에서 다시 주문했다는 것을 시스템에서 인식하여 고객에게 리뷰를 쓰도록 요청하는 메시지를 표시할 때 발생하는 단계 흐름.|
|*클래스 다이어그램(UML)*<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)|논리 클래스 및 해당 관계. 예를 들어 **리뷰** 및 해당 리뷰와 **음식점**, **메뉴**, **고객**등 다른 엔터티와의 관계를 설명하는 새 클래스가 추가됩니다.<br /><br /> 리뷰를 고객과 연결하려면 시스템에서 고객 세부 정보를 저장해야 합니다. UML 클래스 다이어그램을 통해 해당 세부 정보를 명확하게 설명할 수 있습니다.|
|*코드 기반 클래스 다이어그램*<br /><br /> [방법: 프로젝트에 클래스 다이어그램 추가(클래스 디자이너)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)을 참조하세요.|코드의 기존 클래스.|
|*구성 요소 다이어그램(UML)*<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)<br />-   [UML 구성 요소 다이어그램: 지침](../modeling/uml-component-diagrams-guidelines.md)|Dinner Now 웹 사이트 및 해당 인터페이스와 같은 시스템의 상위 파트. 이들 인터페이스는 인터페이스에서 제공 및 사용되는 메서드 또는 서비스를 통해 구성 요소가 서로 상호 작용하는 방식을 정의합니다.|
|*시퀀스 다이어그램(UML)*<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML 시퀀스 다이어그램: 지침](../modeling/uml-sequence-diagrams-guidelines.md)|인스턴스 간 상호 작용의 시퀀스.|

 예를 들어 다음 구성 요소 다이어그램에서는 Dinner Now 웹 사이트 구성 요소의 파트인 새 구성 요소를 보여 줍니다. ReviewProcessing 구성 요소는 리뷰를 만드는 기능을 처리하며 주황색으로 강조 표시됩니다.

 ![UML 구성 요소 다이어그램](../modeling/media/uml-internal.png "UML_Internal")

 **UML 구성 요소 다이어그램**

 다음 시퀀스 다이어그램에서는 Dinner Now 웹 사이트에서 고객이 이전에 음식점에서 주문했는지를 확인할 때 발생하는 상호 작용의 시퀀스를 보여 줍니다. 이전에 주문했다면 음식점에 전송되고 웹 사이트에 게시되는 리뷰를 작성할지 고객에게 묻습니다.

 ![UML 시퀀스 다이어그램](../modeling/media/uml-revsystem.png "UML_RevSystem")

 **UML 시퀀스 다이어그램**

### <a name="keeping-code-consistent-with-the-design"></a><a name="ValidatingCode"></a>코드와 디자인에 일관성 유지
 Dinner Now는 업데이트된 코드와 디자인의 일관성이 유지되는지 확인해야 합니다. 시스템의 기능 레이어를 설명하는 레이어 다이어그램을 만들고, 레이어 간에 허용되는 종속성을 지정하고, 솔루션 아티팩트를 해당 레이어에 연결합니다.

|**다이어그램**|**설명 내용**|
|-----------------|-------------------|
|*레이어 다이어그램*<br /><br /> 다음을 참조하세요.<br /><br /> -   [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [레이어 다이어그램: 참조](../modeling/layer-diagrams-reference.md)<br />-   [레이어 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)<br />-   [레이어 다이어그램을 통해 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)|코드의 논리적 아키텍처.<br /><br /> 레이어 다이어그램에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션에서 아티팩트를 구성하고 *레이어*라는 추상 그룹에 매핑합니다. 이들 레이어는 아티팩트가 시스템에서 수행하는 역할, 작업 또는 기능을 식별합니다.<br /><br /> 레이어 다이어그램은 의도한 시스템 디자인을 설명하고 해당 디자인에 대해 발전하는 코드의 유효성을 검사하는 데 유용합니다.<br /><br /> 레이어를 만들려면 솔루션 탐색기, 코드 맵, 클래스 뷰 및 개체 브라우저에서 항목을 끌어옵니다. 새 레이어를 그리려면 도구 상자를 사용하거나 다이어그램 곡면을 마우스 오른쪽 단추로 클릭합니다.<br /><br /> 기존 종속성을 보려면 레이어 다이어그램 곡면을 마우스 오른쪽 단추로 클릭하고 **종속성 생성**을 클릭합니다. 의도한 종속성을 지정하려면 새 종속성을 그립니다.|

 예를 들어 다음 레이어 다이어그램에서는 레이어 간 종속성 및 각 레이어와 연결된 아티팩트 수를 설명합니다.

 ![통합 지불 시스템의 레이어 다이어그램](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **레이어 다이어그램**

 코드 개발 중에 디자인 충돌이 발생하지 않는지 확인하기 위해 팀에서는 Team Foundation Build에서 실행되는 빌드에 대해 레이어 유효성 검사를 사용합니다. 또한 사용자 지정 MSBuild 작업을 만들어서 체크 인 작업에서 레이어 유효성 검사를 요구합니다. 빌드 보고서를 사용하여 유효성 검사 오류를 수집합니다.

 다음을 참조하세요.

- [빌드 프로세스 정의](https://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)

- [제어된 체크 인 빌드 프로세스를 사용하여 변경 내용 유효성 검사](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)

- [빌드 프로세스 템플릿 사용자 지정](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

### <a name="general-tips-for-creating-and-using-models"></a><a name="GeneralTips"></a> General Tips for Creating and Using Models

- 대부분 다이어그램은 선으로 연결된 노드로 구성됩니다. 각 다이어그램 유형에 대한 도구 상자에서는 다양한 도구 및 선을 제공합니다.

   도구 상자를 열려면 **보기** 메뉴에서 **도구 상자**를 클릭합니다.

- 노드를 만들려면 도구 상자에서 다이어그램으로 노드를 끌어옵니다. 특정 노드 종류는 기존 노드에 끌어서 놓아야 합니다. 예를 들어 구성 요소 다이어그램에서 새 포트는 기존 구성 요소에 추가해야 합니다.

- 선 또는 연결을 만들려면 도구 상자에서 해당 도구를 클릭하고 소스 노드, 대상 노드를 차례로 클릭합니다. 일부 선은 특정 노드 종류 사이에서만 만들 수 있습니다. 포인터를 가능한 소스 또는 대상 위로 이동하면 포인터가 연결을 만들 수 있는지 여부를 표시합니다.

- UML 다이어그램에서 항목을 만들면 해당 항목이 일반 모델에도 추가됩니다. 모델링 프로젝트의 UML 다이어그램은 해당 모델의 뷰입니다. 레이어 다이어그램의 항목은 일반 모델에 저장되지 않더라도 모델링 프로젝트에 포함됩니다.

   모델을 확인하려면 **아키텍처** 메뉴에서  **Windows**를 가리키고 **UML 모델 탐색기**를 클릭합니다.

- 경우에 따라 특정 항목을 **UML 모델 탐색기** 에서 UML 다이어그램에 끌어서 놓을 수 있습니다. 아키텍처의 대체 뷰를 표시하기 위해 같은 모델 내의 일부 요소가 서로 다른 여러 다이어그램에서 사용될 수 있습니다. 예를 들어 행위자로 사용할 구성 요소를 다른 구성 요소 다이어그램 또는 시퀀스 다이어그램으로 끌 수 있습니다.

- Visual Studio에서는 UML 2.1.2를 지원합니다. 이 개요에서는 이 릴리스의 UML 다이어그램에 대한 주요 기능만 설명하지만 UML 및 해당 사용에 대해 자세히 설명하는 다양한 문서가 있습니다.

  [앱에 대한 모델 만들기를](../modeling/create-models-for-your-app.md)참조하십시오.

### <a name="planning-and-tracking-work"></a><a name="PlanningTracking"></a>작업 계획 및 추적
 Visual Studio 모델링 다이어그램은 Team Foundation Server와 통합되므로 작업을 더 쉽게 계획, 관리 및 추적할 수 있습니다. 두 팀에서는 모두 모델을 사용하여 테스트 사례 및 개발 작업을 식별하고 작업을 예측합니다. Lucerne은 Team Foundation Server 작업 항목을 만들고 사용 사례 및 구성 요소 등의 모델 요소에 연결합니다. 이렇게 하면 진행 상황을 모니터링하고 작업을 다시 사용자 요구 사항에 맞춰 추적할 수 있습니다. 이를 통해 변경 내용이 해당 요구 사항을 계속 충족하는지 확인할 수 있습니다.

 작업이 진행됨에 따라 팀에서는 작업 항목을 업데이트하여 작업에 걸린 시간을 반영합니다. 다음 Team Foundation Server 기능을 사용하여 작업 상태를 모니터링 및 보고합니다.

- 일일 *번다운(Burndown) 보고서* - 계획된 작업을 예상 시간 안에 완료할지를 보여 줍니다. Team Foundation Server에서 기타 비슷한 보고서를 생성하여 버그 진행 상황을 추적합니다.

- *반복 워크시트* - Microsoft Excel을 사용하여 팀에서 구성원 간의 작업 부하를 모니터링하고 균형을 맞추도록 도와줍니다. 이 워크시트는 Team Foundation Server에 연결되고 정기적인 진행 회의 중에 논의할 중점 사안을 제공합니다.

- *개발 대시보드* - Office Project를 사용하여 중요한 프로젝트 정보를 팀에 지속적으로 제공합니다.

  다음을 참조하세요.

- [Visual Studio Team Services 또는 Team Foundation Server를 사용하여 작업 추적](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)

- [모델 요소 및 작업 항목 연결](../modeling/link-model-elements-and-work-items.md)

- [Visual Studio ALM용 차트, 대시보드 및 보고서](https://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)

- [Project를 사용하여 백로그 및 작업 만들기](https://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)

### <a name="testing-validating-and-checking-in-code"></a><a name="TestValidateCheckInCode"></a> 코드 테스트, 유효성 검사 및 체크 인
 팀에서 각 작업을 완료하면 코드를 Team Foundation 버전 제어에 체크 인하고 잊지 않도록 Team Foundation Server에서 미리 알림을 수신합니다. Team Foundation Server가 체크 인을 승인하기 전에 팀에서는 단위 테스트 및 레이어 유효성 검사를 실행하여 테스트 사례 및 디자인에 대해 코드를 확인합니다. Team Foundation Server를 사용하여 빌드, 자동화된 단위 테스트 및 레이어 유효성 검사를 정기적으로 실행합니다. 이렇게 하면 코드가 다음 기준을 충족하는지 확인할 수 있습니다.

- 예상대로 작동합니다.

- 이전에 작동한 코드가 중단되지 않습니다.

- 디자인과 충돌하지 않습니다.

  Dinner Now의 자동화된 대규모 테스트 컬렉션은 지금도 거의 모두 적용되고 있기 때문에 Lucerne이 다시 사용할 수 있습니다. Lucerne은 이들 테스트를 기반으로 빌드하고 새 기능을 다루는 새 테스트를 추가할 수 있습니다. 두 팀에서는 모두 Visual Studio를 사용한 수동 테스트도 실행합니다.

  코드가 디자인을 따르는지 확인하기 위해 팀에서는 Team Foundation Build에서 해당 빌드를 구성하여 레이어 유효성 검사를 포함합니다. 충돌이 발생하면 세부 정보가 포함된 보고서가 생성됩니다.

  다음을 참조하세요.

- [애플리케이션 테스트](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)

- [개발하는 동안 시스템 유효성 검사](../modeling/validate-your-system-during-development.md)

- [사용자 버전 제어](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [응용 프로그램 빌드](/azure/devops/pipelines/index)

## <a name="updating-the-system-using-visualization-and-modeling"></a><a name="UpdatingSystem"></a> Updating the System Using Visualization and Modeling
 Lucerne과 Dinner Now는 결제 시스템을 통합해야 합니다. 다음 섹션에서는 이 작업을 하는 데 도움이 되는 Visual Studio의 모델링 다이어그램을 보여 줍니다.

- [사용자 요구 사항 이해: 사용 사례 다이어그램](#UnderstandUseCases)

- [비즈니스 프로세스 이해: 동작 다이어그램](#UnderstandActivities)

- [시스템 구조 설명: 구성 요소 다이어그램](#DescribeComponents)

- [상호 작용 설명: 시퀀스 다이어그램](#DescribeSequence)

- [기존 코드 시각화: 코드 맵](#VisualizeCode)

- [형식 용어집 정의: 클래스 다이어그램](#DefineClasses)

- [논리적 아키텍처 설명: 레이어 다이어그램](#DescribeLayers)

  다음을 참조하세요.

- [앱용 모델 만들기](../modeling/create-models-for-your-app.md)

- [코드 시각화](../modeling/visualize-code.md)

- [개발 프로세스에서 모델 사용](../modeling/use-models-in-your-development-process.md)

- [사용자 요구 사항 모델링](../modeling/model-user-requirements.md)

- [앱의 아키텍처 모델링](../modeling/model-your-app-s-architecture.md)

### <a name="understand-the-user-requirements-use-case-diagrams"></a><a name="UnderstandUseCases"></a>사용자 요구 사항 이해: 사용 사례 다이어그램
 사용 사례 다이어그램에서는 시스템에서 지원하는 동작 및 해당 동작을 수행하는 사람을 간략히 설명합니다. Lucerne은 사용 사례 다이어그램을 사용하여 Dinner Now 시스템에 대한 다음 정보를 알아봅니다.

- 고객이 주문을 작성합니다.

- 음식점이 주문을 받습니다.

- Dinner Now 결제 시스템에서 결제 유효성을 검사하는 데 사용하는 외부 결제 프로세서 게이트웨이는 웹 사이트 범위를 벗어납니다.

  다이어그램에는 일부 주요 사용 사례가 더 작은 사용 사례로 어떻게 나뉘는지도 보여 줍니다. Lucerne은 자체 결제 시스템을 사용하고자 합니다. 변경이 필요함을 나타내려고 Process Payment 사용 사례를 다른 색으로 강조 표시합니다.

  ![사용 사례 다이어그램에서 Process Payment 강조 표시](../modeling/media/uml-processpay.png "UML_ProcessPay")

  **사용 사례 다이어그램에서 Process Payment 강조 표시**

  개발 기간이 짧으면 팀에서 고객이 음식점에 직접 결제하게 할지를 논의할 수 있습니다. 이를 표시하기 위해 Process Payment 사용 사례를 Dinner Now 시스템 경계를 벗어난 사용 사례로 바꿉니다. 그리고 고객을 직접 음식점에 연결하여 Dinner Now가 주문 처리만 수행한다는 것을 나타냅니다.

  ![사용 사례 다이어그램의 식당 지불 범위 조정](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")

  **사용 사례 다이어그램의 식당 지불 범위 조정**

  다음을 참조하세요.

- [UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)

- [UML 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="drawing-a-use-case-diagram"></a>사용 사례 다이어그램 그리기
 사용 사례 다이어그램의 주요 기능은 다음과 같습니다.

- *행위자* 는 개인, 조직, 컴퓨터 또는 소프트웨어 시스템이 수행하는 역할을 나타냅니다. 예를 들어 고객, 음식점 및 Dinner Now 결제 시스템은 행위자입니다.

- *사용 사례* 는 행위자와 개발 중인 시스템 간 상호 작용을 나타냅니다.  단일 마우스 클릭 또는 메시지부터 여러 날 이상 연장되는 트랜잭션까지 모든 규모의 상호 작용을 나타낼 수 있습니다.

- *연결* 은 행위자를 사용 사례에 연결합니다.

- 더 큰 사용 사례에는 더 작은 사용 사례가 *포함* 될 수 있습니다. 예를 들어 주문 작성에는 음식점 선택이 포함됩니다. 사용 사례를 *확장* 하고, 목표 단계를 확장된 사용 사례에 추가하여 사용 사례가 특정 조건에서만 발생하도록 지정할 수 있습니다. 사용 사례가 서로 상속할 수도 있습니다.

- *하위 시스템* 은 개발 중인 소프트웨어 시스템 또는 해당 구성 요소 하나를 나타냅니다. 사용 사례를 포함하는 큰 상자입니다. 사용 사례 다이어그램에서는 하위 시스템 경계 내부 또는 외부에 있는 항목을 분명히 설명합니다. 사용자가 특정 목표를 다른 방법으로 달성하도록 지정하려면 해당 사용 사례를 하위 시스템 경계 외부에서 그립니다.

- *아티팩트* 는 다이어그램의 요소를 다른 다이어그램 또는 문서에 연결합니다.

  다음을 참조하세요.

- [UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)

- [UML 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="summary-strengths-of-use-case-diagrams"></a>요약: 사용 사례 다이어그램의 장점
 사용 사례 다이어그램을 통해 시각화할 수 있는 것은 다음과 같습니다.

- 시스템이 지원하거나 지원하지 않는 동작

- 해당 동작을 수행하는 사람 및 외부 시스템

- 부모 시스템 내부에 중첩된 하위 시스템으로 표현할 수 있는 각 동작을 지원하는 시스템의 주요 구성 요소

- 사용 사례를 더 작은 사용 사례 또는 변형으로 나누는 방법

#### <a name="relationship-to-other-diagrams"></a>다른 다이어그램과의 관계

|**다이어그램**|**설명 내용**|
|-----------------|-------------------|
|동작 다이어그램|사용 사례의 단계 흐름 및 해당 동작을 수행하는 주체.<br /><br /> 사용 사례 이름은 보통 동작 다이어그램의 단계를 그대로 반영합니다. 동작 다이어그램에서는 의사 결정, 병합, 입력 및 출력, 동시 흐름 등의 요소를 지원합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 활동 다이어그램: 참조](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML 활동 다이어그램: 지침](../modeling/uml-activity-diagrams-guidelines.md)|
|시퀀스 다이어그램|사용 사례의 참가자 간 상호 작용 시퀀스.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML 시퀀스 다이어그램: 지침](../modeling/uml-sequence-diagrams-guidelines.md)|
|클래스 다이어그램(UML)|사용 사례에 참가하는 엔터티 또는 형식.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)|

### <a name="understand-the-business-process-activity-diagrams"></a><a name="UnderstandActivities"></a>비즈니스 프로세스 이해: 활동 다이어그램
 동작 다이어그램에서는 비즈니스 프로세스의 단계 흐름을 설명하고 워크플로를 전달하는 간단한 방법을 제공합니다. 개발 프로젝트에는 여러 동작 다이어그램이 포함될 수 있습니다. 일반적으로 동작은 음식 주문, 메뉴 업데이트 또는 비즈니스에 새 음식점 추가 등의 외부 작업 하나에서 발생하는 모든 작업을 포함합니다. 동작은 복잡한 작업의 세부 정보도 설명합니다.

 Lucerne은 다음 동작 다이어그램을 업데이트하여 Lucerne이 결제를 처리하고 음식점에 대금을 지급한다는 것을 보여 줍니다. 강조 표시된 대로 Dinner Now 결제 시스템을 Lucerne 결제 시스템으로 바꿉니다.

 ![동작 다이어그램의 Lucerne 지불 시스템](../modeling/media/uml-lucerne.png "UML_Lucerne")

 **동작 다이어그램에서 Dinner Now 결제 시스템 바꾸기**

 업데이트된 다이어그램을 통해 Lucerne과 Dinner Now는 Lucerne 결제 시스템이 비즈니스 프로세스에 채택된 위치를 시각화합니다. 이 릴리스에서 주석은 단계를 수행하는 역할을 식별하는 데 사용됩니다. 선은 역할별 단계를 구성하는 *스윔 레인*을 만드는 데 사용됩니다.

 팀에서는 고객이 대신 주문이 배달된 후에 음식점에 결제하는 대체 스토리를 논의해 볼 수 있습니다. 이렇게 하면 소프트웨어 시스템에 대한 다른 요구 사항이 발생합니다.

 이전에 Dinner Now는 이들 다이어그램을 화이트보드나 PowerPoint에 그렸습니다. 현재는 팀에서 세부 정보를 캡처, 이해 및 관리할 수 있도록 Visual Studio를 사용하여 이들 다이어그램을 그립니다.

 다음을 참조하세요.

- [UML 동작 다이어그램: 참조](../modeling/uml-activity-diagrams-reference.md)

- [UML 동작 다이어그램: 지침](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="drawing-an-activity-diagram"></a>동작 다이어그램 그리기
 동작 다이어그램의 주요 기능은 다음과 같습니다.

- *초기 노드* - 동작의 첫 번째 작업을 나타냅니다.

   다이어그램에는 항상 이러한 노드 하나가 있어야 합니다.

- *작업* - 사용자 또는 소프트웨어가 작업을 수행하는 단계를 설명합니다.

- *제어 흐름* - 작업 간 흐름을 보여 줍니다.

- *의사 결정 노드* - 흐름에서 조건부 분기를 나타냅니다.

- *분기 노드* - 단일 흐름을 동시 흐름으로 나눕니다.

- *동작 최종 노드* - 동작의 끝을 보여 줍니다.

   이들 노드는 선택 사항이지만 다이어그램에 포함하면 동작이 끝나는 위치를 표시할 수 있습니다.

  다음을 참조하세요.

- [UML 동작 다이어그램: 참조](../modeling/uml-activity-diagrams-reference.md)

- [UML 동작 다이어그램: 지침](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="summary-strengths-of-activity-diagrams"></a>요약: 동작 다이어그램의 장점
 동작 다이어그램을 통해 비즈니스, 시스템 또는 프로그램의 작업 간의 제어 흐름 및 정보를 시각화하고 설명할 수 있습니다. 이 간단하고 유용한 방법으로 다른 사용자와 소통할 때 워크플로를 설명합니다.

#### <a name="relationship-to-other-diagrams"></a>다른 다이어그램과의 관계

|**다이어그램**|**설명**|
|-----------------|---------------------|
|사용 사례 다이어그램|각 행위자가 수행하는 동작을 요약합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)|
|구성 요소 다이어그램|잘 정의된 인터페이스 집합을 통해 동작을 제공하거나 사용하는 재사용 가능한 파트 컬렉션으로 시스템을 시각화합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)<br />-   [UML 구성 요소 다이어그램: 지침](../modeling/uml-component-diagrams-guidelines.md)|

### <a name="describe-the-system-structure-component-diagrams"></a><a name="DescribeComponents"></a>시스템 구조 설명: 구성 요소 다이어그램
 구성 요소 다이어그램에서는 시스템을 잘 정의된 인터페이스 집합을 통해 동작을 제공하거나 사용하는 분리 가능한 파트 컬렉션으로 설명합니다. 파트는 크기에 제한이 없고 모든 방식으로 연결될 수 있습니다.

 Lucerne과 Dinner Now는 시스템 구성 요소 및 해당 인터페이스를 시각화하고 이에 대해 논의하는 데 도움이 되는 다음 구성 요소 다이어그램을 만듭니다.

 ![지불 시스템의 외부 구성 요소](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")

 **Dinner Now 결제 시스템의 구성 요소**

 이 다이어그램에서는 다양한 구성 요소 형식 및 해당 *종속성*을 보여 줍니다. 예를 들어 결제의 유효성을 검사하려면 Dinner Now 웹 사이트와 Lucerne 결제 시스템에 외부 결제 프로세서 게이트웨이가 필요합니다. 구성 요소 사이에 있는 화살표는 다른 구성 요소의 기능이 필요한 구성 요소를 나타내는 종속성을 나타냅니다.

 Lucerne 결제 시스템을 사용하려면 Lucerne 결제 시스템에서 PaymentApproval 및 PayableInsertion 인터페이스를 사용하도록 Dinner Now 웹 사이트를 업데이트해야 합니다.

 다음 다이어그램에서는 Dinner Now 웹 사이트에 대한 구성 요소의 특정 구성을 보여 줍니다. 이 구성은 웹 사이트 인스턴스가 다음 4개 *파트*로 구성됨을 나타냅니다.

- CustomerProcessing

- OrderProcessing

- ReviewProcessing

- PaymentProcessing

  이들 파트는 지정된 구성 요소 형식의 인스턴스이고 다음과 같이 연결됩니다.

  ![Dinner Now 웹 사이트 내부의 구성 요소](../modeling/media/uml-dinnernow.png "UML_DinnerNow")

  **Dinner Now 웹 사이트 내부의 구성 요소**

  Dinner Now 웹 사이트는 웹 사이트의 기능을 처리하는 동작을 이들 파트에 위임합니다. 부모 구성 요소와 해당 구성원 구성 요소 사이에 있는 화살표는 부모가 인터페이스를 통해 받고 보낸 메시지를 처리하는 파트를 지정하는 *위임* 을 보여 줍니다.

  이 구성에서 PaymentProcessing 구성 요소는 고객 결제를 처리합니다. 따라서 Lucerne 결제 시스템과 통합하도록 업데이트되어야 합니다. 다른 시나리오에서는 구성 요소 형식의 여러 인스턴스가 같은 부모 구성 요소에 있을 수 있습니다.

  다음을 참조하세요.

- [UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)

- [UML 구성 요소 다이어그램: 지침](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="drawing-a-component-diagram"></a>구성 요소 다이어그램 그리기
 구성 요소 다이어그램의 주요 기능은 다음과 같습니다.

- *구성 요소* - 시스템 기능의 분리 가능한 부분을 나타냅니다.

- *제공된 인터페이스 포트* - 구성 요소가 구현하고 다른 구성 요소나 외부 시스템에서 사용되는 메시지 또는 호출의 그룹을 나타냅니다.

- *필요한 인터페이스 포트* - 구성 요소가 다른 구성 요소나 외부 시스템에 보내는 메시지 또는 호출의 그룹을 나타냅니다. 이 포트 종류는 구성 요소가 다른 구성 요소나 외부 시스템에서 최소한으로 예상하는 작업을 설명합니다.

- *파트* 는 구성 요소의 구성원이며 일반적으로 다른 구성 요소의 인스턴스입니다. 파트는 부모 구성 요소의 내부 디자인 조각입니다.

- *종속성* - 구성 요소에 다른 구성 요소의 기능이 필요함을 나타냅니다.

- *위임* - 구성 요소 파트가 부모 구성 요소에서 보내거나 받는 메시지를 처리함을 나타냅니다.

  다음을 참조하세요.

- [UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)

- [UML 구성 요소 다이어그램: 지침](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="summary-strengths-of-component-diagrams"></a>요약: 구성 요소 다이어그램의 장점
 구성 요소 다이어그램을 통해 다음을 시각화할 수 있습니다.

- 구현 언어나 스타일과 관계없이 분리 가능한 파트의 컬렉션으로서 시스템.

- 요구 사항이 변경될 때 디자인을 더 쉽게 이해하고 업데이트할 수 있게 하는 잘 정의된 인터페이스가 있는 구성 요소.

#### <a name="relationship-to-other-diagrams"></a>다른 다이어그램과의 관계

|**다이어그램**|**설명**|
|-----------------|---------------------|
|코드 맵|기존 코드에서 구성 및 관계를 시각화합니다.<br /><br /> 구성 요소 후보를 식별하려면 코드 맵을 만들고 시스템에서 기능별로 항목을 그룹화합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [솔루션 전반에 걸쳐 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)|
|시퀀스 다이어그램|구성 요소 간 또는 구성 요소 내부 파트 간 상호 작용의 시퀀스를 시각화합니다.<br /><br /> 시퀀스 다이어그램에서 구성 요소의 수명선을 만들려면 구성 요소를 마우스 오른쪽 단추로 클릭하고 **수명선 만들기**를 클릭합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML 시퀀스 다이어그램: 지침](../modeling/uml-sequence-diagrams-guidelines.md)|
|클래스 다이어그램(UML)|제공되거나 필요한 포트 및 구성 요소 기능을 구현하는 클래스에서 인터페이스를 정의합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)|
|레이어 다이어그램|시스템의 논리적 아키텍처를 구성 요소에 대한 관계로 설명합니다. 레이어 유효성 검사를 사용하여 코드와 디자인의 일관성이 유지되는지 확인합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [레이어 다이어그램: 참조](../modeling/layer-diagrams-reference.md)<br />-   [레이어 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)<br />-   [레이어 다이어그램을 통해 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)|
|동작 다이어그램|들어오는 메시지에 대한 응답으로 구성 요소에서 수행하는 내부 처리를 시각화합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 활동 다이어그램: 참조](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML 활동 다이어그램: 지침](../modeling/uml-activity-diagrams-guidelines.md)|

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>기존 코드 시각화: 코드 맵
 코드 맵은 코드의 현재 구성 및 관계를 보여 줍니다. 항목은 맵에서 *노드* 로 표시되고 관계는 *링크*로 표시됩니다. 코드 맵을 통해 다음과 같은 작업을 수행할 수 있습니다.

- 친숙하지 않은 코드를 살펴봅니다.

- 제안된 변경이 기존 코드에 영향을 미칠 수 있는 경우 및 방식을 이해합니다.

- 복잡성, 일반 레이어 또는 패턴의 영역이나 향상된 기능을 활용할 수 있는 기타 영역을 찾습니다.

  예를 들어 Dinner Now는 PaymentProcessing 구성 요소 업데이트 비용을 예측해야 합니다. 비용은 부분적으로 이 변경이 시스템의 다른 부분에 얼마나 영향을 미치는지에 따라 달라집니다. 이 흐름을 이해하는 데 도움이 되도록 Dinner Now 개발자의 한 명이 코드에서 코드 맵을 생성하고 변경이 영향을 미칠 수 있는 영역에서 범위 초점을 조정합니다.

  다음 맵은 PaymentProcessing 클래스와 선택된 것으로 표시되는 Dinner Now 시스템 다른 파트 간의 종속성을 보여 줍니다.

  ![Dinner Now 지불 시스템의 종속성 그래프](../modeling/media/dep-dnpayment.png "Dep_DNPayment")

  **Dinner Now 결제 시스템에 대한 코드 맵**

  개발자는 PaymentProcessing 클래스를 확장하고 해당 구성원을 선택하여 영향을 받을 수 있는 영역을 확인하는 방식으로 맵을 살펴봅니다.

  ![PaymentProcessing 내부 메서드 및 종속성](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")

  **PaymentProcessing 클래스 내부 메서드 및 해당 종속성**

  Lucerne 결제 시스템에 대한 다음 맵을 생성하여 클래스, 메서드 및 종속성을 검사합니다. 팀에서는 Lucerne 시스템에 Dinner Now의 다른 부분과 상호 작용하기 위해 작업이 필요한지를 확인합니다.

  ![Lucerne 지불 시스템의 종속성 그래프](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")

  **Lucerne 결제 시스템에 대한 코드 맵**

  두 팀이 모두 협력하여 두 시스템을 통합하는 데 필요한 변경 내용을 결정합니다. 더 쉽게 업데이트할 수 있게 일부 코드를 리팩터링하도록 결정합니다. PaymentApprover 클래스는 DinnerNow.Business 네임스페이스로 이동하며 몇 가지 새로운 메서드가 필요합니다. 트랜잭션을 처리하는 Dinner Now 클래스에는 자체 네임스페이스가 있습니다. 팀에서는 작업 항목을 만들고 사용하여 작업을 계획, 구성 및 추적합니다. 필요할 경우 작업 항목을 모델 요소에 연결합니다.

  코드를 재구성하고 나서 팀에서는 새 코드 맵을 생성하여 업데이트된 구조와 관계를 확인합니다.

  ![코드를 재구성한 종속성 그래프](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")

  **코드를 재구성한 코드 맵**

  이 맵은 PaymentApprover 클래스가 현재 DinnerNow.Business 네임스페이스에 있고 몇 가지 새로운 메서드를 포함한다는 것을 보여 줍니다. Dinner Now 트랜잭션 클래스에는 현재 자체 PaymentSystem 네임스페이스가 있고 이를 통해 나중에 해당 코드를 더 쉽게 처리할 수 있습니다.

#### <a name="creating-a-code-map"></a>코드 맵 만들기

- 소스 코드의 간략한 개요를 확인하려면 다음 단계에 따라 코드 맵을 생성합니다.

     **아키텍처** 메뉴에서 **솔루션용 코드 맵 생성**을 클릭합니다.

     컴파일된 코드의 간략한 개요를 확인하려면 빈 코드 맵을 만들고 어셈블리 파일이나 이진 파일을 맵 표면으로 끌어옵니다.

- 특정 코드 또는 솔루션 항목을 살펴보려면 솔루션 탐색기를 사용하여 시각화할 항목 및 관계를 선택합니다. 그다음에 새 맵을 생성하거나 선택된 항목을 기존 맵에 추가할 수 있습니다. [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)을 참조하세요.

- 맵을 살펴보는 데 도움이 되도록 수행할 작업 종류에 맞게 레이아웃을 다시 정렬합니다.

     예를 들어 코드에서 레이어를 시각화하려면 트리 레이아웃을 선택합니다. [코드 맵 찾아보기 및 재정렬을](../modeling/browse-and-rearrange-code-maps.md)참조하십시오.

#### <a name="summary-strengths-of-code-maps"></a>요약: 코드 맵의 장점
 코드 맵을 통해 다음을 수행할 수 있습니다.

- 기존 코드의 구성 및 관계에 대해 알아봅니다.

- 제안된 변경이 영향을 받을 수 있는 영역을 식별합니다.

- 복잡성, 패턴, 레이어의 영역이나 코드를 더 쉽게 유지 관리, 변경 및 다시 사용하도록 향상할 수 있는 기타 영역을 찾습니다.

#### <a name="relationship-to-other-diagrams"></a>다른 다이어그램과의 관계

|**다이어그램**|**설명 내용**|
|-----------------|-------------------|
|레이어 다이어그램|시스템의 논리적 아키텍처. 레이어 유효성 검사를 사용하여 코드와 디자인의 일관성이 유지되는지 확인합니다.<br /><br /> 기존 레이어 또는 의도한 레이어를 식별하는 데 도움이 되도록 코드 맵을 만들고 관련 항목을 그룹화합니다. 레이어 다이어그램을 만들려면 다음을 참조하세요.<br /><br /> -   [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [레이어 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)|
|구성 요소 다이어그램|구성 요소, 해당 인터페이스 및 해당 관계.<br /><br /> 구성 요소를 식별하는 데 도움이 되도록 코드 맵을 만들고 시스템에서 기능별로 항목을 그룹화합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)<br />-   [UML 구성 요소 다이어그램: 지침](../modeling/uml-component-diagrams-guidelines.md)|
|클래스 다이어그램(UML)|클래스, 해당 특성 및 작업, 해당 관계.<br /><br /> 이들 요소를 식별하는 데 도움이 되도록 해당 요소를 표시하는 UML 클래스 다이어그램을 만듭니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)|
|클래스 다이어그램(코드 기반)|특정 프로젝트에 대한 코드의 기존 클래스.<br /><br /> 코드에서 기존 클래스를 시각화 및 수정하려면 클래스 디자이너를 사용합니다.<br /><br /> [방법: 프로젝트에 클래스 다이어그램 추가(클래스 디자이너)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)을 참조하세요.|

### <a name="describe-the-interactions-sequence-diagrams"></a><a name="DescribeSequence"></a>상호 작용 설명: 시퀀스 다이어그램
 시퀀스 다이어그램에서는 시스템 파트 간에 발생하는 일련의 상호 작용을 설명합니다. 파트는 크기에 제한이 없습니다. 예를 들어 파트의 범위는 프로그램의 개별 개체부터 대형 하위 시스템 또는 외부 행위자까지 해당할 수 있습니다. 상호 작용은 크기 및 형식의 제한이 없습니다. 예를 들어 상호 작용의 범위는 개별 메시지부터 확장된 트랜잭션까지 해당할 수 있고 함수 호출 또는 웹 서비스 메시지가 될 수도 있습니다.

 Lucerne과 Dinner Now는 Process Payment 사용 사례의 단계를 설명하고 논의하는 과정에 도움이 되도록 구성 요소 다이어그램에서 다음 시퀀스 다이어그램을 만듭니다. 수명선은 Dinner Now 웹 사이트 구성 요소 및 해당 파트를 미러링합니다. 수명선 사이에 나타나는 메시지는 구성 요소 다이어그램의 연결을 따릅니다.

 ![Process Payment 사용 사례에 대한 시퀀스 다이어그램](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")

 **Process Payment 사용 사례에 대한 시퀀스 다이어그램**

 시퀀스 다이어그램에서는 고객이 주문을 작성할 때 Dinner Now 웹 사이트가 OrderProcessing 인스턴스에서 ProcessOrder를 호출함을 보여 줍니다. 다음으로 OrderProcessing은 PaymentProcessing에서 ProcessPayment를 호출합니다. 이 작업은 외부 결제 프로세서 게이트웨이에서 결제 유효성을 확인할 때까지 계속됩니다. 확인되고 나면 제어가 Dinner Now 웹 사이트로 돌아갑니다.

 Lucerne은 Dinner Now 시스템과 통합하기 위해 결제 시스템을 업데이트하는 비용을 예측해야 합니다. 이에 대한 이해를 돕기 위해 코드 맵을 만들어 영향을 받는 코드를 시각화할 수도 있습니다.

 다음을 참조하세요.

- [UML 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)

- [UML 시퀀스 다이어그램: 지침](../modeling/uml-sequence-diagrams-guidelines.md)

- [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)

#### <a name="drawing-a-sequence-diagram"></a>시퀀스 다이어그램 그리기
 시퀀스 다이어그램의 주요 기능은 다음과 같습니다.

- 세로 *수명선* - 소프트웨어 개체의 행위자 또는 인스턴스를 나타냅니다.

   참가자가 개발 중인 시스템 외부에 있음을 나타내는 행위자 기호를 추가하려면 수명선을 클릭합니다. **속성** 창에서 **행위자** 를 **True**로 설정합니다. **속성** 창이 열리지 않으면 **F4**키를 누릅니다.

- 가로 *메시지* - 메서드 호출, 웹 서비스 메시지 또는 일부 기타 통신을 나타냅니다. *실행 빈도* - 수명선에 나타나는 세로 음영이 있는 사각형이며 수신하는 개체가 호출을 처리하는 기간을 나타냅니다.

- *동기* 메시지 동안 보낸 자 개체는 컨트롤이 일반 \<함수 호출에서와 같이>> 반환하지 <때까지 기다립니다. *비동기* 메시지 중에 sender는 즉시 계속 진행할 수 있습니다.

- <\<>> 메시지를 만들어 다른 개체에 의한 개체의 구성을 나타냅니다. 개체에 전송된 첫 번째 메시지여야 합니다.

  다음을 참조하세요.

- [UML 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)

- [UML 시퀀스 다이어그램: 지침](../modeling/uml-sequence-diagrams-guidelines.md)

#### <a name="summary-strengths-of-sequence-diagrams"></a>요약: 시퀀스 다이어그램의 장점
 시퀀스 다이어그램을 통해 다음을 시각화할 수 있습니다.

- 사용 사례 실행 중에 행위자 또는 개체 간에 전송되는 제어 흐름.

- 메서드 호출 또는 메시지의 구현.

#### <a name="relationship-to-other-diagrams"></a>다른 다이어그램과의 관계

|**다이어그램**|**설명**|
|-----------------|---------------------|
|클래스 다이어그램(UML)|수명선이 나타내는 클래스와 수명선 간에 전송되는 메시지에 사용되는 매개 변수 및 반환 값을 정의합니다.<br /><br /> 수명선에서 클래스를 만들려면 수명선을 마우스 오른쪽 단추로 클릭하고 **클래스 만들기** 또는 **인터페이스 만들기**를 클릭합니다. 클래스 다이어그램의 형식에서 수명선을 만들려면 형식을 마우스 오른쪽 단추로 클릭하고 **수명선 만들기**를 클릭합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)<br />-   [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)|
|구성 요소 다이어그램|수명선이 나타내는 구성 요소 및 메시지로 표시되는 동작을 제공하고 사용하는 인터페이스를 설명합니다.<br /><br /> 구성 요소 다이어그램에서 수명선을 만들려면 구성 요소를 마우스 오른쪽 단추로 클릭하고 **수명선 만들기**를 클릭합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)<br />-   [UML 구성 요소 다이어그램: 지침](../modeling/uml-component-diagrams-guidelines.md)|
|사용 사례 다이어그램|시퀀스 다이어그램에서 사용자 및 구성 요소 간의 상호 작용을 사용자 목표를 나타내는 사용 사례로 간략하게 설명합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a> 형식 용어집 정의: 클래스 다이어그램
 클래스 다이어그램에서는 시스템에 참가하는 엔터티, 용어 또는 개념과 서로 간의 관계를 정의합니다. 예를 들어 개발 중에 이들 다이어그램을 사용하여 구현 언어나 스타일과 관계없이 각 클래스에 대한 특성 및 작업을 설명할 수 있습니다.

 Lucerne은 Process Payment 사용 사례에 참가하는 엔터티를 설명하고 논의하는 데 도움이 되도록 다음 클래스 다이어그램을 그립니다.

 ![클래스 다이어그램의 Process Payment 엔터티](../modeling/media/uml-payentities.png "UML_PayEntities")

 **클래스 다이어그램의 Process Payment 엔터티**

 이 다이어그램에서는 고객에게 많은 주문과 다양한 주문 결제 방법이 있음을 보여 줍니다. BankAccount 및 CreditCard는 둘 다 Payment에서 상속됩니다.

 개발 중에 Lucerne은 다음 클래스 다이어그램을 사용하여 각 클래스의 세부 정보를 설명하고 논의합니다.

 ![클래스 다이어그램의 Process Payment 엔터티 세부 정보](../modeling/media/uml-payment.png "UML_Payment")

 **클래스 다이어그램의 Process Payment 세부 정보**

 다음을 참조하세요.

- [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)

- [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)

#### <a name="drawing-a-class-diagram"></a>클래스 다이어그램 그리기
 클래스 다이어그램의 주요 기능은 다음과 같습니다.

- 클래스, 인터페이스 및 열거형 등의 형식:

  - *클래스* 는 특정 구조 또는 동작 특성을 공유하는 개체의 정의입니다.

  - *인터페이스* 는 개체의 외부적으로 표시되는 동작 파트를 정의합니다.

  - *열거형* 은 리터럴 값 목록을 포함하는 분류자입니다.

- *특성* 은 *분류자*의 각 인스턴스를 설명하는 특정 형식 값입니다. 분류자는 형식, 구성 요소, 사용 사례 및 행위자의 일반 이름입니다.

- *작업* 은 분류자의 인스턴스가 수행할 수 있는 메서드 또는 함수입니다.

- *연결* 은 두 분류자 간의 몇 가지 관계를 나타냅니다.

  - *집합체* 는 분류자 간에 공유되는 소유권을 나타내는 연결입니다.

  - *컴퍼지션* 은 분류자 간에 전체-부분 관계를 나타내는 연결입니다.

    집합체 또는 컴퍼지션을 표시하려면 연결에서 **집합체** 속성을 설정합니다. **공유** 는 집합체를 표시하고 **복합** 은 컴퍼지션을 표시합니다.

- *종속성* 은 한 분류자의 정의를 변경하면 다른 분류자의 정의가 변경될 수 있음을 나타냅니다.

- *일반화* 는 특정 분류자가 일반 분류자에서 정의 파트를 상속함을 나타냅니다. *인식*은 클래스가 인터페이스에서 제공된 작업 및 특성을 구현함을 나타냅니다.

   이들 관계를 만들려면 **상속** 도구를 사용합니다. 인식이 *롤리팝*으로 표시될 수도 있습니다.

- *패키지* 는 분류자, 연결, 수명선, 구성 요소 및 기타 패키지의 그룹입니다. *가져오기* 관계는 한 패키지에 다른 패키지의 모든 정의가 포함됨을 나타냅니다.

  기존 클래스를 살펴보고 논의하려면 먼저 클래스 디자이너를 사용하여 코드에서 클래스 다이어그램을 만듭니다.

  다음을 참조하세요.

- [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)

- [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)

- [방법: 프로젝트에 클래스 다이어그램 추가(클래스 디자이너)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>요약: 클래스 다이어그램의 장점
 클래스 다이어그램을 통해 다음을 정의할 수 있습니다.

- 사용자 요구 및 시스템에 참가하는 엔터티에 대해 논의할 때 사용할 일반 용어집. [사용자 요구 사항 모델을](../modeling/model-user-requirements.md)참조하십시오.

- 구현과 관계없이 구성 요소와 같은 시스템 파트에서 사용되는 형식. [앱의 아키텍처 모델을](../modeling/model-your-app-s-architecture.md)참조하십시오.

- 종속성과 같은 형식 간 관계. 예를 들어 한 형식을 다른 형식의 여러 인스턴스와 연결할 수 있다는 것을 표시할 수 있습니다.

#### <a name="relationship-to-other-diagrams"></a>다른 다이어그램과의 관계

|**다이어그램**|**설명**|
|-----------------|---------------------|
|사용 사례 다이어그램|사용 사례의 목표 및 단계를 설명하는 데 사용되는 형식을 정의합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)|
|동작 다이어그램|개체 노드, 입력 핀, 출력 핀 및 동작 매개 변수 노드를 통과하는 데이터 형식을 정의합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 활동 다이어그램: 참조](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML 활동 다이어그램: 지침](../modeling/uml-activity-diagrams-guidelines.md)|
|구성 요소 다이어그램|구성 요소, 해당 인터페이스 및 해당 관계를 설명합니다. 클래스가 전체 구성 요소를 설명할 수도 있습니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)<br />-   [UML 구성 요소 다이어그램: 지침](../modeling/uml-component-diagrams-guidelines.md)|
|레이어 다이어그램|시스템의 논리적 아키텍처를 클래스에 대한 관계로 설명합니다.<br /><br /> 레이어 유효성 검사를 사용하여 코드와 디자인의 일관성이 유지되는지 확인합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [레이어 다이어그램: 참조](../modeling/layer-diagrams-reference.md)<br />-   [레이어 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)<br />-   [레이어 다이어그램을 통해 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)|
|시퀀스 다이어그램|수명선 형식과 수명선이 수신할 수 있는 모든 메시지에 대한 작업, 매개 변수 및 반환 값을 정의합니다.<br /><br /> 클래스 다이어그램의 형식에서 수명선을 만들려면 형식을 마우스 오른쪽 단추로 클릭하고 **수명선 만들기**를 클릭합니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML 시퀀스 다이어그램: 지침](../modeling/uml-sequence-diagrams-guidelines.md)|
|코드 맵|기존 코드에서 구성 및 관계를 시각화합니다.<br /><br /> 클래스, 해당 관계 및 해당 메서드를 식별하려면 해당 요소를 표시하는 코드 맵을 만듭니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [솔루션 전반에 걸쳐 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-layer-diagrams"></a><a name="DescribeLayers"></a>논리 아키텍처 설명: 레이어 다이어그램
 레이어 다이어그램에서는 솔루션의 아티팩트를 추상 그룹 또는 *레이어*로 구성하여 시스템의 논리적 아키텍처를 설명합니다. 아티팩트는 네임스페이스, 프로젝트, 클래스, 메서드 등 다양한 항목에 해당할 수 있습니다. 레이어는 아티팩트가 시스템에서 수행하는 역할 또는 작업을 표시하고 설명합니다. 빌드 및 체크 인 작업에 레이어 유효성 검사를 포함하여 코드와 디자인의 일관성이 유지되는지 확인할 수도 있습니다.

 코드와 디자인의 일관성을 유지하기 위해 Dinner Now와 Lucerne은 다음 레이어 다이어그램을 사용하여 코드가 발전함에 따라 코드의 유효성을 검사합니다.

 ![통합 지불 시스템의 레이어 다이어그램](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Lucerne과 통합된 Dinner Now에 대한 레이어 다이어그램**

 이 다이어그램의 레이어는 해당하는 Dinner Now 및 Lucerne 솔루션 아티팩트에 연결됩니다. 예를 들어 비즈니스 레이어는 현재 PaymentApprover 클래스를 포함하는 DinnerNow.Business 네임스페이스 및 해당 구성원에 연결됩니다. 리소스 액세스 레이어는 DinnerNow.Data 네임스페이스에 연결됩니다. 화살표 또는 *종속성*은 비즈니스 레이어에서만 리소스 액세스 레이어의 기능을 사용할 수 있도록 지정합니다. 팀에서 해당 코드를 업데이트하면 레이어 유효성 검사가 주기적으로 수행되어 충돌이 발생할 때 이를 catch하고 팀에서 충돌을 빠르게 해결하도록 도와줍니다.

 팀에서는 협력하여 두 시스템을 점차 통합하고 테스트합니다. PaymentProcessing을 처리하기 전에 먼저 PaymentApprover와 Dinner Now의 나머지 부분이 서로 성공적으로 연동되는지 확인합니다.

 다음 코드 맵은 Dinner Now와 PaymentApprover 간의 새로운 호출을 보여 줍니다.

 ![통합 시스템으로 업데이트된 종속성 그래프](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")

 **메서드 호출이 업데이트된 코드 맵**

 시스템이 예상대로 작동하는지 확인하고 나서 Dinner Now는 PaymentProcessing 코드를 주석으로 처리합니다. 레이어 유효성 검사 보고서는 분명하며, 결과 코드 맵은 PaymentProcessing 종속성이 존재하지 않음을 보여 줍니다.

 ![PaymentProcessing 없는 종속성 그래프](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")

 **PaymentProcessing이 없는 코드 맵**

#### <a name="drawing-a-layer-diagram"></a>레이어 다이어그램 그리기
 레이어 다이어그램의 주요 기능은 다음과 같습니다.

- *레이어* - 아티팩트의 논리 그룹을 설명합니다.

- *링크* - 레이어와 아티팩트 간 연결입니다.

   아티팩트에서 레이어를 만들려면 솔루션 탐색기, 코드 맵, 클래스 뷰 또는 개체 브라우저에서 항목을 끌어옵니다. 새 레이어를 그리고 아티팩트에 연결하려면 도구 상자를 사용하거나 다이어그램 곡면을 마우스 오른쪽 단추로 클릭하여 레이어를 만들고 항목을 해당 레이어에 끌어옵니다.

   레이어의 숫자는 해당 레이어에 연결된 아티팩트의 수를 나타냅니다. 이들 아티팩트는 네임스페이스, 프로젝트, 클래스, 메서드 등에 해당할 수 있습니다. 레이어의 아티팩트 수를 해석할 때 다음을 고려하세요.

  - 레이어가 직접 연결되지 않은 다른 아티팩트를 포함하는 아티팩트에 연결된 경우 연결된 아티팩트만 숫자에 포함됩니다. 그러나 레이어 유효성 검사 중에는 직접 연결되지 않은 다른 아티팩트도 분석을 위해 포함됩니다.

     예를 들어 레이어가 단일 네임스페이스에 연결된 경우 해당 네임스페이스에 클래스가 들어 있더라도 연결된 아티팩트의 수는 1입니다. 레이어가 네임스페이스의 각 클래스에도 연결되어 있으면 연결된 클래스가 숫자에 포함됩니다.

  - 레이어가 아티팩트에 연결된 다른 레이어를 포함하면 컨테이너 레이어가 이 아티팩트에도 연결됩니다. 단, 컨테이너 레이어의 숫자에는 이러한 아티팩트가 포함되지 않습니다.

    레이어에 연결된 아티팩트를 확인하려면 레이어를 마우스 오른쪽 단추로 클릭하고 **링크 보기** 를 클릭하여 **레이어 탐색기**를 엽니다.

- *종속성* 은 한 레이어에서 다른 레이어의 기능을 사용할 수 있지만 반대의 경우는 불가능함을 나타냅니다. *양방향 종속성* 은 한 레이어에서 다른 레이어의 기능을 사용할 수 있고 반대 방향으로도 가능함을 나타냅니다.

   레이어 다이어그램에 기존 종속성을 표시하려면 다이어그램 곡면을 마우스 오른쪽 단추로 클릭하고 **종속성 생성**을 클릭합니다. 의도한 종속성을 설명하려면 새 종속성을 그립니다.

  다음을 참조하세요.

- [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)

- [레이어 다이어그램: 참조](../modeling/layer-diagrams-reference.md)

- [레이어 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)

- [레이어 다이어그램에 대해 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-layer-diagrams"></a>요약: 레이어 다이어그램의 장점
 레이어 다이어그램을 통해 다음을 수행할 수 있습니다.

- 아티팩트의 기능에 따라 시스템의 논리적 아키텍처를 설명합니다.

- 개발 중인 코드가 지정된 디자인을 준수하는지 확인합니다.

#### <a name="relationship-to-other-diagrams"></a>다른 다이어그램과의 관계

|**다이어그램**|**설명**|
|-----------------|---------------------|
|코드 맵|기존 코드에서 구성 및 관계를 시각화합니다.<br /><br /> 레이어를 만들려면 코드 맵을 생성하고 맵에서 항목을 잠재적인 레이어로 그룹화합니다. 그룹을 맵에서 레이어 다이어그램으로 끌어옵니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [솔루션 전반에 걸쳐 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)<br />-   [코드 맵 찾아보기 및 재정렬](../modeling/browse-and-rearrange-code-maps.md)|
|구성 요소 다이어그램|구성 요소, 해당 인터페이스 및 해당 관계를 설명합니다.<br /><br /> 레이어를 시각화하려면 시스템에 있는 다양한 구성 요소의 기능을 설명하는 구성 요소 다이어그램을 만듭니다.<br /><br /> 다음을 참조하세요.<br /><br /> -   [UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)<br />-   [UML 구성 요소 다이어그램: 지침](../modeling/uml-component-diagrams-guidelines.md)|

## <a name="external-resources"></a>외부 리소스

|**범주**|**링크**|
|------------------|---------------|
|**포럼**|-   [Visual Studio 시각화 및 모델링 도구](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio 시각화 및 모델링 SDK(DSL 도구)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>참고 항목
 [코드 시각화](../modeling/visualize-code.md) 개발 [프로세스에서](../modeling/use-models-in-your-development-process.md) 앱 사용 [모델에 대한 모델 만들기](../modeling/create-models-for-your-app.md) [Agile 개발에서](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) 모델 개발 [확장 UML 모델 및 다이어그램](../modeling/extend-uml-models-and-diagrams.md) [동안 시스템 유효성](../modeling/validate-your-system-during-development.md) 검사
