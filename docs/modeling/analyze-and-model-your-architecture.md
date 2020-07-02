---
title: 아키텍처 분석 및 모델링
ms.date: 11/04/2016
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1db28867ea47752aa74b7898c44e797c0704594
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544224"
---
# <a name="analyze-and-model-your-architecture"></a>아키텍처 분석 및 모델링

앱을 디자인 및 모델링 하기 위해 Visual Studio 아키텍처 및 모델링 도구를 사용 하 여 앱이 아키텍처 요구 사항을 충족 하는지 확인 합니다.

* Visual Studio를 사용하여 코드의 구조, 동작 및 관계를 시각화하는 방식으로 기존 프로그램 코드를 더 쉽게 이해할 수 있습니다.

* 아키텍처 종속성을 준수 하는 데 필요한 팀을 교육 합니다.

* 개발 프로세스의 일부로 애플리케이션 수명 주기 전체에 걸쳐 다양한 상세 수준으로 모델을 만듭니다.

[시나리오: 시각화 및 모델링을 사용 하 여 디자인 변경](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)을 참조 하세요.

## <a name="article-reference"></a>문서 참조

|시나리오|문서|
|-|-|
|**코드 시각화**:<br /><br />-코드 맵을 만들어 코드의 구성 및 관계를 확인 합니다. 어셈블리, 네임스페이스, 클래스, 메서드 간의 종속성을 시각화합니다.<br />-코드에서 클래스 다이어그램을 만들어 특정 프로젝트에 대 한 클래스 구조 및 멤버를 확인 합니다.<br />-코드의 유효성을 검사 하는 종속성 다이어그램을 만들어 코드와 디자인 간의 충돌을 찾습니다.|- [코드 시각화](../modeling/visualize-code.md)<br />- [클래스 및 기타 형식 작업 (클래스 디자이너)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />- [비디오: Visual Studio 2015 코드 맵을 사용 하 여 코드에서 디자인 이해](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />- [비디오: 실시간으로 아키텍처 종속성 유효성 검사](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**아키텍처 정의**:<br /><br />-종속성 다이어그램을 만들어 코드의 구성 요소 간 종속성에 대 한 제약 조건을 정의 하 고 적용 합니다.|- [비디오: Visual Studio를 사용 하 여 아키텍처 종속성 유효성 검사 (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**요구 사항 및 의도한 디자인을 사용하여 시스템의 유효성을 검사합니다.**<br /><br />-의도 한 아키텍처를 설명 하 고 디자인과 충돌할 수 있는 변경 사항을 방지 하는 종속성 다이어그램으로 코드 종속성의 유효성을 검사 합니다.|- [비디오: Visual Studio를 사용 하 여 아키텍처 종속성 유효성 검사 (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**모델 및 다이어그램 사용자 지정**:<br /><br />-도메인 특정 언어를 만듭니다.|- [Visual Studio 용 모델링 SDK-도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**T4 템플릿을 사용하여 텍스트 생성**:<br /><br />-텍스트 블록 및 템플릿 내에서 컨트롤 논리를 사용 하 여 텍스트 기반 파일을 생성 합니다.<br /> -Visual Studio에 포함 된 MSBuild를 사용 하 여 T4 템플릿 빌드|- [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)|
|**Team Foundation 버전 제어를 사용하여 모델, 다이어그램 및 코드 맵 공유**:<br /><br />-코드 맵, 프로젝트 및 종속성 다이어그램을 공유할 수 있도록 Team Foundation 버전 제어에 추가 합니다.| |

각 기능을 지 원하는 Visual Studio의 버전을 확인 하려면 [아키텍처 및 모델링 도구에 대 한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport) 을 참조 하세요.

## <a name="types-of-models-and-typical-uses"></a>모델 유형 및 일반적인 용도

### <a name="code-maps"></a>코드 맵

코드 맵을 통해 코드의 구성과 관계를 확인할 수 있습니다.

**일반적인 용도:**

- 구조 및 종속성, 업데이트 방법을 더 잘 이해할 수 있도록 프로그램 코드를 검사하고 제안된 변경의 비용을 예측합니다.

**참조**

- [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)
- [코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)
- [코드 맵 분석기를 사용하여 잠재적 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagrams"></a>종속성 다이어그램

종속성 다이어그램을 사용 하면 명시적 종속성이 포함 된 레이어 또는 블록 집합으로 응용 프로그램의 구조를 정의할 수 있습니다. 라이브 유효성 검사는 코드의 종속성과 종속성 다이어그램에 설명 된 종속성 간의 충돌을 보여 줍니다.

**일반적인 용도:**

- 애플리케이션 수명 동안 다양한 변경을 통해 애플리케이션 구조를 안정화합니다.
- 코드에 대한 변경을 확인하기 전에 의도하지 않은 종속성 충돌을 검색합니다.

**참조**

- [코드에서 종속성 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)
- [종속성 다이어그램: 참조](../modeling/layer-diagrams-reference.md)
- [종속성 다이어그램을 사용하여 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>DSL(도메인 특정 언어)

DSL은 특정 용도에 맞게 디자인하는 표기법입니다. Visual Studio에서는 일반적으로 그래픽입니다.

**일반적인 용도:**

- 애플리케이션 파트를 생성하거나 구성합니다. 표기법 및 도구를 개발하려면 작업이 필요합니다. 결과는 UML 사용자 지정보다 도메인에 더 적합할 수 있습니다.
- 대규모 프로젝트에 사용되거나, 여러 프로젝트에서 DSL을 사용하여 DSL 및 도구 개발에 대한 투자 수익을 얻는 제품군에 사용됩니다.

**참조**

- [Visual Studio용 모델링 SDK - 도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="see-also"></a>참고 항목

- [Visual Studio 2017의 모델링에 대 한 새로운 기능](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps 및 애플리케이션 수명 주기 관리](/azure/devops/user-guide/devops-alm-overview)
