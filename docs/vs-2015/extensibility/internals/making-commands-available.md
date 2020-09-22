---
title: 명령을 사용할 수 있도록 설정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cab4244fbf9173895159a4b104260006fc93f0c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841370"
---
# <a name="making-commands-available"></a>명령을 사용 가능하게 지정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

여러 Vspackage을 Visual Studio에 추가 하면 UI (사용자 인터페이스)가 명령과 함께 과도 하 게 복잡 해질 수 있습니다. 다음과 같이이 문제를 줄이기 위해 패키지를 프로그래밍할 수 있습니다.  
  
- 사용자가 필요한 경우에만 로드 되도록 패키지를 프로그래밍 합니다.  
  
- 패키지를 프로그래밍 하 여 IDE (통합 개발 환경)의 현재 상태 컨텍스트에서 필요할 수 있는 경우에만 해당 명령이 표시 되도록 합니다.  
  
## <a name="delayed-loading"></a>지연 로드  
 지연 된 로드를 사용 하도록 설정 하는 일반적인 방법은 해당 명령이 UI에 표시 되도록 VSPackage을 디자인 하는 것 이지만 사용자가 명령 중 하나를 클릭할 때까지 패키지 자체가 로드 되지 않습니다. 이를 위해. vsct 파일에서 명령 플래그가 없는 명령을 만듭니다.  
  
 다음 예제에서는. vsct 파일의 메뉴 명령 정의를 보여 줍니다. 템플릿의 **메뉴 명령** 옵션을 선택 하면 Visual Studio 패키지 템플릿에서 생성 되는 명령입니다.  
  
