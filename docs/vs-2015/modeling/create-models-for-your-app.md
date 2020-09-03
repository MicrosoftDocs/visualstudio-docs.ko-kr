---
title: 앱에 대 한 모델 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7e1b37a357113be010ea336fc5666beb8cd33dbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852017"
---
# <a name="create-models-for-your-app"></a>앱용 모델 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모델링 다이어그램을 통해 코드에 대한 아이디어 및 소프트웨어 시스템에서 지원해야 하는 사용자 요구 사항을 이해하고 분명히 설명하고 전달할 수 있습니다. 예를 들어 사용자 요구 사항을 설명 및 전달하려면 UML(Unified Modeling Language) 사용 사례, 동작, 클래스 및 시퀀스 다이어그램을 사용하면 됩니다. 시스템 기능을 설명 및 전달하려면 UML 구성 요소, 클래스, 동작 및 시퀀스 다이어그램을 사용하면 됩니다.

 [Channel 9 비디오: 모델링을 통해 아키텍처 향상](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)을 참조 하세요.

 이 릴리스에서 다음 UML 다이어그램을 만들 수 있습니다.

|**다이어그램**|**보여 주는 것**|
|-----------------|---------------|
|[UML 동작 다이어그램: 참조](../modeling/uml-activity-diagrams-reference.md)|비즈니스 프로세스의 작업과 참가자 간 작업 흐름|
|[UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)|시스템, 해당 인터페이스, 포트 및 관계의 구성 요소|
|[UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)|시스템 및 해당 관계에서 데이터를 저장하고 교환하는 데 사용되는 형식|
|[UML 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)|개체, 구성 요소, 시스템 또는 행위자 간 상호 작용의 시퀀스|
|[UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)|시스템이 지원하는 사용자 목표 및 작업|

 각 종류의 다이어그램을 지 원하는 Visual Studio 버전을 확인 하려면 [아키텍처 및 모델링 도구에 대 한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조 하세요.

 시스템 또는 기존 코드의 아키텍처를 시각화하려면 다음 다이어그램을 만듭니다.

|**다이어그램**|**보여 주는 것**|
|-----------------|---------------|
|[레이어 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)<br /><br /> [레이어 다이어그램: 참조](../modeling/layer-diagrams-reference.md)|시스템의 상위 수준 아키텍처|
|코드 맵<br /><br /> [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [코드 맵 분석기를 사용하여 잠재적 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)|기존 코드의 종속성 및 기타 관계|
|코드에서 생성된 클래스 다이어그램<br /><br /> [클래스 다이어그램 사용(클래스 디자이너)](../ide/working-with-class-diagrams-class-designer.md)|.NET 코드의 형식 및 해당 관계|

## <a name="common-tasks"></a>일반 태스크

|**항목**|**Task**|
|---------------|--------------|
|[UML 모델링 프로젝트 및 다이어그램 만들기](../modeling/create-uml-modeling-projects-and-diagrams.md)|**모델을 만들고** 다이어그램을 추가 합니다.|
|[UML 모델 및 다이어그램 편집](../modeling/edit-uml-models-and-diagrams.md)|**다이어그램을 그려** 모델을 편집 합니다.|
|[패키지 및 네임스페이스 정의](../modeling/define-packages-and-namespaces.md)|다른 팀 멤버가 작업할 수 있는 단위로 모델을 분할 하는 **패키지를 만듭니다** .|
|[UML 클래스 다이어그램에서 코드 생성](../modeling/generate-code-from-uml-class-diagrams.md)|**클래스 다이어그램에서 c # 코드를 생성** 하 여 구현을 시작 합니다.|
|[프로필 및 스테레오타입을 사용하여 모델 사용자 지정](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|스테레오 타입을 사용 하 여 **모델 요소를 사용자 지정** 하 여 특정 용도에 맞게 표준 UML 모델 요소를 확장 합니다.|
|[모델 요소 및 작업 항목 연결](../modeling/link-model-elements-and-work-items.md)|작업, 테스트 사례, 버그, 요구 사항, 문제 또는 모델의 특정 부분과 연결 된 다른 종류의 작업을 추적 하는 데 도움이 되도록 **모델 요소와 작업 항목 간에 링크를 만듭니다** .|
|[다이어그램을 이미지로 내보내기](../modeling/export-diagrams-as-images.md)|를 사용 하지 않는 사용자를 포함 하 여 다른 사용자와 공유할 수 있도록 **모델 및 다이어그램을 저장** [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] 합니다.|

## <a name="related-tasks"></a>관련 작업

|**항목**|**Task**|
|---------------|--------------|
|[코드 시각화](../modeling/visualize-code.md)|친숙하지 않은 코드를 더 잘 이해하도록 코드 맵과 레이어 다이어그램을 만듭니다.|
|[사용자 요구 사항 모델링](../modeling/model-user-requirements.md)|모델을 사용하여 사용자 요구 사항을 분명히 설명하고 전달합니다.|
|[앱의 아키텍처 모델링](../modeling/model-your-app-s-architecture.md)|모델을 사용하여 시스템의 전체 구조 및 동작을 설명하고 사용자 요구 사항에 맞는지 확인합니다.|
|[개발하는 동안 시스템 유효성 검사](../modeling/validate-your-system-during-development.md)|소프트웨어와 사용자 요구 사항 및 전체 시스템 아키텍처의 일관성이 유지되는지 확인합니다.|
|[개발 프로세스에서 모델 사용](../modeling/use-models-in-your-development-process.md)<br /><br /> [Agile 개발에서 모델 사용](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)|모델을 사용하여 개발하는 동안 시스템을 이해하고 변경하도록 도와줍니다.|
|[모델링 솔루션 구성](../modeling/structure-your-modeling-solution.md)|대규모 또는 중간 규모 프로젝트에서 모델을 구성합니다.|

## <a name="external-resources"></a>외부 리소스

|**범주**|**연결**|
|------------------|---------------|
|**포럼**|-   [Visual Studio 시각화 및 모델링 도구](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio 시각화 및 모델링 SDK(DSL 도구)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
