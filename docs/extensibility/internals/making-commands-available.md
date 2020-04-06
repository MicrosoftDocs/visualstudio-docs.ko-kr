---
title: 명령을 사용할 수 있도록 하기 | 마이크로 소프트 문서
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d64df85516e0a1ac326f8d40558755718c4644c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707329"
---
# <a name="making-commands-available"></a>명령을 사용할 수 있도록 만들기

여러 VSPackage를 Visual Studio에 추가하면 사용자 인터페이스(UI)가 명령으로 과밀해질 수 있습니다. 다음과 같이 이 문제를 줄이는 데 도움이 되는 패키지를 프로그래밍할 수 있습니다.

- 사용자가 패키지를 필요로 하는 경우에만 로드되도록 패키지를 프로그래밍합니다.

- 통합 개발 환경(IDE)의 현재 상태의 컨텍스트에서 필요할 수 있는 경우에만 해당 명령이 표시되도록 패키지를 프로그래밍합니다.

## <a name="delayed-loading"></a>지연된 로딩

지연된 로드를 활성화하는 일반적인 방법은 VSPackage를 디자인하여 해당 명령이 UI에 표시되지만 사용자가 명령 중 하나를 클릭할 때까지 패키지 자체가 로드되지 않도록 하는 것입니다. 이렇게 하려면 .vsct 파일에서 명령 플래그가 없는 명령을 만듭니다.

다음 예제에서는 .vsct 파일에서 메뉴 명령의 정의 보여 줍니다. 템플릿의 메뉴 명령 옵션을 선택할 때 Visual Studio 패키지 템플릿에서 생성되는 **명령입니다.**

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

이 예에서 부모 그룹이 `MyMenuGroup` **도구** 메뉴와 같은 최상위 메뉴의 하위 그룹인 경우 명령은 해당 메뉴에 표시되지만 명령을 실행하는 패키지는 사용자가 명령을 클릭할 때까지 로드되지 않습니다. 그러나 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 구현하기 위한 명령을 프로그래밍하여 명령을 포함하는 메뉴가 처음 확장될 때 패키지를 로드할 수 있습니다.

지연된 로딩은 시동 성능도 향상될 수 있습니다.

## <a name="current-context-and-the-visibility-of-commands"></a>현재 컨텍스트 및 명령의 가시성

VSPackage 데이터의 현재 상태 또는 현재 관련이 있는 작업에 따라 VSPackage 명령을 표시하거나 숨길 수 있도록 프로그래밍할 수 있습니다. VSPackage를 사용하여 일반적으로 <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스에서 메서드의 구현을 사용하여 해당 명령의 상태를 설정할 수 있지만 코드를 실행하기 전에 VSPackage를 로드해야 합니다. 대신 패키지를 로드하지 않고 IDE를 사용하여 명령의 가시성을 관리하는 것이 좋습니다. 이렇게 하려면 .vsct 파일에서 명령을 하나 이상의 특수 UI 컨텍스트와 연결합니다. 이러한 UI 컨텍스트는 *명령*컨텍스트 GUID로 알려진 GUID로 식별됩니다.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]는 프로젝트 로드 또는 편집에서 빌드로의 작업과 같은 사용자 작업으로 인한 변경 사항을 모니터링합니다. 변경 사항이 발생하면 IDE의 모양이 자동으로 수정됩니다. 다음 표에서는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 모니터링하는 IDE 변경의 네 가지 주요 컨텍스트를 보여 주십니다.

| 컨텍스트 유형 | 설명 |
|-------------------------| - |
| 활성 프로젝트 유형 | 대부분의 프로젝트 유형에서 `GUID` 이 값은 프로젝트를 구현하는 VSPackage의 GUID와 동일합니다. 그러나 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트는 프로젝트 유형을 `GUID` 값으로 사용합니다. |
| 활성 창 | 일반적으로 키 바인딩에 대 한 현재 UI 컨텍스트를 설정 하는 마지막 활성 문서 창입니다. 그러나 내부 웹 브라우저와 유사한 키 바인딩 테이블이 있는 도구 창일 수도 있습니다. HTML 편집기와 같은 다중 탭된 문서 창의 경우 `GUID`모든 탭에는 다른 명령 컨텍스트가 있습니다. |
| 액티브 어학 서비스 | 현재 텍스트 편집기에서 표시되는 파일과 연결된 언어 서비스입니다. |
| 활성 공구 창 | 열려 있고 포커스가 있는 도구 창입니다. |

다섯 번째 주요 컨텍스트 영역은 IDE의 UI 상태입니다. UI 컨텍스트는 다음과 같이 `GUID`활성 명령 컨텍스트 s로 식별됩니다.

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

이러한 GUID는 IDE의 현재 상태에 따라 활성 또는 비활성으로 표시됩니다. 여러 UI 컨텍스트를 동시에 활성화할 수 있습니다.

### <a name="hide-and-display-commands-based-on-context"></a>컨텍스트에 따라 명령 숨기기 및 표시

패키지 자체를 로드하지 않고 IDE에 패키지 명령을 표시하거나 숨길 수 있습니다. `DefaultDisabled`이렇게 하려면 에서 `DefaultInvisible`및 명령 플래그를 사용하고 하나 이상의 `DynamicVisibility` [Visibility항목](../../extensibility/visibilityitem-element.md) 요소를 가시성 제약 섹션에 추가하여 패키지의 .vsct 파일에서 명령을 [정의합니다.](../../extensibility/visibilityconstraints-element.md) 지정된 명령 컨텍스트가 `GUID` 활성화되면 패키지를 로드하지 않고 명령이 표시됩니다.

### <a name="custom-context-guids"></a>사용자 지정 컨텍스트 GUID

적절한 명령 컨텍스트 GUID가 아직 정의되지 않은 경우 VSPackage에서 GUID를 정의한 다음 명령의 가시성을 제어하는 데 필요한 대로 활성 또는 비활성으로 프로그래밍할 수 있습니다. 서비스를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 사용하여 다음을 수행합니다.

- 컨텍스트 GUID를 등록합니다(메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> 호출하여).

- 메서드를 호출하여 `GUID` 컨텍스트의 상태를 가져옵니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>

- 메서드를 `GUID` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 호출하여 컨텍스트 s를 켜고 끕니다.

    > [!CAUTION]
    > 다른 VSPackage가 종속될 수 있으므로 VSPackage가 기존 컨텍스트 GUID의 상태에 영향을 주지 않는지 확인합니다.

## <a name="example"></a>예제

VSPackage 명령의 다음 예제에서는 VSPackage를 로드하지 않고 명령 컨텍스트에서 관리하는 명령의 동적 가시성을 보여 줍니다.

명령이 활성화되고 솔루션이 있을 때마다 표시하도록 설정됩니다. 즉, 다음 명령 컨텍스트 GUID 중 하나가 활성화될 때마다 다음과 같은 명령 컨텍스트GUID가 활성화됩니다.

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

이 예제에서는 모든 명령 플래그가 별도의 [명령 플래그](../../extensibility/command-flag-element.md) 요소입니다.

```xml
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

또한 모든 UI 컨텍스트는 다음과 같이 `VisibilityItem` 별도의 요소에 제공되어야 합니다.

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

## <a name="see-also"></a>참조

- [솔루션 탐색기 도구 모음에 명령 추가](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VSPackage의 명령 라우팅](../../extensibility/internals/command-routing-in-vspackages.md)
- [메뉴 항목 동적 추가](../../extensibility/dynamically-adding-menu-items.md)
