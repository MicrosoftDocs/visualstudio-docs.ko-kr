---
title: 메뉴 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dc4731f95e31781f6b10704d7cb14dc83e96d7a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702593"
---
# <a name="menu-element"></a>메뉴 요소
하나의 메뉴 항목을 정의합니다. 다음은 6가지 메뉴 종류: 컨텍스트, 메뉴, 메뉴 컨트롤러, MenuControllerLatched, 도구 모음 및 ToolWindowToolbar입니다.

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
|guid|필수 사항입니다. GUID/ID 명령 식별자의 GUID입니다.|
|id|필수 사항입니다. GUID/ID 명령 식별자의 ID입니다.|
|priority|(선택 사항) 메뉴 그룹의 메뉴 상대위치를 지정하는 숫자 값입니다.|
|도구 모음우선 순위인밴드|(선택 사항) 창이 도킹될 때 밴드에서 도구 모음의 상대적 위치를 지정하는 숫자 값입니다.|
|type|(선택 사항) 요소의 종류를 지정하는 예인된 값입니다.<br /><br /> 없는 경우 기본 유형은 메뉴입니다.<br /><br /> Context<br /> 사용자가 창을 마우스 오른쪽 단추로 클릭할 때 표시되는 바로 가기 메뉴입니다. 바로 가기 메뉴에는 다음과 같은 특성이 있습니다.<br /><br /> - 메뉴가 바로 가기 메뉴로 표시될 때 **부모** 및 **우선 순위** 필드를 사용하지 않습니다.<br />- 하위 메뉴및 바로 가기 메뉴로 사용할 수 있습니다. 이 경우 **그룹 ID** 및 **우선 순위** 필드가 모두 적용됩니다.<br />- 항상 사용할 수 있는 것은 아닙니다.<br /><br /> 바로 가기 메뉴는 다음 조건이 true인 경우에만 표시됩니다.<br /><br /> - 호스트하는 창이 표시됩니다.<br />- VSPackage의 마우스 처리기는 창을 마우스 오른쪽 단추로 클릭한 다음 명령을 처리하는 메서드를 호출합니다.<br />- 바로 가기 메뉴는 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> 방법 (권장 접근 방식) <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> 또는 방법을 호출하여 표시됩니다.<br /><br /> 메뉴<br /> 드롭다운 메뉴를 제공합니다. 드롭다운 메뉴에는 다음과 같은 특성이 있습니다.<br /><br /> - 정의에 부모를 존중합니다.<br />- 상위 그룹 또는 그룹에 대한 명령 배치가 있어야 합니다.<br />- 메뉴의 다른 종류의 하위 메뉴가 될 수 있습니다.<br />- 부모 메뉴가 표시될 때마다 자동으로 표시됩니다.<br />- VSPackage 코드를 구현하여 표시할 필요가 없습니다.<br /><br /> 메뉴 컨트롤러<br /> 일반적으로 도구 모음에 사용되는 분할 단추 드롭다운 메뉴를 제공합니다. MenuController 메뉴에는 다음과 같은 특성이 있습니다.<br /><br /> - 부모 또는 명령 배치를 통해 다른 메뉴에 포함되어야합니다.<br />- 정의에 부모를 존중합니다.<br />- 부모로 메뉴의 종류를 가질 수 있습니다.<br />- 부모 메뉴가 표시될 때마다 자동으로 사용할 수 있습니다.<br />- 메뉴를 표시하기 위해 프로그래밍 지원이 필요하지 않습니다.<br /><br /> 분할 단추 메뉴의 명령이 메뉴 단추에 표시됩니다. 표시된 명령에는 다음 특성 중 하나가 있습니다.<br /><br /> - 명령이 여전히 표시되고 활성화되어 있는 경우 사용된 마지막 명령입니다.<br />- 그것은 첫 번째 표시되는 명령입니다.<br /><br /> 메뉴컨트롤러라치<br /> 명령을 래치로 표시하여 명령을 기본 선택 으로 지정할 수 있는 분할 단추 드롭다운 메뉴를 제공합니다.<br /><br /> 래치된 명령은 일반적으로 확인 표시를 표시하여 메뉴에 선택된 것으로 표시된 명령입니다. 명령은 인터페이스 메서드의 구현에서 OLECMDF_LATCHED 플래그가 설정되어 있는 경우 래치로 `QueryStatus` 표시할 수 있습니다. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> MenuControllerLatched 메뉴에는 다음과 같은 특성이 있습니다.<br /><br /> - 부모 그룹 또는 명령 배치를 통해 다른 메뉴에 포함되어야 합니다.<br />- 정의에 부모를 존중합니다.<br />- 부모로 메뉴의 종류를 가질 수 있습니다.<br />- 부모 메뉴가 표시될 때마다 사용할 수 있습니다.<br />- 메뉴를 표시하기 위해 프로그래밍 지원이 필요하지 않습니다.<br /><br /> 분할 단추 메뉴의 명령이 메뉴 단추에 표시됩니다. 표시된 명령에는 다음 특성 중 하나가 있습니다.<br /><br /> - 래치되는 첫 번째 표시된 명령입니다.<br />- 그것은 첫 번째 표시되는 명령입니다.<br /><br /> 도구 모음<br /> 도구 모음을 제공합니다. 도구 모음에는 다음과 같은 특성이 있습니다.<br /><br /> - 정의에서 부모를 무시합니다.<br />- 명령 배치를 사용하여도 어떤 그룹의 하위 메뉴를 만들 수 없습니다.<br />- **항상 보기** 메뉴에서 **도구 모음을** 클릭하여 표시 할 수 있습니다.<br />- 가시성항목을 사용하여 표시할 수 [있습니다.](../extensibility/visibilityitem-element.md)<br />- 코드를 만들 필요가 없습니다. 도구 모음을 만드는 방법에 대한 예제는 [도구 모음 추가](../extensibility/adding-a-toolbar.md)를 참조하십시오.<br /><br /> 도구 창 도구 모음<br /> 도구 모음이 개발 환경에 연결된 것처럼 특정 도구 창에 연결된 도구 모음을 제공합니다.<br /><br /> - 정의에서 부모를 무시합니다.<br />- 명령 배치를 사용하여도 어떤 그룹의 하위 메뉴를 만들 수 없습니다.<br />- 도구 모음을 호스트하는 도구 창이 표시되고 VSPackage가 도구 모음을 도구 창에 명시적으로 추가하는 경우에만 표시됩니다. 이 작업은 일반적으로 도구 창 프레임에서 도구 모음 호스트 속성을 얻은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> 다음 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> 메서드를 호출하여 도구 모음 호스트 속성을 생성할 때 수행됩니다.|
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|Parent|(선택 사항) 메뉴 항목의 상위 요소입니다.|
|커맨드 플래그|필수 사항입니다. [명령 플래그 요소를](../extensibility/command-flag-element.md)참조하십시오. 메뉴에 유효한 CommandFlag 값은 다음과 같습니다.<br /><br /> -   **항상 만들기**<br />-   **기본도킹**<br />-   **기본보이지 않음** - 이 플래그는 도구 모음 표시에 영향을 주지 않습니다.<br />-   **돈트캐시**<br />-   **Dynamic가시성** - 이 플래그는 도구 모음표시에 영향을 주지 않습니다.<br />-   **아이콘및텍스트**<br />-   **사용자 지정 안 됩니다.**<br />-   **노인TB리스트**<br />-   **노툴바닫기**<br />-   **텍스트 변경**<br />-   **텍스트Is앵커명령**|
|문자열|필수 사항입니다. [문자열 요소를](../extensibility/strings-element.md)참조하십시오. 자식 `ButtonText` 요소를 정의해야 합니다.|
|주석|선택적 주석.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[메뉴 요소](../extensibility/menus-element.md)|VSPackage가 구현하는 모든 메뉴를 정의합니다.|

## <a name="example"></a>예제

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <CommandFlag>AlwaysCreate</CommandFlag>
    <Strings>
      <ButtonText>Edit Widget</ButtonText>
    </Strings>
    </Parent>
</Menu>
```

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블(.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
