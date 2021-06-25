---
title: Menu 요소 | Microsoft Docs
description: Menu 요소는 하나의 메뉴 항목을 정의합니다. 메뉴 종류는 Context, Menu, MenuController, MenuControllerLatched, Toolbar 및 ToolWindowToolbar입니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2ffa029dd05e7fe3d32a9df4a1d06c90c8b9c6b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901541"
---
# <a name="menu-element"></a>Menu 요소
하나의 메뉴 항목을 정의합니다. 다음은 6가지 종류의 메뉴인 Context, Menu, MenuController, MenuControllerLatched, Toolbar 및 ToolWindowToolbar입니다.

## <a name="syntax"></a>구문

```xml
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">
  <Parent>... </Parent>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Menu>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|guid|필수 요소. GUID/ID 명령 식별자의 GUID입니다.|
|id|필수 요소. GUID/ID 명령 식별자의 ID입니다.|
|priority|선택 사항입니다. 메뉴 그룹에서 메뉴의 상대 위치를 지정하는 숫자 값입니다.|
|ToolbarPriorityInBand|선택 사항입니다. 창이 도킹될 때 밴드에서 도구 모음의 상대 위치를 지정하는 숫자 값입니다.|
|형식(type)|선택 사항입니다. 요소의 종류를 지정하는 열거형 값입니다.<br /><br /> 없는 경우 기본 유형은 Menu입니다.<br /><br /> 컨텍스트<br /> 사용자가 창을 마우스 오른쪽 단추로 클릭할 때 표시되는 바로 가기 메뉴입니다. 바로 가기 메뉴에는 다음과 같은 특징이 있습니다.<br /><br /> - 메뉴가 바로 가기 메뉴로 표시될 때 **부모** 및 **우선 순위** 필드를 사용하지 않습니다.<br />- 하위 메뉴로 사용할 수 있으며 바로 가기 메뉴로도 사용할 수 있습니다. 이 경우 **그룹 ID** 및 **우선 순위** 필드가 모두 준수됩니다.<br />- 항상 사용할 수 있는 것은 아닙니다.<br /><br /> 바로 가기 메뉴는 다음 조건이 충족되는 경우에만 표시됩니다.<br /><br /> - 호스트하는 창이 표시됩니다.<br />- VSPackage의 마우스 처리기가 창에서 마우스 오른쪽 단추를 클릭한 다음 명령을 처리하는 메서드를 호출합니다.<br />- 바로 가기 메뉴는 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> 메서드(권장 방법) 또는 메서드를 호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> 표시됩니다.<br /><br /> 메뉴<br /> 드롭다운 메뉴를 제공합니다. 드롭다운 메뉴에는 다음과 같은 특징이 있습니다.<br /><br /> - 해당 정의에서 부모를 준수합니다.<br />- 부모 그룹 또는 그룹에 대한 CommandPlacement가 있어야 합니다.<br />- 다른 종류의 메뉴에서 하위 메뉴가 될 수 있습니다.<br />- 부모 메뉴가 표시될 때마다 자동으로 표시됩니다.<br />- VSPackage 코드를 표시하기 위해 구현할 필요가 없습니다.<br /><br /> MenuController<br /> 일반적으로 도구 모음에서 사용되는 분할 단추 드롭다운 메뉴를 제공합니다. MenuController 메뉴에는 다음과 같은 특징이 있습니다.<br /><br /> - Parent 또는 CommandPlacement를 통해 다른 메뉴에 포함되어야 합니다.<br />- 해당 정의에서 부모를 준수합니다.<br />- 모든 종류의 메뉴를 부모로 사용할 수 있습니다.<br />- 부모 메뉴가 표시될 때마다 자동으로 사용할 수 있습니다.<br />- 메뉴를 표시하기 위해 프로그래밍 방식 지원이 필요하지 않습니다.<br /><br /> 분할 단추 메뉴의 명령이 메뉴 단추에 표시됩니다. 표시되는 명령에는 다음 특성 중 하나가 있습니다.<br /><br /> - 명령이 계속 표시되고 사용하도록 설정된 경우 사용된 마지막 명령입니다.<br />- 표시되는 첫 번째 명령입니다.<br /><br /> MenuControllerLatched<br /> 명령을 래치된 것으로 표시하여 명령을 기본 선택 영역으로 지정할 수 있는 분할 단추 드롭다운 메뉴를 제공합니다.<br /><br /> 래치된 명령은 일반적으로 확인 표시를 표시하여 메뉴에 선택된 것으로 표시되는 명령입니다. 인터페이스의 메서드 구현에서 OLECMDF_LATCHED 플래그가 설정된 경우 명령을 래치된 것으로 표시할 수 `QueryStatus` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 있습니다. MenuControllerLatched 메뉴에는 다음과 같은 특징이 있습니다.<br /><br /> - 부모 그룹 또는 CommandPlacement를 통해 다른 메뉴에 포함되어야 합니다.<br />- 해당 정의에서 부모를 준수합니다.<br />- 모든 종류의 메뉴를 부모로 사용할 수 있습니다.<br />- 부모 메뉴가 표시될 때마다 사용할 수 있습니다.<br />- 메뉴를 표시하기 위해 프로그래밍 방식 지원이 필요하지 않습니다.<br /><br /> 분할 단추 메뉴의 명령이 메뉴 단추에 표시됩니다. 표시되는 명령에는 다음 특성 중 하나가 있습니다.<br /><br /> - 래치되는 첫 번째 표시된 명령입니다.<br />- 표시되는 첫 번째 명령입니다.<br /><br /> 도구 모음<br /> 도구 모음을 제공합니다. 도구 모음에는 다음과 같은 특징이 있습니다.<br /><br /> - 해당 정의에서 부모를 무시합니다.<br />- CommandPlacement를 사용하더라도 그룹의 하위 메뉴가 될 수 없습니다.<br />- **보기** 메뉴에서 **도구 모음을** 클릭하여 항상 표시할 수 있습니다.<br />- [VisibilityItem](../extensibility/visibilityitem-element.md)을 사용하여 표시할 수 있습니다.<br />- 코드를 만들 필요가 없습니다. 도구 모음을 만드는 방법에 대한 예제는 도구 [모음 추가를 참조하세요.](../extensibility/adding-a-toolbar.md)<br /><br /> ToolWindowToolbar<br /> 도구 모음이 개발 환경에 연결된 것처럼 특정 도구 창에 연결된 도구 모음을 제공합니다.<br /><br /> - 해당 정의에서 부모를 무시합니다.<br />- CommandPlacement를 사용하더라도 그룹의 하위 메뉴가 될 수 없습니다.<br />- 도구 모음을 호스트하는 도구 창이 표시되고 VSPackage에서 도구 모음을 도구 창에 명시적으로 추가하는 경우에만 표시됩니다. 이 작업은 일반적으로 도구 창 프레임에서 도구 모음 호스트 속성(인터페이스로 표시)을 가져온 다음 메서드를 호출하여 도구 창을 만들 때 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> 수행됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A>|
|조건|선택 사항입니다. [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|Parent|선택 사항입니다. 메뉴 항목의 부모 요소입니다.|
|CommandFlag|필수 요소. [Command 플래그 요소](../extensibility/command-flag-element.md)를 참조하세요. 메뉴의 유효한 CommandFlag 값은 다음과 같습니다.<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked 됨**<br />-   **Defaultinvisible** 않음-이 플래그는 도구 모음의 표시에 영향을 주지 않습니다.<br />-   **DontCache**<br />-   **Dynamicvisibility** -이 플래그는 도구 모음의 표시에 영향을 주지 않습니다.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **Noa를 닫습니다.**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|
|문자열|필수 요소. [Strings 요소](../extensibility/strings-element.md)를 참조 하세요. 자식 `ButtonText` 요소를 정의 해야 합니다.|
|Annotation|선택적 설명입니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Menus 요소](../extensibility/menus-element.md)|VSPackage가 구현 하는 모든 메뉴를 정의 합니다.|

## <a name="example"></a>예제

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"/>
  <CommandFlag>AlwaysCreate</CommandFlag>
  <Strings>
    <ButtonText>Edit Widget</ButtonText>
  </Strings>
</Menu>
```

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
