---
title: 비주얼 스튜디오 메뉴 모음에 메뉴 추가 | 마이크로 소프트 문서
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91e5a6e1714dbb87abc67fbf722c3bbd1a194a5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740316"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>비주얼 스튜디오 메뉴 모음에 메뉴 추가

이 연습에서는 IDE(Visual Studio 통합 개발 환경)의 메뉴 모음에 메뉴를 추가하는 방법을 보여 줍니다. IDE 메뉴 모음에는 **파일,** **편집,** **보기,** **창**및 도움말과 같은 메뉴 범주가 포함되어 **있습니다.**

Visual Studio 메뉴 모음에 새 메뉴를 추가하기 전에 명령을 기존 메뉴 내에 배치할지 여부를 고려합니다. 명령 배치에 대한 자세한 내용은 [Visual Studio의 메뉴 및 명령을](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)참조하십시오.

메뉴는 프로젝트의 *.vsct* 파일에 선언됩니다. 메뉴 및 *.vsct* 파일에 대한 자세한 내용은 [명령, 메뉴 및 도구 모음을](../extensibility/internals/commands-menus-and-toolbars.md)참조하십시오.

이 연습을 완료하면 하나의 명령이 포함된 **TestMenu라는** 메뉴를 만들 수 있습니다.

> [!NOTE]
> VS 2019에서는 확장에 의해 기여하는 최상위 메뉴가 확장 메뉴 아래에 **배치됩니다.**

## <a name="prerequisites"></a>사전 요구 사항

Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>사용자 지정 명령 항목 템플릿이 있는 VSIX 프로젝트 만들기

1. 라는 VSIX 프로젝트를 `TopLevelMenu`만듭니다. 새 프로젝트 대화 상자에서 "vsix"를 검색하여 VSIX **프로젝트** 템플릿을 찾을 수 있습니다.  자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)참조하십시오.

2. 프로젝트가 열리면 **TestCommand**라는 사용자 지정 명령 항목 템플릿을 추가합니다. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** >  선택합니다. 새 **항목 추가** 대화 상자에서 **시각적 C# / 확장성으로** 이동하여 **사용자 지정 명령을 선택합니다.** 창 아래쪽의 **이름** 필드에서 명령 파일 이름을 *TestCommand.cs*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>IDE 메뉴 모음에서 메뉴 만들기

::: moniker range="vs-2017"

1. **솔루션 탐색기에서** *테스트명령 패키지.vsct*를 엽니다.

    파일 의 끝에는 여러 \< \<GuidSymbol> 노드가 포함된 기호> 노드가 있습니다. guidTestCommandPackageCmdSet이라는 노드에서 다음과 같이 새 기호를 추가합니다.

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. > 그룹 \<> 바로 전에 \< \<명령> 노드에서 빈 메뉴> 노드를 만듭니다. \<메뉴> 노드에서 다음과 \<같이 메뉴> 노드를 추가합니다.

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

    메뉴의 `id` 및 값은 `guid` 명령 집합과 명령 집합의 특정 메뉴를 지정합니다.

    상위 `guid` `id` 값은 도구 및 추가 기능 메뉴가 포함된 Visual Studio 메뉴 모음의 섹션에 메뉴를 배치합니다.

    문자열 값은 `CommandName` 메뉴 항목에 텍스트가 표시되도록 지정합니다.

3. \<그룹> 섹션에서 \<그룹> 찾아 \<방금 추가한 메뉴를 가리키도록 부모> 요소를 변경합니다.

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    이렇게 하면 그룹이 새 메뉴의 일부가 됩니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. **솔루션 탐색기에서** *최상위 수준메뉴 패키지.vsct*를 엽니다.

    파일 의 끝에는 여러 \< \<GuidSymbol> 노드가 포함된 기호> 노드가 있습니다. guidTopLevelMenuPackageCmdSet이라는 노드에서 다음과 같이 새 기호를 추가합니다.

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. > 그룹 \<> 바로 전에 \< \<명령> 노드에서 빈 메뉴> 노드를 만듭니다. \<메뉴> 노드에서 다음과 \<같이 메뉴> 노드를 추가합니다.

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

    메뉴의 `id` 및 값은 `guid` 명령 집합과 명령 집합의 특정 메뉴를 지정합니다.

    상위 `guid` `id` 값은 도구 및 추가 기능 메뉴가 포함된 Visual Studio 메뉴 모음의 섹션에 메뉴를 배치합니다.

    문자열 값은 `CommandName` 메뉴 항목에 텍스트가 표시되도록 지정합니다.

3. \<그룹> 섹션에서 \<그룹> 찾아 \<방금 추가한 메뉴를 가리키도록 부모> 요소를 변경합니다.

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    이렇게 하면 그룹이 새 메뉴의 일부가 됩니다.

::: moniker-end

4. `Buttons` 섹션을 찾습니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 패키지 템플릿에서 부모가 로 `Button` 설정된 요소를 생성했습니다. `MyMenuGroup` 따라서 이 명령은 메뉴에 나타납니다.

## <a name="build-and-test-the-extension"></a>확장 빌드 및 테스트

1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스의 인스턴스가 나타나야 합니다.

::: moniker range="vs-2017"

2. 실험 인스턴스의 메뉴 모음에는 **TestMenu** 메뉴가 포함되어야 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

2. 실험 인스턴스의 **확장** 메뉴에는 **TestMenu** 메뉴가 포함되어야 합니다.

::: moniker-end

3. 테스트 **메뉴** 메뉴에서 **테스트 명령 호출을 클릭합니다.**

     메시지 상자가 나타나고 "TopLevelMenu.TestCommand.MenuItemCallback()" 안에 있는 TestCommand 패키지"라는 메시지가 표시되어야 합니다.

## <a name="see-also"></a>참조

- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
