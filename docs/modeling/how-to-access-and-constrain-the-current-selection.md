---
title: '방법: 현재 선택 항목 액세스 및 제약'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1f5aaa106e00f9b10eb88892bcc978b92a01c79
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545693"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>방법: 현재 선택 항목 액세스 및 제약

도메인 특정 언어에 대 한 명령 또는 제스처 처리기를 작성 하는 경우 사용자가 마우스 오른쪽 단추로 클릭 한 요소를 확인할 수 있습니다. 일부 셰이프나 필드가 선택 되지 않도록 할 수도 있습니다. 예를 들어 사용자가 아이콘 데코레이터를 클릭 하면이를 포함 하는 도형이 대신 선택 되도록 정렬할 수 있습니다. 이러한 방식으로 선택 범위를 제한 하면 써야 하는 처리기 수가 줄어듭니다. 또한 사용자가 데코레이터를 방지 하지 않고도 셰이프의 아무 곳 이나 클릭 하 여 더 쉽게 작업할 수 있습니다.

## <a name="access-the-current-selection-from-a-command-handler"></a>명령 처리기에서 현재 선택 영역에 액세스 합니다.

도메인 특정 언어에 대 한 명령 집합 클래스에는 사용자 지정 명령에 대 한 명령 처리기가 포함 되어 있습니다. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>도메인 특정 언어에 대 한 명령 집합 클래스가 파생 되는 클래스는 현재 선택 항목에 액세스 하기 위한 몇 가지 멤버를 제공 합니다.

명령에 따라 명령 처리기가 모델 디자이너, 모델 탐색기 또는 활성 창에서 선택 해야 할 수 있습니다.

### <a name="to-access-selection-information"></a>선택 정보에 액세스 하려면

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>클래스는 현재 선택 영역에 액세스 하는 데 사용할 수 있는 다음 멤버를 정의 합니다.

    |멤버|설명|
    |-|-|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> 메서드|`true`모델 디자이너에서 선택한 요소가 구획 모양이 면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> 메서드|`true`모델 디자이너에서 다이어그램이 선택 되어 있으면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> 메서드|`true`모델 디자이너에서 정확히 하나의 요소만 선택 하면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> 메서드|`true`활성 창에서 정확히 하나의 요소가 선택 되어 있으면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> 속성|모델 디자이너에서 선택한 요소의 읽기 전용 컬렉션을 가져옵니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> 속성|활성 창에서 선택한 요소의 읽기 전용 컬렉션을 가져옵니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> 속성|모델 디자이너에서 선택 항목의 기본 요소를 가져옵니다.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> 속성|활성 창에서 선택 영역의 기본 요소를 가져옵니다.|

2. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A>클래스의 속성은 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 모델 디자이너 창을 나타내는 개체에 대 한 액세스를 제공 하 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> 고 모델 디자이너에서 선택 된 요소에 대 한 추가 액세스를 제공 합니다.

3. 또한 생성 된 코드는 도메인 특정 언어에 대 한 명령 집합 클래스에서 탐색기 도구 창 속성 및 탐색기 선택 속성을 정의 합니다.

    - 탐색기 도구 창 속성은 도메인별 언어에 대 한 탐색기 도구 창 클래스의 인스턴스를 반환 합니다. 탐색기 도구 창 클래스는 클래스에서 파생 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> 되며 도메인별 언어의 모델 탐색기를 나타냅니다.

    - `ExplorerSelection`속성은 도메인 특정 언어에 대 한 모델 탐색기 창에서 선택한 요소를 반환 합니다.

## <a name="determine-which-window-is-active"></a>활성화 된 창을 확인 합니다.

인터페이스에는 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 셸에서 현재 선택 상태에 대 한 액세스를 제공 하는 멤버를 정의 합니다. <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> `MonitorSelection` 각의 기본 클래스에 정의 된 속성을 통해 도메인별 언어에 대 한 패키지 클래스 또는 명령 집합 클래스에서 개체를 가져올 수 있습니다. Package 클래스는 클래스에서 파생 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> 되 고 명령 집합 클래스는 클래스에서 파생 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 됩니다.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>명령 처리기에서 활성화 되는 창 유형을 확인 하려면

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>클래스의 속성은 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 셸에서 현재 선택 상태에 대 한 액세스를 제공 하는 개체를 반환 합니다.

2. <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A>인터페이스의 속성은 활성 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 창과 다를 수 있는 활성 선택 컨테이너를 가져옵니다.

3. 도메인 특정 언어의 명령 집합 클래스에 다음 속성을 추가 하 여 활성 상태인 창 유형을 결정 합니다.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>선택 영역 제한

선택 규칙을 추가 하 여 사용자가 모델에서 요소를 선택할 때 선택할 요소를 제어할 수 있습니다. 예를 들어 사용자가 여러 요소를 단일 단위로 처리할 수 있도록 하려면 선택 규칙을 사용할 수 있습니다.

### <a name="to-create-a-selection-rule"></a>선택 규칙을 만들려면

1. DSL 프로젝트에서 사용자 지정 코드 파일 만들기

2. 클래스에서 파생 되는 선택 규칙 클래스를 정의 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> 합니다.

3. 선택 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> 조건을 적용 하려면 selection 규칙 클래스의 메서드를 재정의 합니다.

4. ClassDiagram 클래스의 partial 클래스 정의를 사용자 지정 코드 파일에 추가 합니다.

     `ClassDiagram`클래스는 클래스에서 파생 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> 되며, DSL 프로젝트에서 생성 된 코드 파일 Diagram.cs에 정의 됩니다.

5. <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A>클래스의 속성을 재정의 `ClassDiagram` 하 여 사용자 지정 선택 규칙을 반환 합니다.

     속성의 기본 구현에서는 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> 선택 항목을 수정 하지 않는 선택 규칙 개체를 가져옵니다.

### <a name="example"></a>예제

다음 코드 파일은 선택 영역을 확장 하 여 처음 선택 된 각 도메인 셰이프의 모든 인스턴스를 포함 하는 선택 규칙을 만듭니다.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>