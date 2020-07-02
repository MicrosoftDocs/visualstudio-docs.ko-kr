---
title: 코드 시각화 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 665dc76126eac964f405be06605c40b5b30cc9a5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532940"
---
# <a name="visualize-code"></a>코드 시각화
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 시각화 및 모델링 도구를 사용하여 기존 코드를 이해하고 애플리케이션을 설명할 수 있습니다. 이렇게 하면 변경 내용이 코드에 미치는 영향을 시각적으로 알아보고 작업 및 해당 변경 내용으로 인한 위험을 평가할 수 있습니다. 예를 들면 다음과 같습니다.

- 코드의 관계를 이해하려면 해당 관계를 시각적으로 매핑합니다.

- 시스템의 아키텍처를 설명하고 코드와 디자인의 일관성을 유지하려면 레이어 다이어그램을 만들고 이러한 다이어그램에 대해 코드의 유효성을 검사합니다.

- 클래스 구조를 설명하려면 클래스 다이어그램을 만듭니다.

- 시스템의 다양한 측면을 모델링하고 전달하려면 UML(Unified Modeling Language) 다이어그램을 그립니다. 예를 들어 시스템의 구성 요소, 형식, 상호 작용 및 프로세스를 모델링할 수 있습니다.

  또한 이러한 도구는 프로젝트에 관련된 사용자와 보다 쉽게 커뮤니케이션하는 데 도움이 됩니다. 예를 들어 UML 클래스 다이어그램을 사용하여 프로젝트 이해 관계자, 사용자 및 팀 멤버와 시스템을 논의하기 위한 일반 용어집을 만들 수 있습니다.

  각 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

|시나리오|문서|
|-|-|
|**코드 및 해당 관계 이해:**<br /><br /> 특정 코드 조각 간의 관계를 매핑합니다.<br /><br /> 전체 솔루션에 대한 코드의 관계 개요를 참조하세요.<br /><br /> **참고**: 이 Visual Studio 릴리스에서는 *종속성 그래프* 대신에 *코드 맵*이 사용됩니다.|-   [솔루션 전체에서 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)<br />-   [코드 맵을 사용 하 여 응용 프로그램 디버그](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [코드 맵 분석기를 사용 하 여 잠재적인 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [디버깅 하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**클래스 구조 이해:**<br /><br /> 코드에서 클래스 다이어그램을 만들어 프로젝트의 클래스 구조를 시각화합니다.|[방법: 프로젝트에 클래스 다이어그램 추가 (클래스 디자이너)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**전반적인 시스템 디자인을 설명하고 이 디자인에 대해 코드의 유효성 검사:**<br /><br /> 레이어 다이어그램을 만들어 전반적인 시스템 디자인 및 의도한 종속성에 대해 설명합니다. 이 디자인과 비교해서 코드의 유효성을 검사하여 코드의 종속성이 디자인과 일치하는지 확인합니다.|-   [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [레이어 다이어그램: 참조](../modeling/layer-diagrams-reference.md)<br />-   [레이어 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)<br />-   [레이어 다이어그램을 사용 하 여 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)|
|**사용자 요구 사항 및 아키텍처 전달:**<br /><br /> 동작, 구성 요소, 클래스, 시퀀스 및 사용 사례의 UML 다이어그램을 그려 사용자 요구 사항과 소프트웨어 시스템의 아키텍처를 모델링합니다.|-   [앱에 대 한 모델 만들기](../modeling/create-models-for-your-app.md)<br />-   [사용자 요구 사항 모델링](../modeling/model-user-requirements.md)<br />-   [앱의 아키텍처 모델링](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>외부 리소스

|**범주**|**링크**|
|------------------|---------------|
|**포럼**|-   [Visual Studio 시각화 및 모델링 도구](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio 시각화 및 모델링 SDK(DSL 도구)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**블로그**|[Visual Studio ALM + Team Foundation Server 블로그](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**기술 문서 및 저널**|[MSDN 아키텍처 포럼](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>참고 항목
 [시나리오: 시각화 및 모델링을 사용 하 여 디자인 변경](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [아키텍처 분석 및 모델링 아키텍처 모델](../modeling/analyze-and-model-your-architecture.md) [만들기](../modeling/create-models-for-your-app.md) [사용자 요구 사항](../modeling/model-user-requirements.md) [모델 앱 아키텍처](../modeling/model-your-app-s-architecture.md) [사용 개발 프로세스에서 모델 사용](../modeling/use-models-in-your-development-process.md)
