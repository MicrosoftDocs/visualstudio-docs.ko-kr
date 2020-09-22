---
title: '방법: 중첩 프로젝트 구현 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 427ef425c64323246ffe1141d081fd7d921506a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841955"
---
# <a name="how-to-implement-nested-projects"></a>방법: 중첩된 프로젝트 구현
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

중첩 된 프로젝트 형식을 만들 때 몇 가지 추가 단계를 구현 해야 합니다. 부모 프로젝트는 솔루션에서 중첩 된 (자식) 프로젝트에 대해 수행 하는 것과 동일한 책임을가지고 있습니다. 부모 프로젝트는 솔루션과 비슷한 프로젝트의 컨테이너입니다. 특히 솔루션에서 발생 하는 여러 이벤트와 부모 프로젝트가 중첩 된 프로젝트의 계층 구조를 빌드하기 위해 발생 해야 합니다. 이러한 이벤트는 중첩 된 프로젝트를 만들기 위해 다음 프로세스에 설명 되어 있습니다.  
  
### <a name="to-create-nested-projects"></a>중첩 된 프로젝트를 만들려면  
  
1. IDE (통합 개발 환경)는 인터페이스를 호출 하 여 부모 프로젝트의 프로젝트 파일 및 시작 정보를 로드 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> . 부모 프로젝트가 만들어지고 솔루션에 추가 됩니다.  
  
   > [!NOTE]
   > 이 시점에서 부모 프로젝트가 생성 되어야 자식 프로젝트를 만들 수 있기 때문에 부모 프로젝트가 중첩 된 프로젝트를 만들 수 없습니다. 이 순서에 따라 부모 프로젝트가 자식 프로젝트에 설정을 적용할 수 있으며, 필요한 경우 자식 프로젝트가 부모 프로젝트에서 정보를 가져올 수 있습니다. 이 시퀀스는 SCC (소스 코드 제어) 및 솔루션 탐색기 같은 클라이언트에서 필요 합니다.  
  
    부모 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> 해당 중첩 된 (자식) 프로젝트 또는 프로젝트를 만들기 전에 IDE에서 메서드를 호출할 때까지 기다려야 합니다.  
  
2. IDE는 `QueryInterface` 의 부모 프로젝트에서를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> . 이 호출이 성공 하면 IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> 부모의 메서드를 호출 하 여 부모 프로젝트에 대 한 모든 중첩 프로젝트를 엽니다.  
  
3. 부모 프로젝트는 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> 하 여 중첩 된 프로젝트가 만들어지도록 수신기에 알립니다. 예를 들어, SCC는 이러한 이벤트를 수신 대기 하 여 솔루션 및 프로젝트 생성 프로세스의 단계가 순서 대로 발생 하는지 확인 합니다. 단계가 순서를 벗어난 경우 솔루션이 소스 코드 제어에 올바르게 등록 되지 않았을 수 있습니다.  
  
4. 부모 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> 각 자식 프로젝트에서 메서드 또는 메서드를 호출 합니다.  
  
    <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> `AddVirtualProject` 가상 (중첩 된) 프로젝트를 프로젝트 창에 추가 하 고, 빌드에서 제외 하 고, 소스 코드 제어에 추가 하는 등의 방법을 나타내려면 메서드에를 전달 합니다. `VSADDVPFLAGS` 중첩 된 프로젝트의 표시 여부를 제어 하 고이에 연결 된 기능을 표시할 수 있습니다.  
  
    부모 프로젝트의 프로젝트 파일에 저장 된 프로젝트 GUID가 있는 기존 자식 프로젝트를 다시 로드 하는 경우에는 부모 프로젝트가를 호출 `AddVirtualProjectEx` 합니다. 과의 유일한 차이점 `AddVirtualProject` 은 `AddVirtualProjectEX` `AddVirtualProjectEX` 부모 프로젝트가 자식 프로젝트에 대해 인스턴스당를 지정 하 여를 사용 하도록 설정 하 `guidProjectID` <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> 제대로 작동할 수 있도록 하는 매개 변수를 포함 한다는 것입니다.  
  
    새 중첩 프로젝트를 추가 하는 경우와 같이 사용할 수 있는 GUID가 없는 경우 솔루션이 부모에 추가 될 때 프로젝트에 대 한 GUID를 만듭니다. 프로젝트 파일에서 해당 프로젝트 GUID를 유지 하는 것은 부모 프로젝트의 책임입니다. 중첩 된 프로젝트를 삭제 하는 경우 해당 프로젝트에 대 한 GUID도 삭제할 수 있습니다.  
  
