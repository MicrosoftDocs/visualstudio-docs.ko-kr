---
title: 코드 시각화
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9886ea905a4997d5735e4dd2cabbfc4798a5c4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535878"
---
# <a name="visualize-code"></a>코드 시각화

Visual Studio의 시각화 및 모델링 도구를 사용하여 기존 코드를 이해하고 애플리케이션을 설명할 수 있습니다. 이렇게 하면 변경 내용이 코드에 미치는 영향을 시각적으로 알아보고 작업 및 해당 변경 내용으로 인한 위험을 평가할 수 있습니다. 예를 들면 다음과 같습니다.

- 코드의 관계를 이해하려면 해당 관계를 시각적으로 매핑합니다.

- 시스템의 아키텍처를 설명 하 고 코드를 디자인과 일관 되 게 유지 하려면 종속성 다이어그램을 만들고 이러한 다이어그램에 대해 코드의 유효성을 검사 합니다.

- 클래스 구조를 설명하려면 클래스 다이어그램을 만듭니다.

또한 이러한 도구는 프로젝트에 관련된 사용자와 보다 쉽게 커뮤니케이션하는 데 도움이 됩니다.

각 기능을 지 원하는 Visual Studio의 버전을 확인 하려면 [아키텍처 및 모델링 도구에 대 한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport) 을 참조 하세요.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

|시나리오|문서|
|-|-|
|**코드 및 해당 관계 이해:**<br /><br /> 특정 코드 조각 간의 관계를 매핑합니다.<br /><br /> 전체 솔루션에 대한 코드의 관계 개요를 참조하세요.|- [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)<br />- [코드 맵을 사용 하 여 응용 프로그램 디버그](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [코드 맵 분석기를 사용 하 여 잠재적인 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [디버깅 하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**클래스 구조 이해:**<br /><br /> 코드에서 클래스 다이어그램을 만들어 프로젝트의 클래스 구조를 시각화합니다.|[방법: 프로젝트에 클래스 다이어그램 추가(클래스 디자이너)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**전반적인 시스템 디자인을 설명하고 이 디자인에 대해 코드의 유효성 검사:**<br /><br /> 종속성 다이어그램을 만들어 상위 수준 시스템 디자인과 해당 종속성을 설명 합니다. 이 디자인과 비교해서 코드의 유효성을 검사하여 코드의 종속성이 디자인과 일치하는지 확인합니다.|- [코드에서 종속성 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)<br />- [종속성 다이어그램: 참조](../modeling/layer-diagrams-reference.md)<br />- [종속성 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)<br />- [종속성 다이어그램을 사용하여 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>추가 정보

- [시나리오: 시각화 및 모델링을 사용하여 디자인 변경](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [분석 및 모델 아키텍처](../modeling/analyze-and-model-your-architecture.md)
- [앱의 아키텍처 모델링](../modeling/model-your-app-s-architecture.md)
- [개발 프로세스에서 모델 사용](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
