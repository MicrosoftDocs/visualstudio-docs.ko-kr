---
title: Visual Studio 메뉴 모음에 메뉴 추가 | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39dee051991efe05b9a661ce1d213e71b456590b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904252"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Visual Studio 메뉴 모음에 메뉴 추가

이 연습에서는 Visual Studio IDE (통합 개발 환경)의 메뉴 모음에 메뉴를 추가 하는 방법을 보여 줍니다. IDE 메뉴 모음에는 **파일**, **편집**, **보기**, **창**및 **도움말과**같은 메뉴 범주가 있습니다.

Visual Studio 메뉴 모음에 새 메뉴를 추가 하기 전에 기존 메뉴에 명령을 배치 해야 하는지 여부를 고려 합니다. 명령 배치에 대 한 자세한 내용은 [Visual Studio에 대 한 메뉴 및 명령](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)을 참조 하세요.

메뉴는 프로젝트의 *. vsct* 파일에서 선언 됩니다. 메뉴 및 *vsct* 파일에 대 한 자세한 내용은 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)을 참조 하세요.

이 연습을 완료 하면 하나의 명령을 포함 하는 **testmenu** 라는 메뉴를 만들 수 있습니다.

:::moniker range=">=vs-2019"
> [!NOTE]
> Visual Studio 2019부터 확장에서 제공 하는 최상위 메뉴는 **확장** 메뉴 아래에 배치 됩니다.
:::moniker-end

## <a name="prerequisites"></a>사전 요구 사항

Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>사용자 지정 명령 항목 템플릿이 있는 VSIX 프로젝트 만들기

1. 이라는 VSIX 프로젝트를 만듭니다 `TopLevelMenu` . **새 프로젝트** 대화 상자에서 "vsix"를 검색 하 여 vsix 프로젝트 템플릿을 찾을 수 있습니다.  자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.

2. 프로젝트가 열리면 **testcommand**라는 사용자 지정 명령 항목 템플릿을 추가 합니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **Add**  >   **새 항목**추가를 선택 합니다. **새 항목 추가** 대화 상자에서 **Visual c #/확장성** 으로 이동 하 고 **사용자 지정 명령**을 선택 합니다. 창 맨 아래에 있는 **이름** 필드에서 명령 파일 이름을 *TestCommand.cs*로 변경 합니다.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>IDE 메뉴 모음에서 메뉴 만들기

::: moniker range="vs-2017"

1. **솔루션 탐색기**에서 *testcommandpackage. vsct*를 엽니다.

    파일의 끝에는 \<Symbols> 여러 노드를 포함 하는 노드가 있습니다 \<GuidSymbol> . GuidTestCommandPackageCmdSet 라는 노드에서 다음과 같이 새 기호를 추가 합니다.

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. \<Menus>이전 처럼 노드에 빈 노드를 만듭니다 \<Commands> \<Groups> . 노드에서 다음과 \<Menus> 같이 노드를 추가 합니다 \<Menu> .

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid`메뉴의 및 값은 명령 집합 `id` 및 명령 집합의 특정 메뉴를 지정 합니다.

    `guid` `id` 부모의 및 값은 도구 및 추가 기능 메뉴가 포함 된 Visual Studio 메뉴 모음의 섹션에서 메뉴를 배치 합니다.

    문자열의 값은 `CommandName` 텍스트가 메뉴 항목에 나타나도록 지정 합니다.

3. 섹션에서 \<Groups> 를 찾고 \<Group> \<Parent> 방금 추가한 메뉴를 가리키도록 요소를 변경 합니다.

   ```xml
   <Groups>
       <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    이렇게 하면 그룹이 새 메뉴의 일부가 됩니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. **솔루션 탐색기**에서 *TopLevelMenuPackage*을 엽니다.

    파일의 끝에는 \<Symbols> 여러 노드를 포함 하는 노드가 있습니다 \<GuidSymbol> . GuidTopLevelMenuPackageCmdSet 라는 노드에서 다음과 같이 새 기호를 추가 합니다.

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. \<Menus>이전 처럼 노드에 빈 노드를 만듭니다 \<Commands> \<Groups> . 노드에서 다음과 \<Menus> 같이 노드를 추가 합니다 \<Menu> .

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid`메뉴의 및 값은 명령 집합 `id` 및 명령 집합의 특정 메뉴를 지정 합니다.

    `guid` `id` 부모의 및 값은 도구 및 추가 기능 메뉴가 포함 된 Visual Studio 메뉴 모음의 섹션에서 메뉴를 배치 합니다.

    문자열의 값은 `CommandName` 텍스트가 메뉴 항목에 나타나도록 지정 합니다.

3. 섹션에서 \<Groups> 를 찾고 \<Group> \<Parent> 방금 추가한 메뉴를 가리키도록 요소를 변경 합니다.

   ```xml
   <Groups>
       <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    이렇게 하면 그룹이 새 메뉴의 일부가 됩니다.

::: moniker-end

4. `Buttons` 섹션을 찾습니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]패키지 템플릿에서 `Button` 부모 집합이로 설정 된 요소를 생성 합니다 `MyMenuGroup` . 그러면이 명령이 메뉴에 표시 됩니다.

## <a name="build-and-test-the-extension"></a>확장 빌드 및 테스트

1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스의 인스턴스가 표시 되어야 합니다.

::: moniker range="vs-2017"

2. 실험적 인스턴스의 메뉴 모음에는 **Testmenu** 메뉴가 포함 되어야 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

2. 실험적 인스턴스의 **확장** 메뉴에는 **testmenu** 메뉴가 있어야 합니다.

::: moniker-end

3. **Testmenu** 메뉴에서 **테스트 명령 호출**을 클릭 합니다.

     메시지 상자가 나타나고 "TestCommand Package in TopLevelMenu. MenuItemCallback ()" 라는 메시지가 표시 됩니다.

## <a name="see-also"></a>참조

- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
