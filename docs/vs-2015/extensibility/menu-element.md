---
title: Menu 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79a8fafc748274015dac7f8f0938bba37ba5a8bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194346"
---
# <a name="menu-element"></a>Menu 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

하나의 메뉴 항목을 정의 합니다. 이러한 종류의 메뉴에는 컨텍스트, 메뉴, 메뉴, 메뉴 메뉴, 메뉴 모음, 도구 모음 및 ToolWindowToolbar가 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|guid|필수 요소. GUID/ID 명령 식별자의 GUID입니다.|  
|id|필수 요소. GUID/ID 명령 식별자의 ID입니다.|  
|priority|선택 사항입니다. 메뉴 그룹에서 메뉴의 상대 위치를 지정 하는 숫자 값입니다.|  
|ToolbarPriorityInBand|선택 사항입니다. 창이 도킹 될 때 밴드에서 도구 모음의 상대 위치를 지정 하는 숫자 값입니다.|  
|형식|선택 사항입니다. 요소의 종류를 지정 하는 열거형 값입니다.<br /><br /> 표시 되지 않는 경우 기본 형식은 메뉴입니다.<br /><br /> Context<br /> 사용자가 창을 마우스 오른쪽 단추로 클릭할 때 표시 되는 바로 가기 메뉴입니다. 바로 가기 메뉴에는 다음과 같은 특징이 있습니다.<br /><br /> -메뉴를 바로 가기 메뉴로 표시 하는 경우 부모 및 우선 순위 필드를 사용 하지 않습니다.<br />-하위 메뉴 및 바로 가기 메뉴와 함께 사용할 수 있습니다. 이 경우 그룹 ID와 우선 순위 필드가 모두 적용 됩니다.<br />-항상 사용할 수 있는 것은 아닙니다.<br /><br /> 바로 가기 메뉴는 다음 조건에 해당 하는 경우에만 표시 됩니다.<br /><br /> -이를 호스트 하는 창이 표시 됩니다.<br />-VSPackage의 마우스 처리기가 창을 마우스 오른쪽 단추로 클릭 한 다음 명령을 처리 하는 메서드를 호출 하는 방법을 검색 합니다.<br />-바로 가기 메뉴는 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> 메서드 (권장 방법) 또는 메서드를 호출 하 여 표시 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> .<br /><br /> 메뉴<br /> 드롭다운 메뉴를 제공 합니다. 드롭다운 메뉴에는 다음과 같은 특징이 있습니다.<br /><br /> -부모를 해당 정의에서 고려 합니다.<br />-부모 그룹이 나 CommandPlacement를 그룹에 포함 해야 합니다.<br />-다른 종류의 메뉴에서 하위 메뉴를 사용할 수 있습니다.<br />-부모 메뉴가 표시 될 때마다 자동으로 표시 됩니다.<br />-VSPackage 코드를 표시 하기 위해 구현 하지 않아도 됩니다.<br /><br /> MenuController<br /> 일반적으로 도구 모음에 사용 되는 분할 단추 드롭다운 메뉴를 제공 합니다. MenuController 메뉴에는 다음과 같은 특징이 있습니다.<br /><br /> -부모 또는 CommandPlacement를 통해 다른 메뉴에 포함 되어야 합니다.<br />-부모를 해당 정의에서 고려 합니다.<br />-모든 종류의 메뉴를 부모로 사용할 수 있습니다.<br />-부모 메뉴가 표시 될 때마다 자동으로 사용할 수 있게 됩니다.<br />-메뉴를 표시 하도록 프로그래밍 방식으로 지원할 필요가 없습니다.<br /><br /> 분할 단추 메뉴의 명령이 메뉴 단추에 표시 됩니다. 표시 되는 명령에는 다음 특징 중 하나가 있습니다.<br /><br /> -명령이 계속 표시 되 고 사용 하도록 설정 된 경우에 사용 되는 마지막 명령입니다.<br />-첫 번째로 표시 되는 명령입니다.<br /><br /> MenuControllerLatched<br /> 명령을 래치 된 상태로 표시 하 여 명령을 기본 선택 항목으로 지정할 수 있는 분할 단추 드롭다운 메뉴를 제공 합니다.<br /><br /> 래치 된 명령은 일반적으로 확인 표시를 표시 하 여 메뉴에 선택 된 대로 표시 되는 명령입니다. 인터페이스의 메서드 구현에서 OLECMDF_LATCHED 플래그가 설정 되어 있으면 명령이 래치 된 것으로 표시 될 수 있습니다 `QueryStatus` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . 메뉴 메뉴에는 다음과 같은 특징이 있습니다.<br /><br /> -부모 그룹이 나 CommandPlacement를 통해 다른 메뉴에 포함 되어야 합니다.<br />-부모를 해당 정의에서 고려 합니다.<br />-모든 종류의 메뉴를 부모로 사용할 수 있습니다.<br />-부모 메뉴가 표시 될 때마다 사용할 수 있습니다.<br />-메뉴를 표시 하도록 프로그래밍 방식으로 지원할 필요가 없습니다.<br /><br /> 분할 단추 메뉴의 명령이 메뉴 단추에 표시 됩니다. 표시 되는 명령에는 다음 특징 중 하나가 있습니다.<br /><br /> -래치 된 첫 번째 표시 된 명령입니다.<br />-첫 번째로 표시 되는 명령입니다.<br /><br /> 도구 모음<br /> 도구 모음을 제공 합니다. 도구 모음에는 다음과 같은 특징이 있습니다.<br /><br /> -정의에서 부모를 무시 합니다.<br />-CommandPlacement를 사용 하는 것이 아니라 어떤 그룹의 하위 메뉴도 만들 수 없습니다.<br />- **보기** 메뉴에서 **도구 모음** 을 클릭 하 여 항상 표시할 수 있습니다.<br />- [VisibilityItem](../extensibility/visibilityitem-element.md)을 사용 하 여 표시할 수 있습니다.<br />-코드를 만들 필요가 없습니다. 도구 모음을 만드는 방법에 대 한 예제는 [도구 모음 추가](../extensibility/adding-a-toolbar.md)를 참조 하세요.<br /><br /> ToolWindowToolbar<br /> 도구 모음이 개발 환경에 연결 되어 있는 것 처럼 특정 도구 창에 연결 된 도구 모음을 제공 합니다.<br /><br /> -정의에서 부모를 무시 합니다.<br />-CommandPlacement를 사용 하는 것이 아니라 어떤 그룹의 하위 메뉴도 만들 수 없습니다.<br />-도구 모음을 호스팅하는 도구 창이 표시 되 고 VSPackage에서 도구 모음을 도구 창에 명시적으로 추가 하는 경우에만 표시 됩니다. 이는 일반적으로 도구 창 프레임에서 도구 모음 호스트 속성 (인터페이스로 표시 됨)을 가져온 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> 다음 메서드를 호출 하 여 도구 창을 만들 때 수행 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> .|  
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|Parent|선택 사항입니다. 메뉴 항목의 부모 요소입니다.|  
|CommandFlag|필수 요소. [명령 플래그 요소](../extensibility/command-flag-element.md)를 참조 하세요. 메뉴의 유효한 CommandFlag 값은 다음과 같습니다.<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked 됨**<br />-   **Defaultinvisible** 않음-이 플래그는 도구 모음의 표시에 영향을 주지 않습니다.<br />-   **DontCache**<br />-   **Dynamicvisibility** -이 플래그는 도구 모음의 표시에 영향을 주지 않습니다.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **Noa를 닫습니다.**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|문자열|필수 요소. [Strings 요소](../extensibility/strings-element.md)를 참조 하세요. 자식 `ButtonText` 요소를 정의 해야 합니다.|  
|주석|선택적 설명입니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[Menus 요소](../extensibility/menus-element.md)|VSPackage가 구현 하는 모든 메뉴를 정의 합니다.|  
  
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
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)