5. IDE는 `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` 부모 프로젝트의 각 자식 프로젝트에 대해 메서드를 호출 합니다.  
  
    프로젝트를 중첩 하려는 경우 부모 프로젝트가를 구현 해야 합니다 `IVsParentProject` . 그러나 부모 프로젝트가 그 `QueryInterface` `IVsParentProject` 아래에 부모 프로젝트가 있는 경우에도에 대해를 호출 하지 않습니다. 솔루션은에 대 한 호출을 처리 하 `IVsParentProject` 고, 구현 된 경우를 호출 `OpenChildren` 하 여 중첩 된 프로젝트를 만듭니다. `AddVirtualProjectEX` 는 항상에서 호출 됩니다 `OpenChildren` . 부모 프로젝트에서 계층 생성 이벤트를 순서 대로 유지 하기 위해이 메서드를 호출 하면 안 됩니다.  
  
6. IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> 자식 프로젝트에서 메서드를 호출 합니다.  
  
7. 부모 프로젝트는 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> 하 여 부모에 대 한 자식 프로젝트가 생성 되었음을 수신기에 알립니다.  
  
8. IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> 모든 자식 프로젝트가 열린 후 부모 프로젝트에서 메서드를 호출 합니다.  
  
    부모 프로젝트가 없는 경우를 호출 하 여 각 중첩 된 프로젝트에 대 한 GUID를 만듭니다 `CoCreateGuid` .  
  
   > [!NOTE]
   > `CoCreateGuid` 는 GUID를 만들 때 호출 되는 COM API입니다. 자세한 내용은 `CoCreateGuid` MSDN Library의 및 guid를 참조 하십시오.  
  
    부모 프로젝트는 다음에 IDE에서 열릴 때 검색할이 GUID를 프로젝트 파일에 저장 합니다. 를 호출 하 여 `AddVirtualProjectEX` `guidProjectID` 자식 프로젝트에 대 한을 검색 하는 것과 관련 된 자세한 내용은 4 단계를 참조 하세요.  
  
9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>그런 다음 중첩 된 프로젝트에 위임 하는 규칙에 따라 부모 ItemID에 대해 메서드가 호출 됩니다. 는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 부모에서 호출 될 때 위임 하려는 프로젝트를 중첩 하는 노드의 속성을 검색 합니다.  
  
     부모 및 자식 프로젝트는 프로그래밍 방식으로 인스턴스화되기 때문에이 시점에서 중첩 프로젝트에 대 한 속성을 설정할 수 있습니다.  
  
    > [!NOTE]
    > 중첩 된 프로젝트에서 컨텍스트 정보를 받을 수 있을 뿐만 아니라, 부모 프로젝트가를 확인 하 여 해당 항목에 대 한 컨텍스트를 포함 하는 경우에도 요청할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> . 이렇게 하면 개별 중첩 프로젝트와 관련 된 추가 동적 도움말 특성 및 메뉴 옵션을 추가할 수 있습니다.  
  
10. 계층은 메서드를 호출 하 여 솔루션 탐색기 표시 하기 위해 빌드됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> .  
  
     계층을를 통해 환경에 전달 하 여 `GetNestedHierarchy` 솔루션 탐색기에 표시할 계층 구조를 작성 합니다. 이러한 방식으로 솔루션은 프로젝트가 존재 하 고 빌드 관리자를 사용 하 여 빌드할 수 있도록 관리 하거나 프로젝트의 파일을 소스 코드 제어에 추가할 수 있습니다.  
  
11. Project1에 대 한 모든 중첩 프로젝트가 생성 되 면 컨트롤이 솔루션에 다시 전달 되 고 Project2에 대해 프로세스가 반복 됩니다.  
  
     중첩 된 프로젝트를 만드는 동일한 프로세스는 자식이 있는 자식 프로젝트에 대해 발생 합니다. 이 경우 Project1의 자식인 BuildProject1에 자식 프로젝트가 있으면 BuildProject1와 Project2 앞에 생성 됩니다. 이 프로세스는 재귀적 이며 계층은 위에서 아래로 작성 됩니다.  
  
     사용자가 솔루션이 나 특정 프로젝트 자체를 닫아야만 중첩 프로젝트가 닫히면,,의 다른 메서드가 `IVsParentProject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> 호출 됩니다. 부모 프로젝트는 및 메서드를 사용 하 여 메서드에 대 한 호출을 래핑하고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> 중첩 프로젝트가 닫히는 솔루션 이벤트에 수신기를 알립니다.  
  
    다음 항목에서는 중첩 된 프로젝트를 구현할 때 고려해 야 할 몇 가지 다른 개념을 다룹니다.  
  
    [중첩된 프로젝트 언로드 및 다시 로드에 대한 고려 사항](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
    [중첩된 프로젝트에 대한 마법사 지원](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
    [중첩된 프로젝트에 대한 명령 처리 구현](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
    [중첩된 프로젝트에 대한 AddItem 필터링 대화 상자](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>참고 항목  
 [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [프로젝트 템플릿 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)   
 [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)   
 [마법사(.Vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)
