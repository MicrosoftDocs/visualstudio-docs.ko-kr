---
title: 솔루션 탐색기 도구 모음에 명령 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a14d87fbb5754d7af35d3add9e438351877a49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740340"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>솔루션 탐색기 도구 모음에 명령 추가
이 연습에서는 **솔루션 탐색기** 도구 모음에 단추를 추가하는 방법을 보여 주며 이 연습에서는 단추를 추가합니다.

 도구 모음 또는 메뉴의 모든 명령을 Visual Studio의 단추라고 합니다. 단추를 클릭하면 명령 처리기의 코드가 실행됩니다. 일반적으로 관련 명령은 하나의 그룹을 형성하기 위해 함께 그룹화됩니다. 메뉴 또는 도구 모음은 그룹의 컨테이너 역할을 합니다. 우선 순위는 그룹의 개별 명령이 메뉴 또는 도구 모음에 표시되는 순서를 결정합니다. 가시성을 제어하여 단추를 도구 모음 또는 메뉴에 표시하지 않도록 할 수 있습니다. *.vsct* 파일의 `<VisibilityConstraints>` 섹션에 나열된 명령은 연결된 컨텍스트에만 나타납니다. 표시 는 그룹에 적용할 수 없습니다.

 메뉴, 도구 모음 명령 및 *.vsct* 파일에 대한 자세한 내용은 [명령, 메뉴 및 도구 모음 을](../extensibility/internals/commands-menus-and-toolbars.md)참조하십시오.

> [!NOTE]
> 명령 테이블 구성 *(.ct)* 파일 대신 XML 명령 테이블 *(.vsct)* 파일을 사용하여 VSPackage에 메뉴와 명령이 표시되는 방식을 정의합니다. 자세한 내용은 [Visual Studio 명령 테이블(를 참조하십시오. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-an-extension-with-a-menu-command"></a>메뉴 명령으로 확장 만들기
 라는 VSIX 프로젝트를 `SolutionToolbar`만듭니다. **도구**모음 단추라는 메뉴 명령 항목 템플릿을 추가합니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)참조하십시오.

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>솔루션 탐색기 도구 모음에 단추 추가
 이 연습 섹션에서는 **솔루션 탐색기** 도구 모음에 단추를 추가하는 방법을 보여 주며 이 섹션에서는 단추를 클릭하면 콜백 메서드의 코드가 실행됩니다.

1. 도구 *모음ButtonPackage.vsct* 파일에서 섹션으로 `<Symbols>` 이동합니다. 노드에는 `<GuidSymbol>` 패키지 템플릿에서 생성된 메뉴 그룹과 명령이 포함되어 있습니다. 이 `<IDSymbol>` 노드에 요소를 추가하여 명령을 보유할 그룹을 선언합니다.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. `<Groups>` 섹션에서 기존 그룹 항목 후 이전 단계에서 선언한 새 그룹을 정의합니다.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     상위 GUID:ID 쌍을 `guidSHLMainMenu` 설정하고 `IDM_VS_TOOL_PROJWIN` 이 그룹을 **솔루션 탐색기** 도구 모음에 놓고 우선 순위가 높은 값을 설정하면 다른 명령 그룹 다음으로 설정됩니다.

3. `<Buttons>` 섹션에서 생성된 `<Button>` 항목의 상위 ID를 변경하여 이전 단계에서 정의한 그룹을 반영합니다. 수정된 `<Button>` 요소는 다음과 같아야 합니다.

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다.

     **솔루션 탐색기** 도구 모음은 기존 단추의 오른쪽에 새 명령 단추를 표시해야 합니다. 단추 아이콘은 스트라이크스루입니다.

5. 새 단추를 클릭합니다.

     솔루션 도구 모음 내부에 도구 모음 단추 패키지 라는 메시지가 있는 대화 상자가 표시 되어야 **합니다.ToolbarButton.MenuItemCallback()** 표시 되어야 합니다.

## <a name="control-the-visibility-of-a-button"></a>버튼의 가시성 제어
 연습의 이 섹션에서는 도구 모음에서 단추의 가시성을 제어하는 방법을 보여 주며 이 섹션에서는 `<VisibilityConstraints>` *SolutionToolbar.vsct* 파일 섹션에 하나 이상의 프로젝트에 컨텍스트를 설정하면 프로젝트 또는 프로젝트가 열려 있을 때만 단추를 표시하도록 제한할 수 있습니다.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>하나 이상의 프로젝트가 열려 있을 때 단추를 표시하려면

1. `<Buttons>` *ToolbarButtonPackage.vsct*의 `<Button>` `<Strings>` 섹션에서는 기존 요소와 `<Icons>` 태그 사이에 두 개의 명령 플래그를 추가합니다.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    섹션의 `DynamicVisibility` 항목이 적용될 수 있도록 `<VisibilityConstraints>` `DefaultInvisible` 및 플래그를 설정해야 합니다.

2. 두 `<VisibilityConstraints>` 개의 `<VisibilityItem>` 항목이 있는 섹션을 만듭니다. 닫는 `</Commands>` 태그 바로 직후에 새 섹션을 넣습니다.

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasSingleProject" />
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasMultipleProjects" />
   </VisibilityConstraints>
   ```

    각 가시성 항목은 지정된 단추가 표시되는 조건을 나타냅니다. 여러 조건을 적용하려면 동일한 단추에 대해 여러 항목을 만들어야 합니다.

3. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다.

    **솔루션 탐색기** 도구 모음에는 스트라이크스루 버튼이 포함되어 있지 않습니다.

4. 프로젝트가 포함된 모든 솔루션을 엽니다.

    스트라이크 스루 버튼은 기존 버튼의 오른쪽에있는 도구 모음에 나타납니다.

5. **파일** 메뉴에서 **솔루션 닫기**를 클릭합니다. 도구 모음에서 버튼이 사라집니다.

   VSPackage가 로드될 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 때까지 단추의 가시성이 제어됩니다. VSPackage를 로드한 후 VSPackage에 의해 버튼의 가시성이 제어됩니다.  자세한 내용은 [메뉴 명령 및 올레메뉴 명령 서를 참조하십시오.](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)

## <a name="see-also"></a>참조
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
