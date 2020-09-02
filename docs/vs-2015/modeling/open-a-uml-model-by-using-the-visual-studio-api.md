---
title: Visual Studio API를 사용 하 여 UML 모델 열기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 694f10fb0af440513331aa6e76dbf9a59a16d340
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668503"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Visual Studio API를 사용하여 UML 모델 열기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

API를 사용하여 Visual Studio 사용자 인터페이스에서 모델 및 다이어그램을 열 수도 있습니다.

 사용자에게 표시하지 않고 프로그램 코드에서 모델을 읽기만 하려는 경우 다음 메서드를 사용할 수 있습니다.

- Visual Studio 모델 버스는 내부 모델 및 요소에 액세스할 수 있게 해주며 모델 간에 링크를 만드는 표준 방법을 제공합니다. 자세한 내용은 [UML 모델을 다른 모델 및 도구와 통합](../modeling/integrate-uml-models-with-other-models-and-tools.md)을 참조 하세요.

- 읽기 전용 모드에서 모델을 열 수 있습니다. 자세한 내용은 [프로그램 코드에서 UML 모델 읽기](../modeling/read-a-uml-model-in-program-code.md)를 참조 하세요.

## <a name="opening-models-and-diagrams-in-visual-studio"></a><a name="Showing"></a> Visual Studio에서 모델 및 다이어그램 열기
 사용자 인터페이스에서 모델을 열려면 표준 Visual Studio API `EnvDTE.DTE`를 사용합니다. 모델링 프로젝트 항목에 대해 수행할 수 있는 두 가지 유용한 캐스트가 있습니다.

- `EnvDTE.Project``IModelingProject`프로젝트가 모델링 프로젝트이 고 프로젝트가 현재 AppDomain에 로드 된 경우에는에서 캐스팅할 수 있습니다.

- `EnvDTE.ProjectItem` 항목이 UML 다이어그램인 경우에서로 캐스팅할 수 있습니다 `IDiagramContext` .

  다음 예제에서는 프로젝트가 아래 참조를 가져와야 합니다.

- EnvDTE

- Microsoft.VisualStudio.ArchitectureTools.Extensibility

- Microsoft.VisualStudio.Modeling.Sdk.[version]

- Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]

- Microsoft.VisualStudio.Shell.Immutable.[version]

- Microsoft.VisualStudio.Uml.Interfaces

- System.ComponentModel.Composition

  이 예제에서는 Visual Studio에서 UML 모델을 엽니다.

```
using EnvDTE; // Visual Studio API for loading diagrams
using
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   // for ICommandExtension and other handler types
using Microsoft.VisualStudio.Uml.Classes;
   // for basic UML types
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   // for model construction methods
using EnvDTE;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
                             // for IDiagram
...
```

 Visual Studio 확장에서 이 선언을 만들어 호스트 서비스 공급자에 액세스할 수 있습니다.

```
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}
...
```

 메서드에서 현재 프로젝트 등의 프로젝트에 액세스할 수 있습니다.

```
DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;
IModelingProject modelingProject = project as IModelingProject;
if (modelingProject == null) return; // not a modeling project

// Access the model's store and contents.
IModelStore store = modelingProject.Store;
foreach (IElement element in store.Root.OwnedElements) {...}

// Open all the project's diagrams.
foreach (ProjectItem item in project.ProjectItems)
{
     IDiagramContext modelingItem = item as IDiagramContext;
     if (modelingItem == null)
         continue; // not a model diagram
     IDiagram diagram = modelingItem.CurrentDiagram;
     if (diagram == null)
     {
        // Diagram is closed. Open it.
        item.Open().Activate();
        diagram = modelingItem.CurrentDiagram;
     }
     // Access the shapes.
     foreach (IShape<IElement> shape
               in diagram.GetChildShapes<IElement>())
     {
       IElement displayedElement = shape.Element;
       ...
     }
   }
}
```

## <a name="see-also"></a>관련 항목
 Uml [API를 사용한 프로그래밍으로](../modeling/programming-with-the-uml-api.md) [uml 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md)
