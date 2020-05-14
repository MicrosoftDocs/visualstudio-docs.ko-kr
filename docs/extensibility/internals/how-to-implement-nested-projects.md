---
title: '방법: 중첩 프로젝트 구현 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d9dfe567db0b8788b93b13aeb760d45f4c05b57
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707981"
---
# <a name="how-to-implement-nested-projects"></a>방법: 중첩 된 프로젝트 구현

중첩된 프로젝트 유형을 만들 때 구현해야 하는 몇 가지 추가 단계가 있습니다. 상위 프로젝트는 중첩된(자식) 프로젝트에 대해 솔루션이 가지고 있는 것과 동일한 책임을 수행합니다. 상위 프로젝트는 솔루션과 유사한 프로젝트의 컨테이너입니다. 특히 중첩 된 프로젝트의 계층 구조를 빌드하기 위해 솔루션 및 상위 프로젝트에서 제기해야 하는 몇 가지 이벤트가 있습니다. 이러한 이벤트는 중첩된 프로젝트를 만들기 위한 다음 프로세스에 설명되어 있습니다.

## <a name="create-nested-projects"></a>중첩된 프로젝트 만들기

1. 통합 개발 환경(IDE)은 인터페이스를 호출하여 상위 프로젝트의 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 파일 및 시작 정보를 로드합니다. 상위 프로젝트가 만들어지고 솔루션에 추가됩니다.

    > [!NOTE]
    > 이 시점에서 상위 프로젝트를 만들기 전에 상위 프로젝트를 만들어야 하기 때문에 부모 프로젝트가 중첩된 프로젝트를 만드는 프로세스의 너무 이르다. 이 순서에 따라 상위 프로젝트는 자식 프로젝트에 설정을 적용할 수 있으며 하위 프로젝트는 필요한 경우 상위 프로젝트에서 정보를 수집할 수 있습니다. 이 시퀀스는 소스 코드 제어(SCC) 및 솔루션 **탐색기와**같은 클라이언트에서 필요한 경우입니다.

     상위 프로젝트는 중첩된(자식) <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> 프로젝트 또는 프로젝트를 만들려면 메서드가 IDE에서 호출될 때까지 기다려야 합니다.

2. IDE는 `QueryInterface` 에 대한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>상위 프로젝트를 호출합니다. 이 호출이 성공하면 IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> 부모의 메서드를 호출하여 상위 프로젝트에 대해 중첩된 모든 프로젝트를 엽니다.

3. 상위 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> 중첩된 프로젝트가 생성될 예정임을 청취자에게 알리는 메서드를 호출합니다. 예를 들어 SCC는 솔루션 및 프로젝트 생성 프로세스의 단계가 순서대로 발생하는지 확인하기 위해 이러한 이벤트를 듣고 있습니다. 단계가 순서에 관계없이 발생하면 솔루션이 소스 코드 제어에 올바르게 등록되지 않을 수 있습니다.

4. 상위 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> 각 자식 프로젝트에 대한 메서드 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> 메서드를 호출합니다.

     메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> `AddVirtualProject` 전달하여 가상(중첩) 프로젝트를 프로젝트 창에 추가하고 빌드에서 제외하고 소스 코드 컨트롤에 추가해야 함을 나타냅니다. `VSADDVPFLAGS`을 사용하면 중첩된 프로젝트의 가시성을 제어하고 연결된 기능을 나타낼 수 있습니다.

     상위 프로젝트의 프로젝트 파일에 저장된 프로젝트 GUID가 있는 기존 자식 프로젝트를 다시 로드하는 `AddVirtualProjectEx`경우 부모 프로젝트가 호출합니다. 유일한 `AddVirtualProject` 차이점은 `AddVirtualProjectEX` `AddVirtualProjectEX` 부모 프로젝트가 자식 프로젝트를 활성화하고 `guidProjectID` <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> 올바르게 작동하도록 인스턴스당 을 지정할 수 있도록 하는 매개 변수가 있다는 것입니다.

     새 중첩 된 프로젝트를 추가할 때와 같이 사용 가능한 GUID가 없는 경우 솔루션은 상위 프로젝트에 추가할 때 프로젝트에 대해 하나를 만듭니다. 프로젝트 GUID를 프로젝트 파일에 유지하는 것은 부모 프로젝트의 책임입니다. 중첩된 프로젝트를 삭제하면 해당 프로젝트의 GUID도 삭제할 수 있습니다.

5. IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> 상위 프로젝트의 각 자식 프로젝트에서 메서드를 호출합니다.

     프로젝트를 중첩하려면 `IVsParentProject` 상위 프로젝트를 구현해야 합니다. 그러나 상위 프로젝트는 `QueryInterface` 그 `IVsParentProject` 아래에 상위 프로젝트가 있더라도 절대로 요구하지 않습니다. 솔루션은 호출을 `IVsParentProject` 처리하고 구현된 경우 중첩된 프로젝트를 만들기 위한 호출을 `OpenChildren` 처리합니다. `AddVirtualProjectEX`항상 에서 `OpenChildren`호출됩니다. 계층 만들기 이벤트를 순서대로 유지하려면 부모 프로젝트에서 호출해서는 안 됩니다.

6. IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> 자식 프로젝트에서 메서드를 호출합니다.

7. 상위 프로젝트는 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> 호출하여 상위에 대한 자식 프로젝트가 생성되었음을 청취자에게 알립니다.

8. 모든 자식 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> 프로젝트가 열린 후 IDE는 상위 프로젝트에서 메서드를 호출합니다.

     아직 존재하지 않는 경우 부모 프로젝트는 `CoCreateGuid`호출하여 중첩된 각 프로젝트에 대한 GUID를 만듭니다.

    > [!NOTE]
    > `CoCreateGuid`는 GUID를 만들 때 호출되는 COM API입니다. 자세한 내용은 MSDN 라이브러리의 GUID를 참조하십시오. `CoCreateGuid`

     상위 프로젝트는 이 GUID를 프로젝트 파일에 저장하여 다음에 IDE에서 열릴 때 검색할 수 있습니다. 자식 프로젝트에 `AddVirtualProjectEX` `guidProjectID` 대한 검색 요청과 관련된 자세한 내용은 4단계를 참조하십시오.

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 그런 다음 중첩된 프로젝트에 대해 규칙별로 위임하는 상위 ItemID에 메서드가 호출됩니다. 는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 부모에 호출 될 때 위임 할 프로젝트를 중첩 노드의 속성을 검색합니다.

     부모 및 자식 프로젝트는 프로그래밍 방식으로 인스턴스화되므로 이 시점에서 중첩된 프로젝트에 대한 속성을 설정할 수 있습니다.

    > [!NOTE]
    > 중첩된 프로젝트에서 컨텍스트 정보를 받을 뿐만 아니라 상위 프로젝트에 __VSHPROPID 확인하여 해당 항목에 대한 컨텍스트가 있는지 물어볼 수도 [있습니다. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). 이러한 방식으로 개별 중첩 된 프로젝트에 특정 추가 동적 도움말 특성 및 메뉴 옵션을 추가할 수 있습니다.

10. 계층 구조는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> 메서드에 대 한 호출을 사용 하 고 솔루션 **탐색기에서** 표시 하기 위해 빌드됩니다.

     계층을 환경으로 `GetNestedHierarchy` 전달하여 솔루션 탐색기에서 표시할 계층을 빌드합니다. 이러한 방식으로 솔루션은 프로젝트가 존재하고 빌드 관리자가 빌드하기 위해 관리할 수 있음을 알고 있거나 프로젝트의 파일을 소스 코드 제어 하에 배치하도록 허용할 수 있습니다.

11. Project1에 대한 중첩된 모든 프로젝트가 만들어지면 컨트롤이 솔루션으로 다시 전달되고 Project2에 대한 프로세스가 반복됩니다.

     중첩 된 프로젝트를 만드는 이 동일한 프로세스는 자식이 있는 자식 프로젝트에 대해 발생합니다. 이 경우 Project1의 자식인 BuildProject1에 자식 프로젝트가 있는 경우 BuildProject1 이후 및 Project2 전에 만들어집니다. 프로세스는 재귀적이며 계층 구조는 위에서 아래로 빌드됩니다.

     사용자가 솔루션 또는 특정 프로젝트 자체를 닫았기 때문에 중첩된 프로젝트가 `IVsParentProject`닫히면 에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>대한 다른 메서드가 호출됩니다. 부모 프로젝트는 메서드에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> 대한 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> 랩핑하고 중첩된 프로젝트가 닫혀 있음을 솔루션 이벤트에 수신기에 알리는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> 메서드를 제공합니다.

다음 항목에서는 중첩된 프로젝트를 구현할 때 고려해야 할 몇 가지 다른 개념을 다룹니다.

- [중첩된 프로젝트 언로드 및 다시 로드에 대한 고려 사항](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [중첩 된 프로젝트에 대 한 마법사 지원](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [중첩된 프로젝트에 대한 명령 처리 구현](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [중첩된 프로젝트에 대한 AddItem 대화 상자 필터링](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>참조

- [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [프로젝트 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)
- [검사 목록: 새 프로젝트 유형 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)
- [마법사(.vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)
