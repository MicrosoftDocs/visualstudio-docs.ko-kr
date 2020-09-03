---
title: 프로그램 코드에서 레이어 모델 탐색 및 업데이트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 88ab52f1b06e6a2da94d17225bdb26ecec358a6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668567"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>프로그램 코드에서 레이어 모델 탐색 및 업데이트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 프로그램 코드를 사용하여 탐색하고 업데이트할 수 있는 레이어 모델의 요소와 관계에 대해 설명합니다. 사용자의 관점에서 레이어 다이어그램에 대 한 자세한 내용은 [레이어 다이어그램: 참조](../modeling/layer-diagrams-reference.md) 및 [레이어 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)을 참조 하세요.

 이 항목에서 설명하는 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` 모델은 보다 일반적인 <xref:Microsoft.VisualStudio.GraphModel> 모델의 단순한 버전입니다. [메뉴 명령 또는 제스처 확장](../modeling/add-commands-and-gestures-to-layer-diagrams.md)을 작성 하는 경우에는 모델을 사용 `Layer` 합니다. [레이어 유효성 검사 확장](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)을 작성 하는 경우를 사용 하는 것이 더 쉽습니다 `GraphModel` .

## <a name="transactions"></a>트랜잭션
 모델을 업데이트할 때는 `ILinkedUndoTransaction`에 변경 내용을 포함할 수도 있습니다. 그러는 경우 변경 내용이 트랜잭션 하나로 그룹화됩니다. 변경 중 하나라도 실패하면 전체 트랜잭션이 롤백됩니다. 사용자가 변경 하나를 실행 취소하면 모든 변경이 함께 실행 취소됩니다.

 자세한 내용은 [트랜잭션을 사용 하 여 UML 모델 업데이트 링크](../modeling/link-uml-model-updates-by-using-transactions.md)를 참조 하세요.

```
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Containment
 ![ILayer 및 ILayerModel 모두에 ILayer가 포함될 수 있음](../modeling/media/layerapi-containment.png "LayerApi_Containment")

 계층 ([ILayer](/previous-versions/ff644251(v=vs.140))) 및 레이어 모델 ([Ilayermodel](/previous-versions/ff643069(v=vs.140)))에는 주석과 레이어가 포함 될 수 있습니다.

 레이어(`ILayer`)는 레이어 모델(`ILayerModel`)에 포함될 수도 있고 다른 `ILayer` 내에 중첩될 수도 있습니다.

 주석이나 레이어를 만들려면 해당 컨테이너에 대해 creation 메서드를 사용합니다.

## <a name="dependency-links"></a>종속성 링크
 종속성 링크는 개체로 표시되며 양방향으로 탐색할 수 있습니다.

 ![ILayerDependencyLink가 두 ILayer를 연결함](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")

 종속성 링크를 만들려면 `source.CreateDependencyLink(target)`를 호출합니다.

## <a name="comments"></a>주석
 주석은 레이어 또는 레이어 모델에 포함될 수 있으며 레이어 요소에 연결할 수도 있습니다.

 ![모든 레이어 요소에 주석을 연결할 수 있음](../modeling/media/layerapi-comments.png "LayerApi_Comments")

 원하는 수만큼의 요소에 주석을 연결하거나 아무 요소에 연결하지 않을 수도 있습니다.

 레이어 요소에 연결된 주석을 가져오려면 다음 코드를 사용합니다.

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));