```xml  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 예를 들어, 부모 그룹인가 `MyMenuGroup` **도구** 메뉴와 같은 최상위 메뉴의 자식인 경우 해당 메뉴에 명령이 표시 되지만 사용자가 명령을 클릭 하 여 명령을 실행 하는 패키지는 로드 되지 않습니다. 그러나 명령을 프로그래밍 하 여 인터페이스를 구현 함으로써 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 명령이 포함 된 메뉴가 처음 확장 될 때 패키지를 로드 하도록 설정할 수 있습니다.  
  
 지연 된 로드로 인해 시작 성능도 향상 될 수도 있습니다.  
  
## <a name="current-context-and-the-visibility-of-commands"></a>현재 컨텍스트 및 명령의 표시 유형  
 VSPackage 데이터의 현재 상태 또는 현재 관련 된 작업에 따라 표시 하거나 숨길 VSPackage 명령을 프로그래밍할 수 있습니다. 일반적으로 인터페이스에서 메서드의 구현을 사용 하 여 VSPackage가 명령의 상태를 설정 하도록 설정할 수 <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 있지만이를 위해서는 코드를 실행 하기 전에 VSPackage를 로드 해야 합니다. 대신 IDE에서 패키지를 로드 하지 않고 명령의 표시 여부를 관리 하도록 설정 하는 것이 좋습니다. 이렇게 하려면. vsct 파일에서 하나 이상의 특수 한 UI 컨텍스트와 명령을 연결 합니다. 이러한 UI 컨텍스트는 *명령 컨텍스트 guid*로 알려진 guid로 식별 됩니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트를 로드 하거나 편집에서 빌드하기로 이동 하는 등의 사용자 작업으로 인해 발생 하는 변경 내용을 모니터링 합니다. 변경이 발생 하면 IDE의 모양이 자동으로 수정 됩니다. 다음 표에서는을 모니터링 하는 IDE 변경의 네 가지 주요 컨텍스트를 보여 줍니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
|컨텍스트 형식|Description|  
|---------------------|-----------------|  
|활성 프로젝트 형식|대부분의 프로젝트 형식에서이 `GUID` 값은 프로젝트를 구현 하는 VSPackage의 GUID와 동일 합니다. 그러나 프로젝트에서 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 프로젝트 형식을 `GUID` 값으로 사용 합니다.|  
|활성 창|일반적으로 키 바인딩에 대 한 현재 UI 컨텍스트를 설정 하는 마지막 활성 문서 창입니다. 그러나 내부 웹 브라우저와 유사한 키 바인딩 테이블이 있는 도구 창이 될 수도 있습니다. HTML 편집기와 같은 다중 탭 문서 창의 경우 모든 탭에 다른 명령 컨텍스트가 `GUID` 있습니다.|  
|활성 언어 서비스|현재 텍스트 편집기에 표시 되는 파일과 연결 된 언어 서비스입니다.|  
|활성 도구 창|열려 있고 포커스가 있는 도구 창입니다.|  
  
 다섯 번째 주요 컨텍스트 영역은 IDE의 UI 상태입니다. UI 컨텍스트는 다음과 같이 활성 명령 컨텍스트로 식별 됩니다 `GUID` .  
  
- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>
  
  이러한 Guid는 IDE의 현재 상태에 따라 활성 또는 비활성으로 표시 됩니다. 여러 UI 컨텍스트는 동시에 활성화 될 수 있습니다.  
  
### <a name="hiding-and-displaying-commands-based-on-context"></a>컨텍스트에 따라 명령 숨기기 및 표시  
 패키지 자체를 로드 하지 않고 IDE에서 패키지 명령을 표시 하거나 숨길 수 있습니다. 이렇게 하려면 `DefaultDisabled` , `DefaultInvisible` 및 명령 플래그를 사용 하 `DynamicVisibility` 고 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) 섹션에 하나 이상의 [VisibilityItem](../../extensibility/visibilityitem-element.md) 요소를 추가 하 여 패키지의. vsct 파일에서 명령을 정의 합니다. 지정 된 명령 컨텍스트가 활성화 되 면 `GUID` 패키지를 로드 하지 않고 명령이 표시 됩니다.  
  
### <a name="custom-context-guids"></a>사용자 지정 컨텍스트 Guid  
 적절 한 명령 컨텍스트 GUID를 아직 정의 하지 않은 경우 VSPackage에서 정의 하 고 명령 표시 여부를 제어 하는 필요에 따라 활성 또는 비활성으로 프로그래밍할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>서비스를 사용 하 여 다음을 수행 합니다.  
  
- 메서드를 호출 하 여 컨텍스트 Guid를 등록 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> 합니다.  
  
- `GUID`메서드를 호출 하 여 컨텍스트의 상태를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> .  
  
- `GUID`메서드를 호출 하 여 컨텍스트를 설정 및 해제 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 합니다.  
  
    > [!CAUTION]
    > 다른 Vspackage가이에 종속 될 수 있으므로 VSPackage가 기존 컨텍스트 GUID의 상태에 영향을 주지 않는지 확인 합니다.  
  
## <a name="example"></a>예제  
 다음 VSPackage 명령 예에서는 VSPackage를 로드 하지 않고 명령 컨텍스트에서 관리 하는 명령의 동적 표시 유형을 보여 줍니다.  
  
 이 명령은 솔루션이 있을 때마다 사용 하도록 설정 되 고 표시 되도록 설정 됩니다. 즉, 다음 명령 컨텍스트 Guid 중 하나가 활성화 될 때마다입니다.  
  
- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>  
  
- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>  
  
- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>  
  
  예제에서 모든 명령 플래그는 별도의 [명령 플래그](../../extensibility/command-flag-element.md) 요소입니다.  
  
```  
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"   
        priority="0x0100" type="Button">  
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <CommandFlag>DefaultDisabled</CommandFlag>  
  <CommandFlag>DefaultInvisible</CommandFlag>  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <CommandName>cmdidMyCommand</CommandName>  
    <ButtonText>My Command name</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 또한 다음과 같이 별도의 요소에 모든 UI 컨텍스트를 지정 해야 합니다 `VisibilityItem` .  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
  
```  
  
## <a name="see-also"></a>참고 항목  
 [MenuCommands와 OleMenuCommands 비교](../../misc/menucommands-vs-olemenucommands.md)   
 [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage의 명령 라우팅](../../extensibility/internals/command-routing-in-vspackages.md)   
 [메뉴 항목 동적 추가](../../extensibility/dynamically-adding-menu-items.md)
