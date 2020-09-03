---
title: UML 모델 탐색 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23f87c81e43b2dfafb1c9c78c3135faff809bb9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74289855"
---
# <a name="navigate-the-uml-model"></a>UML 모델 탐색
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 UML 모델의 주요 형식을 소개합니다.

## <a name="the-model-elements-model-and-model-store"></a>모델 요소, 모델 및 모델 저장소
 **Microsoft.VisualStudio.Uml.Interfaces.dll** 어셈블리에 정의 된 형식은 [UML 사양 버전 2.1.2](https://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/)에 정의 된 형식에 해당 합니다.

 UML 사양의 형식은 Visual Studio에서 인터페이스로 인식됩니다. 각 형식의 이름 앞에 'I' 문자가 추가됩니다. 예: [IElement](/previous-versions/dd516035(v=vs.140)), [IClass](/previous-versions/dd523539%28v%3dvs.140%29), [ioperation](/previous-versions/dd481186(v=vs.140)).

 IElement를 제외한 모든 형식은 하나 이상의 상위 형식에서 속성을 상속합니다.

- 모델 형식에 대 한 요약은 [UML 모델 요소 형식](../modeling/uml-model-element-types.md)을 참조 하세요.

- API에 대 한 자세한 내용은 [UML 모델링 확장성에 대 한 Api 참조](../modeling/api-reference-for-uml-modeling-extensibility.md)를 참조 하세요.

### <a name="relationships"></a>관계
 UML 사양에 정의된 속성 및 관계는 .NET 속성으로 구현됩니다.

 대부분의 관계는 양방향으로 탐색할 수 있습니다. 관계는 양쪽 끝에 형식의 속성이 하나씩 있는 한 쌍의 속성에 해당합니다. 예를 들어 `IElement.Owner` 및 `IElement.OwnedElements` 속성은 관계의 양쪽 끝을 나타냅니다. 따라서 다음 식은 항상 true로 평가됩니다.

 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`

 IAssociation과 같은 대부분의 관계는 고유한 속성을 가질 수 있는 개체로도 표시됩니다.

 모델에서 요소를 삭제하면 참여하는 관계도 자동으로 삭제되고 반대쪽 속성이 업데이트됩니다.

 UML 사양에서 속성에 복합성 0..1을 할당하는 경우 `null` 값을 가질 수 있습니다. 복합성이 1 보다 큰 복합성은 .NET 속성의 형식은 형식 `IEnumerable<` *Type* `>` 입니다.

 관계 트래버스에 대 한 자세한 내용은 [UML API를 사용 하 여 관계 탐색](../modeling/navigate-relationships-with-the-uml-api.md)을 참조 하세요.

### <a name="the-ownership-tree"></a>소유권 트리
 모델에는 [IElement](/previous-versions/dd516035(v=vs.140)) 개체의 트리가 포함 되어 있습니다. 모든 요소에 `OwnedElements` 및 `Owner` 속성이 있습니다.

 대부분의 경우 `Owner` 및 `OwnedElements` 속성의 대상은 보다 구체적인 이름을 가진 다른 속성에서도 참조됩니다. 예를 들어 모든 UML 작업은 UML 클래스가 소유합니다. 따라서 [ioperation에](/previous-versions/dd481186(v=vs.140)) 는 [Ioperation. 클래스](/previous-versions/dd473473%28v%3dvs.140%29)및 모든 [ioperation](/previous-versions/dd481186(v=vs.140)) 개체의 속성이 `Class == Owner` 있습니다.

 소유자가 없는 트리의 최상위 요소는 `AuxiliaryConstructs.IModel` 입니다. IModel는에 포함 되어 `IModelStore` 있습니다. 여기서는 [Imodelstore. Root](/previous-versions/ee789368(v=vs.140))입니다.

 모든 모델 요소는 소유자를 사용하여 생성됩니다. 자세한 내용은 [UML 모델에서 요소 및 관계 만들기](../modeling/create-elements-and-relationships-in-uml-models.md)를 참조 하세요.

 ![클래스 다이어그램: 모델, 다이어그램, 도형 및 요소](../modeling/media/uml-mm1.png)

## <a name="shapes-and-diagrams"></a>모양 및 다이어그램
 UML 모델의 요소를 다이어그램에 표시할 수 있습니다. 각 형식의 다이어그램에 IElement의 다른 하위 형식이 표시될 수 있습니다.

 한 요소는 두 개 이상의 다이어그램에 나타나는 경우도 있습니다. 예를 들어 IUseCase 요소는 한 다이어그램이나 여러 다이어그램에 표시될 수 있는 여러 Ishape를 포함할 수 있습니다.

 모양은 트리로 정렬됩니다. 트리의 가장자리는 ParentShape 및 ChildShapes 속성으로 표시됩니다. 다이어그램은 부모가 없는 유일한 모양입니다. 다이어그램 화면의 모양은 더 작은 파트로 구성됩니다. 예를 들어 클래스 모양에는 특성 및 작업 구획이 있습니다.

 도형에 대 한 자세한 내용은 [다이어그램에 UML 모델 표시](../modeling/display-a-uml-model-on-diagrams.md)를 참조 하세요.

## <a name="access-to-the-model-in-extensions"></a>확장에서 모델 액세스
 MEF 구성 요소로 정의된 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장에서 확장이 실행되는 컨텍스트의 정보를 가져오는 속성을 선언할 수 있습니다.

|특성 유형|다음에 대한 액세스 제공|추가 정보|
|--------------------|----------------------------------|----------------------|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation<br /><br /> .IDiagramContext<br /><br /> (Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll)|현재 포커스 다이어그램입니다.|[모델링 다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|
|Microsoft.VisualStudio.Modeling.ExtensionEnablement<br /><br /> .ILinkedUndoContext<br /><br /> (in Microsoft.VisualStudio.Modeling.Sdk.[version].dll)|변경 내용을 트랜잭션으로 그룹화할 수 있습니다.|[트랜잭션을 사용하여 UML 모델 업데이트 연결](../modeling/link-uml-model-updates-by-using-transactions.md)|
|Microsoft.VisualStudio.Shell .SVsServiceProvider<br /><br /> (in Microsoft.VisualStudio.Shell.Immutable.[version].dll)|호스트 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]입니다. 여기서 파일, 프로젝트 및 기타 측면에 액세스할 수 있습니다.|[Visual Studio API를 사용하여 UML 모델 열기](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|

### <a name="to-get-the-context"></a>컨텍스트를 가져오려면
 확장 클래스 내에서 다음 인터페이스 중 하나 또는 둘 다를 선언합니다.

```
[Import] public IDiagramContext DiagramContext { get; set; }

```

 MEF(Managed Extensibility Framework)는 이러한 인터페이스를 현재 다이어그램, 모델 저장소, 루트 개체 등을 가져올 수 있는 정의에 바인딩합니다.

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
IClassDiagram classDiagram = diagram as IClassDiagram;
       // or diagrams of other types
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

### <a name="to-get-the-current-selection"></a>현재 선택 항목을 지우려면

```
// All selected shapes and their elements
foreach (IShape shape in diagram.SelectedShapes)
{
   IDiagram selectedDiagram = shape as IDiagram;
   if (selectedDiagram != null)
   { // no shape selected - user right-clicked the diagram
     ... Context.CurrentDiagram ...
   }
   else
   {
     IElement selectedElement = shape.Element;
   ...}
// All selected shapes that display a specfic type of element
foreach (IShape<IInterface> in
   diagram.GetSelectedShapes<IInterface>())
{...}
```

## <a name="accessing-another-model-or-diagrams"></a>다른 모델 또는 다이어그램 액세스
 다음과 같습니다.

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 모델 버스를 사용하여 서로 다른 모델의 요소 간에 링크를 만듭니다. 자세한 내용은 [UML 모델을 다른 모델 및 도구와 통합](../modeling/integrate-uml-models-with-other-models-and-tools.md)을 참조 하세요.

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 사용자 인터페이스에 표시하지 않고 모델링 프로젝트 및 다이어그램을 읽기 전용 모드로 로드합니다. 자세한 내용은 [프로그램 코드에서 UML 모델 읽기](../modeling/read-a-uml-model-in-program-code.md)를 참조 하세요.

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 모델링 프로젝트 및 다이어그램을 열고 내용에 액세스합니다. 자세한 내용은 [Visual STUDIO API를 사용 하 여 UML 모델 열기](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보

- [UML 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md)
- [Programming with the UML API](../modeling/programming-with-the-uml-api.md)