```

> [!CAUTION]
> `Comments`의 `ILayer` 속성은 `ILayer` 내에 포함된 주석을 가져옵니다. 그러나 이 속성은 그에 연결된 주석은 가져오지 않습니다.

 해당하는 컨테이너에서 `CreateComment()`를 호출하여 주석을 만듭니다.

 주석에 대해 `CreateLink()`를 사용하여 링크를 만듭니다.

## <a name="layer-elements"></a>레이어 요소
 모델에 포함할 수 있는 모든 형식의 요소는 레이어 요소입니다.

 ![레이어 다이어그램 내용이 ILayerElement임](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")

## <a name="properties"></a>속성
 각 `ILayerElement`에는 `Properties`라는 문자열 디렉터리가 있습니다. 이 디렉터리를 사용하여 임의의 정보를 레이어 요소에 연결할 수 있습니다.

## <a name="artifact-references"></a>아티팩트 참조
 아티팩트 참조 ([Ilayerartifactreference](/previous-versions/ff644536(v=vs.140)))는 레이어와 파일, 클래스 또는 폴더와 같은 프로젝트 항목 간의 링크를 나타냅니다. 사용자는 레이어를 만들거나 솔루션 탐색기, 클래스 뷰 또는 개체 브라우저에서 레이어 다이어그램으로 항목을 끌어서 레이어를 추가할 때 아티팩트를 만듭니다. 아티팩트 참조는 원하는 수만큼 레이어에 연결할 수 있습니다.

 레이어 탐색기의 각 행은 아티팩트 참조를 표시합니다. 자세한 내용은 [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)를 참조 하세요.

 아티팩트 참조와 관련된 기본 형식 및 메서드는 다음과 같습니다.

 [Ilayerartifactreference](/previous-versions/ff644536(v=vs.140)). Categories 속성은 클래스, 실행 파일, 어셈블리 등 참조되는 아티팩트의 종류를 나타내며 식별자가 대상 아티팩트를 식별하는 방법을 결정합니다.

 [CreateArtifactReferenceAsync](/previous-versions/ff695840(v=vs.140)) 는 또는에서 아티팩트 참조를 만듭니다. <xref:EnvDTE.Project> <xref:EnvDTE.ProjectItem> 이 작업은 비동기 작업입니다. 그러므로 만들기가 완료되면 일반적으로 호출될 콜백을 제공합니다.

 레이어 아티팩트 참조를 사용 사례 다이어그램의 아티팩트와 혼동해서는 안 됩니다.

## <a name="shapes-and-diagrams"></a>모양 및 다이어그램
 계층 모델의 각 요소를 나타내는 데 사용 되는 두 개체는 `ILayerElement` 및 [ishape](/previous-versions/ee806673(v=vs.140))입니다. `IShape`는 다이어그램의 모양 크기와 위치를 나타냅니다. 레이어 모델의 모든 `ILayerElement`마다 `IShape` 하나가 있고 레이어 다이어그램의 모든 `IShape`마다 `ILayerElement` 하나가 있습니다. `IShape`는 UML 모델에도 사용됩니다. 그러므로 모든 `IShape`에 레이어 요소가 있는 것은 아닙니다.

 동일한 방식으로 `ILayerModel` 가 하나의 [idiagram 다이어그램](/previous-versions/ee789658(v=vs.140))에 표시 됩니다.

 사용자 지정 명령 또는 제스처 처리기의 코드에서는 `DiagramContext` 가져오기에서 현재 다이어그램 및 현재 모양 선택을 가져올 수 있습니다.

```
public class ... {
[Import]
    public IDiagramContext DiagramContext { get; set; }
...
public void ... (...)
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;
  ILayerModel model = diagram.GetLayerModel();
  if (model != null)
  { foreach (ILayer layer in model.Layers) { ... }}
  foreach (IShape selected in diagram.SelectedShapes)
  { ILayerElement element = selected.GetLayerElement();
    if (element != null) ... }}
```

 ![각 ILayerElement에 대해 IShape가 표시됨](../modeling/media/layerapi-shapes.png)

 [Ishape](/previous-versions/ee806673(v=vs.140)) 및 [ishape](/previous-versions/ee789658(v=vs.140)) UML 모델을 표시 하는 데도 사용 됩니다. 자세한 내용은 [다이어그램에 UML 모델 표시](../modeling/display-a-uml-model-on-diagrams.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보

- [레이어 다이어그램에 명령 및 제스처 추가](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [레이어 다이어그램에 사용자 지정 아키텍처 유효성 검사 추가](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [레이어 다이어그램에 사용자 지정 속성 추가](../modeling/add-custom-properties-to-layer-diagrams.md)
- [레이어 다이어그램: 참조](../modeling/layer-diagrams-reference.md)
- [레이어 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)
- [UML 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md)
