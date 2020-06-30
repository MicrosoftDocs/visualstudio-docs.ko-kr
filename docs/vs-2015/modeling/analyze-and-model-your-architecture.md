---
title: 아키텍처 분석 및 모델링 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e00735a180ec951a8afced0f5c74f7a9466e50b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534097"
---
# <a name="analyze-and-model-your-architecture"></a>아키텍처 분석 및 모델링
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 아키텍처 및 모델링 도구를 사용하여 앱을 디자인 및 모델링하는 방식으로 앱이 사용자 요구 사항을 충족하는지 확인합니다. Visual Studio를 사용하여 코드의 구조, 동작 및 관계를 시각화하는 방식으로 기존 프로그램 코드를 더 쉽게 이해할 수 있습니다.

 개발 프로세스의 일부로 애플리케이션 수명 주기 전체에 걸쳐 다양한 상세 수준으로 모델을 만듭니다. 모델 요소를 Team Foundation Server 작업 항목 및 개발 계획에 연결하여 요구 사항, 작업, 테스트 사례, 버그 및 모델과 연결된 기타 작업을 추적합니다. [시나리오: 시각화 및 모델링을 사용 하 여 디자인 변경](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)을 참조 하세요.

 각 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="to"></a>대상

|시나리오|문서|
|-|-|
|**코드 시각화**:<br /><br /> -코드 맵을 만들어 코드의 구성 및 관계를 확인 합니다. 어셈블리, 네임스페이스, 클래스, 메서드 간의 종속성을 시각화합니다.<br />-코드에서 클래스 다이어그램을 만들어 특정 프로젝트에 대 한 클래스 구조 및 멤버를 확인 합니다.<br />-코드의 유효성을 검사 하는 레이어 다이어그램을 만들어 코드와 디자인 간의 충돌을 찾습니다.<br /><br /> **참고**: 이 Visual Studio 릴리스에서는 *종속성 그래프* 대신에 *코드 맵*이 사용됩니다. 단독으로 사용될 경우 *그래프* 는 일반적으로 방향성 그래프 또는 DGML 다이어그램(또는 문서)을 나타냅니다. 코드 맵은 DGML 다이어그램의 특수화된 형식입니다.|-   [코드 시각화](../modeling/visualize-code.md)<br />-   [클래스 및 기타 형식 작업 (클래스 디자이너)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [비디오: 시각화를 통해 코드 종속성 이해 (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understand-your-code-dependencies-through-visualization)<br />-   [비디오: 변경의 영향 시각화 (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Visualize-the-impact-of-a-change)|
|**사용자 요구 사항 설명 및 전달**:<br /><br /> -사용자 스토리, 비즈니스 규칙 및 기타 요구 사항을 명확 하 게 설명 하 고 사용 사례, 활동 및 클래스 다이어그램과 같은 UML 다이어그램을 그려 일관성을 유지 하는 데 도움이 됩니다.|-   [앱에 대 한 모델 만들기](../modeling/create-models-for-your-app.md)<br />-   [사용자 요구 사항 모델링](../modeling/model-user-requirements.md)<br />-   [비디오: 모델링을 통해 아키텍처 개선 (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)|
|**아키텍처 정의**:<br /><br /> -UML 구성 요소, 클래스 및 시퀀스 다이어그램을 그려 소프트웨어 시스템의 대규모 구조와 디자인 패턴을 모델링 합니다.<br />-레이어 다이어그램을 만들어 코드의 구성 요소 간 종속성에 대 한 제약 조건을 정의 하 고 적용 합니다.|-   [앱에 대 한 모델 만들기](../modeling/create-models-for-your-app.md)<br />-   [앱의 아키텍처 모델링](../modeling/model-your-app-s-architecture.md)<br />-   [비디오: 모델링을 통해 아키텍처 개선 (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)<br />-   [비디오: 레이어 다이어그램을 사용 하 여 아키텍처 디자인 및 유효성 검사 (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)|
|**요구 사항 및 의도한 디자인을 사용하여 시스템의 유효성을 검사합니다.**<br /><br /> -요구 사항 모델에 따라 승인 테스트 또는 시스템 테스트를 정의 합니다. 이렇게 하면 테스트와 사용자 요구 사항 간에 강력한 관계가 생성되고 요구 사항이 변경될 때 시스템을 더 쉽게 업데이트할 수 있습니다.<br />-의도 한 아키텍처를 설명 하 고 디자인과 충돌 하는 변경 내용을 방지 하는 레이어 다이어그램을 사용 하 여 코드 종속성의 유효성을 검사 합니다.|-   [개발 하는 동안 시스템 유효성 검사](../modeling/validate-your-system-during-development.md)<br />-   [비디오: 레이어 다이어그램을 사용 하 여 아키텍처 디자인 및 유효성 검사 (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)|
|**Team Foundation 버전 제어를 사용하여 모델, 다이어그램 및 코드 맵 공유**:<br /><br /> -코드 맵, 모델링 프로젝트, UML 다이어그램 및 레이어 다이어그램을 Team Foundation 버전 제어에 배치 하 여 공유할 수 있도록 합니다.|Team Foundation 버전 제어에서 이들 항목을 사용하는 여러 사용자가 있으면 지침에 따라 버전 제어 문제를 방지합니다.<br /><br /> -   [버전 제어에서 모델 및 다이어그램 관리](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**UML 및 도메인 특정 언어에서 애플리케이션 파트 생성 또는 구성**:<br /><br /> -디자인을 요구 사항에 맞게 변경 하 고 제품 라인에서 쉽게 변수에 대 한 응답성을 향상 합니다.|-   [모델에서 앱 생성 및 구성](../modeling/generate-and-configure-your-app-from-models.md)|
|**모델 및 다이어그램 사용자 지정**:<br /><br /> -UML 요소에 대 한 추가 속성을 정의 하 고 모델이 비즈니스 규칙을 준수 하는지 확인 하는 유효성 검사 제약 조건, 추가 메뉴 명령 및 도구 상자 항목을 정의 하 여 프로젝트에서 모델을 사용 하는 방법에 대 한 모델을 조정<br />-도메인 특정 언어를 만듭니다.|-   [UML 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Visual Studio 용 모델링 SDK-도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**T4 템플릿을 사용하여 텍스트 생성**:<br /><br /> -텍스트 블록 및 템플릿 내에서 컨트롤 논리를 사용 하 여 텍스트 기반 파일을 생성 합니다.|-   [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>모델 형식 및 해당 용도

|**모델 형식 및 일반적인 용도**|
|-------------------------------------|
|**코드 맵**<br /><br /> 코드 맵을 통해 코드의 구성과 관계를 확인할 수 있습니다.<br /><br /> 일반적인 용도:<br /><br /> -구조와 종속성을 더 잘 이해할 수 있도록 프로그램 코드를 검사 하 고, 업데이트 하 고, 제안 된 변경 비용을 예측 합니다.<br /><br /> 참조<br /><br /> -   [솔루션 전체에서 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)<br />-   [코드 맵을 사용 하 여 응용 프로그램 디버그](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [코드 맵 분석기를 사용 하 여 잠재적인 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**레이어 다이어그램**<br /><br /> 레이어 다이어그램을 통해 애플리케이션 구조를 명시적 종속성이 포함된 레이어 또는 블록 집합으로 정의할 수 있습니다. 유효성 검사를 실행하여 코드의 종속성과 레이어 다이어그램에 설명된 종속 간 충돌을 검색할 수 있습니다.<br /><br /> 일반적인 용도:<br /><br /> -수명 동안 많은 변경 내용을 적용 하 여 응용 프로그램의 구조를 안정화 합니다.<br />-코드에 대 한 변경 내용을 체크 인하기 전에 의도 하지 않은 종속성 충돌을 검색 합니다.<br /><br /> 참조<br /><br /> -   [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [레이어 다이어그램: 참조](../modeling/layer-diagrams-reference.md)<br />-   [레이어 다이어그램을 사용 하 여 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)|
|**UML 모델**<br /><br /> UML 모델에는 클래스, 구성 요소, 사용 사례, 동작 및 시퀀스 다이어그램을 비롯한 여러 뷰가 포함됩니다. 애플리케이션 도메인에 맞게 UML을 사용자 지정할 수 있습니다. 예를 들어 태그, 추가 정보 및 제약 조건을 모델 요소에 연결할 수 있습니다. 모델에서 작동하는 도구를 정의할 수도 있습니다. [앱에 대 한 모델 만들기](../modeling/create-models-for-your-app.md)를 참조 하세요.<br /><br /> 일반적인 용도:<br /><br /> -요구 사항 및 디자인을 설명 합니다. 애플리케이션 개발에 UML을 빠르게 적용할 수 있습니다. [개발 프로세스에서 모델 사용](../modeling/use-models-in-your-development-process.md)을 참조 하세요.<br />-테스트 또는 응용 프로그램의 일부를 생성 하거나 구성 합니다. 표기법을 사용자 지정하고 생성 템플릿 또는 구성 가능한 애플리케이션을 개발하려면 몇 가지 작업이 필요합니다. [모델에서 앱 생성 및 구성](../modeling/generate-and-configure-your-app-from-models.md)을 참조 하세요.<br />-일반적인 설명 및 작은 프로젝트의 코드 생성 또는 구성에 대해 설명 합니다.|
|**DSL(도메인 특정 언어)**<br /><br /> DSL은 특정 용도에 맞게 디자인하는 표기법입니다. Visual Studio에서는 일반적으로 그래픽으로 표시됩니다.<br /><br /> 일반적인 용도:<br /><br /> -응용 프로그램의 일부를 생성 하거나 구성 합니다. 표기법 및 도구를 개발하려면 작업이 필요합니다. 결과는 UML 사용자 지정보다 도메인에 더 적합할 수 있습니다.<br />-여러 프로젝트에서 사용 하는 경우 DSL 및 도구를 개발 하는 데 따른 투자가 반환 되는 대량 프로젝트 또는 제품 라인의 경우<br /><br /> 참조<br /><br /> -   [Visual Studio 용 모델링 SDK-도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>추가 정보는 어디서 확인할 수 있나요?

|리소스|링크|
|-|-|
|**포럼**|-   [Visual Studio 시각화 및 모델링 도구](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio 시각화 및 모델링 SDK(DSL 도구)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>참고 항목

- [Visual Studio 2015의 모델링에 대 한 새로운 기능](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps 및 애플리케이션 수명 주기 관리](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
