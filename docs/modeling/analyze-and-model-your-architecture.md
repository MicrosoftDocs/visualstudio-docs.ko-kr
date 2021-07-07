---
title: 아키텍처 분석 및 모델링 도구
description: 앱을 디자인하고 모델링하여 앱이 아키텍처 요구 사항을 충족하는지 확인합니다.
ms.custom: SEO-VS-2020
ms.date: 06/04/2021
ms.topic: overview
helpviewer_keywords:
- diagrams - modeling
- architecture
- code visualization
- application design
- code exploration
- modeling
- application architecture
- architecture [Visual Studio ALM], modeling
- application modeling
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 542b74e7d3bb73847303fa4215651eea7e110e91
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384878"
---
# <a name="analyze-and-model-your-architecture"></a>아키텍처 분석 및 모델링

Visual Studio 아키텍처 및 모델링 도구를 사용하여 앱을 디자인 및 모델링하는 방식으로 앱이 아키텍처 요구 사항을 충족하는지 확인합니다.

1. 코드 구조, 동작과 함께 코드 맵 및 종속성 다이어그램에 대한 관계를 [시각화](visualize-code.md)하여 기존 프로그램 코드를 더 잘 이해합니다.
    - **코드 맵** 을 만들어 코드 구성 및 관계를 확인합니다. 
    - 어셈블리, 네임스페이스, 클래스, 메서드 간의 종속성을 시각화합니다.
    - **종속성 다이어그램** 을 만들어 코드 유효성을 검사하는 방식으로 코드와 해당 디자인 간에 충돌을 확인합니다.
    - [코드에서 클래스 다이어그램을 만들어](../ide/class-designer/designing-and-viewing-classes-and-types.md) 특정 프로젝트의 클래스 구조 및 멤버를 확인합니다.
    - 텍스트 기반 파일을 생성하기 위해 템플릿 내부에 텍스트 블록 및 제어 논리가 있는 [T4 템플릿을 사용하여 텍스트를 생성](../modeling/code-generation-and-t4-text-templates.md)합니다. 
    
1. 아키텍처 종속성을 준수하는 데 필요한 팀을 교육합니다.

1. 개발 프로세스의 일부로 애플리케이션 수명 주기 전체에 걸쳐 다양한 상세 수준으로 모델을 만듭니다.

[시나리오: 시각화 및 모델링을 사용하여 디자인 변경](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)을 참조하세요.

## <a name="code-maps"></a>코드 맵

코드 맵은 코드에서 구성 및 관계를 확인하는 데 도움이 되는 모델 유형 중 하나입니다.

맵을 사용하여 프로그램 코드를 검토하면 해당 구조 및 종속성, 업데이트 방법을 더 잘 이해하고 제안된 변경의 비용을 예측할 수 있습니다.

자세한 정보:
- [아키텍처 코드 도구 설치](install-architecture-tools.md)
- [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)
- [코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)
- [코드 맵 분석기를 사용하여 잠재적 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="dependency-diagrams"></a>종속성 다이어그램

종속성 다이어그램을 통해 애플리케이션 구조를 명시적 종속성이 포함된 레이어 또는 블록 세트로 정의할 수 있습니다. 실시간 유효성 검사를 통해 코드의 종속성과 종속성 다이어그램에 설명된 종속 간 충돌을 보여 줍니다.

종속성 다이어그램을 사용하여 다음을 수행합니다. 
- 애플리케이션 수명 동안 다양한 변경을 통해 애플리케이션 구조를 안정화합니다.
- 코드에 대한 변경을 확인하기 전에 의도하지 않은 종속성 충돌을 검색합니다.

자세한 정보:
- [아키텍처 코드 도구 설치](install-architecture-tools.md)
- [코드에서 종속성 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)
- [종속성 다이어그램: 참조](../modeling/layer-diagrams-reference.md)
- [종속성 다이어그램을 사용하여 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)

## <a name="domain-specific-language-dsl-models"></a>DSL(Domain-Specific Language) 모델

DSL은 특정 용도에 맞게 디자인하는 표기법입니다. Visual Studio에서는 일반적으로 그래픽으로 표시됩니다.

DSL(Domain-Specific Language)을 사용하여 다음을 수행합니다. 
- 애플리케이션 파트를 생성하거나 구성합니다. 표기법 및 도구를 개발하려면 작업이 필요합니다. 결과는 UML 사용자 지정보다 도메인에 더 적합할 수 있습니다.
- 대규모 프로젝트에 사용되거나, 여러 프로젝트에서 DSL을 사용하여 DSL 및 도구 개발에 대한 투자 수익을 얻는 제품군에 사용됩니다.

자세한 정보:
- [Visual Studio용 모델링 SDK - 도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)


## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />아키텍처 및 모델링 도구의 버전 지원

Visual Studio는 여러 버전에서 사용할 수 있습니다. 모든 버전에서 아키텍처 및 모델링 도구가 지원되는 것은 아닙니다. 다음 표에서는 각 도구의 사용 가능 여부를 보여 줍니다.

|**기능**|**Enterprise Edition**|**Professional Edition**|**Community Edition**|
|-|-|-|-|
|**코드 맵**|예|코드 맵 읽기, 코드 맵 필터링, 새 제네릭 노드 추가, 선택 영역에서 새 전송 그래프 만들기만 지원합니다.|-|
|**종속성 다이어그램**|예|종속성 다이어그램 읽기만 지원합니다.|종속성 다이어그램 읽기만 지원합니다.|
|**전송 그래프**(DGML 다이어그램)|예|예|예|
|**코드 복제본**|예|-|-|
