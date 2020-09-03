---
title: UML API를 사용한 프로그래밍 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, API
- UML model, extending
ms.assetid: c5937139-49d0-4439-8a9f-89f5e0474618
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bdf1111198c7f874d03596382372fe25851e37d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852124"
---
# <a name="programming-with-the-uml-api"></a>Programming with the UML API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 UML API를 통해 UML 모델 및 다이어그램을 만들고 읽고 업데이트할 코드를 작성할 수 있습니다. UML 모델을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

 API 참조 페이지 외에 다음 항목에서 API에 대해 설명합니다.

|항목|설명된 예제 형식 및 메서드|설명된 기능|
|-----------|-----------------------------------------|------------------------|
|[UML API를 사용하여 관계 탐색](../modeling/navigate-relationships-with-the-uml-api.md)|UML 요소와 해당 속성 및 연결. 예: IElement 및 해당 하위 항목(IClass, IActivity, IUseCase, IComponent, IInteraction, IModel, IPackage 포함)|Visual Studio에서 UML 모델은 uml 사양 버전 2.1.2을 따르며 uml [리소스 페이지](https://www.uml.org/)에서 가져올 수 있습니다. 각 형식은 UML 형식과 같은 이름을 사용하고 접두사 "I"이 추가된 인터페이스입니다.|
|[UML 모델에서 요소 및 관계 만들기](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage.CreateClass()<br /><br /> IClass.CreateOperation()|각 요소 형식에는 자식을 만들기 위한 메서드가 있습니다.|
|[다이어그램에 UML 모델 표시](../modeling/display-a-uml-model-on-diagrams.md)|IShape, IDiagram<br /><br /> IShape.Move()|모델의 각 요소는 다이어그램의 모양으로 표현할 수 있습니다. 경우에 따라 각 개체에 대한 새 모양을 만들 수 있습니다. 이들 모양을 이동, 크기 조정, 색 지정하고 축소 또는 확장할 수 있습니다.|
|[UML 모델 탐색](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|모델 저장소에는 모델이 저장됩니다.<br /><br /> 다이어그램 컨텍스트는 현재 다이어그램 및 저장소에 대한 액세스를 제공합니다.|
|[트랜잭션을 사용하여 UML 모델 업데이트 연결](../modeling/link-uml-model-updates-by-using-transactions.md)|ILinkedUndoContext|일련의 변경을 하나의 트랜잭션으로 연결할 수 있습니다.|
|[모델링 다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|IMenuCommand<br /><br /> IGestureExtension<br /><br /> ICommandExtension|두 번 클릭하여 호출되는 명령을 정의하고 다이어그램으로 끌어서 다이어그램 기능을 확장할 수 있습니다.|
|[UML 모델에 대한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md)|ValidationContext|모델이 지정된 제약 조건을 준수하는지 확인하도록 도와주는 유효성 검사 규칙을 정의할 수 있습니다.|
|[IDataObject에서 UML 모델 요소 가져오기](../modeling/get-uml-model-elements-from-idataobject.md)|IElement, IShape|UML 모델 탐색기 또는 UML 다이어그램에서 다른 다이어그램 또는 애플리케이션으로 요소를 끌어 놓으면 요소가 IDataObject로 serialize됩니다.|
|[UML API를 사용하여 UML 시퀀스 다이어그램 편집](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|IInteraction, ILifeline, IMessage|상호 작용 다이어그램을 만들고 업데이트하는 작업은 다른 다이어그램 형식으로 작업하는 것과 약간 다릅니다.|
|[Extend layer diagrams](../modeling/extend-layer-diagrams.md)|ILayer, ILayerDiagram|레이어 다이어그램을 만들고 편집하는 코드를 작성하고 이 코드를 기준으로 프로그램 코드의 유효성을 검사할 수 있습니다.|

## <a name="about-the-implementation"></a>구현 정보
 UML 모델링 도구는 [!INCLUDE[dsl](../includes/dsl-md.md)]에 빌드됩니다. 각 패키지와 각 다이어그램은 [!INCLUDE[dsl](../includes/dsl-md.md)] 모델로 표현되고 이들 간의 일관성은 규칙 및 기타 메서드의 컬렉션을 통해 유지 관리합니다.

 해당 플랫폼의 형식은 UML 확장을 작성하기 위해 참조하는 일부 어셈블리에 표시됩니다. [!INCLUDE[dsl](../includes/dsl-md.md)] API에 액세스하여 UML 도구에 대한 확장을 만들 수 있지만 다음을 고려해야 합니다.

- 일부 간단한 변경으로 인해 불일치 및 예기치 않은 효과가 도입되는 것을 확인할 수 있습니다.

- 구현은 나중에 변경될 수 있으므로 [!INCLUDE[dsl](../includes/dsl-md.md)] API를 사용하여 수행한 적응이 더 이상 작동하지 않을 수 있습니다.

## <a name="the-api-assemblies"></a>API 어셈블리
 다음 표에서는 UML 도구에 대한 확장성을 제공하는 어셈블리 및 사용하는 것이 좋은 네임스페이스에 대해 간략하게 설명합니다.

|어셈블리|네임스페이스|다음에 대한 액세스를 제공합니다.|
|--------------|----------------|-------------------------|
|Microsoft.VisualStudio.Uml.Interfaces|(모두)|UML 형식.|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|VisualStudio. Microsoft.visualstudio.architecturetools.layer.validator|[만들기 메서드](../modeling/create-elements-and-relationships-in-uml-models.md)|
||Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation|[다이어그램 및 모양](../modeling/display-a-uml-model-on-diagrams.md)|
||Microsoft.VisualStudio.ArchitectureTools.Extensibility|[모델링 프로젝트](../modeling/read-a-uml-model-in-program-code.md)|
|Microsoft.VisualStudio.Modeling.Sdk.[version]|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[메뉴 명령 확장](../modeling/define-a-menu-command-on-a-modeling-diagram.md)입니다.<br /><br /> [연결 된 실행 취소 트랜잭션](../modeling/link-uml-model-updates-by-using-transactions.md).|
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[유효성 검사](../modeling/define-validation-constraints-for-uml-models.md)|
||(기타 네임스페이스)|고급 사용에만 권장됩니다.|
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[제스처 처리기](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).|
||(기타 네임스페이스)|고급 사용에만 권장됩니다.|
|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|[작업 항목에 대 한 링크](../modeling/define-a-work-item-link-handler.md)입니다.|
|Microsoft.TeamFoundation.WorkItemTracking.Client|Microsoft.TeamFoundation.WorkItemTracking.Client|[작업 항목 및 해당 필드](../modeling/define-a-work-item-link-handler.md)|
|Microsoft.TeamFoundation.Client|Microsoft.TeamFoundation.Client|[작업 항목 및 해당 필드](../modeling/define-a-work-item-link-handler.md)|
|System.ComponentModel.Composition|<xref:System.ComponentModel.Composition>|[MEF 구성 요소의 내보내기 및 가져오기](../modeling/define-and-install-a-modeling-extension.md)|
|System.Linq|<xref:System.Linq>|[특히 관계를 처리할 때 컬렉션을 쉽게 조작할](../modeling/navigate-relationships-with-the-uml-api.md)수 있습니다.|

## <a name="see-also"></a>관련 항목
 Uml [모델링 확장성에 대 한](../modeling/api-reference-for-uml-modeling-extensibility.md) [uml 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md) API 참조
