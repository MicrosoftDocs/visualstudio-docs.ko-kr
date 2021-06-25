---
title: 메뉴 항목에 바로 가기 키 바인딩 | Microsoft Docs
description: Visual Studio 바로 가기 키를 기본 편집기 또는 사용자 지정 편집기용 사용자 지정 단추, 메뉴 항목 또는 도구 모음 명령에 매핑하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a9591a7412b0bcaf506483a16a6660790df5f40
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900436"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>메뉴 항목에 바로 가기 키 바인딩
바로 가기 키를 사용자 지정 메뉴 명령에 바인딩하려면 패키지의 *.vsct* 파일에 항목을 추가하면 됩니다. 이 항목에서는 바로 가기 키를 사용자 지정 단추, 메뉴 항목 또는 도구 모음 명령에 매핑하는 방법과 기본 편집기에서 키보드 매핑을 적용하거나 사용자 지정 편집기로 제한하는 방법에 대해 설명합니다.

 기존 Visual Studio 메뉴 항목에 바로 가기 키를 할당하려면 [바로 가기 키 식별 및 사용자 지정을 참조하세요.](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

## <a name="choose-a-key-combination"></a>키 조합 선택
 Visual Studio 이미 많은 바로 가기 키가 사용되고 있습니다. 중복 바인딩은 검색하기 어려우며 예기치 않은 결과가 발생할 수 있으므로 둘 이상의 명령에 동일한 바로 가기를 할당하면 안 됩니다. 따라서 바로 가기를 할당하기 전에 바로 가기의 가용성을 확인하는 것이 좋습니다.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>바로 가기 키의 가용성을 확인하려면

1. 도구   >  **옵션**  >  **환경** 창에서 **키보드** 를 선택합니다.

2. **에서 새 바로 가기 사용이** **전역** 으로 설정되어 있는지 확인합니다.

3. 바로 **가기 키 누르기** 상자에 사용할 바로 가기 키를 입력합니다.

    바로 가기가 Visual Studio 이미 사용된 경우 현재 에서 사용하는 바로 가기 상자에 바로 **가기가** 현재 호출하는 명령이 표시됩니다.

4. 매핑되지 않은 키를 찾을 때까지 다른 키 조합을 시도합니다.

   > [!NOTE]
   > **Alt** 키를 사용하는 바로 가기 키는 메뉴를 열고 명령을 직접 실행하지 않을 수 있습니다. 따라서 **Alt** 를 포함하는 바로 가기를 입력하면 **현재 상자에서 사용하는** 바로 가기가 비어 있을 수 있습니다. **옵션** 대화 상자를 닫은 다음 키를 눌러 바로 가기가 메뉴를 열지 않는지 확인할 수 있습니다.

   다음 절차에서는 메뉴 명령이 있는 기존 VSPackage가 있다고 가정합니다. 이 작업을 수행하는 데 도움이 필요한 경우 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)살펴보세요.

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>명령에 바로 가기 키를 할당하려면

1. 패키지에 대한 *.vsct* 파일을 엽니다.

2. 비어 있는 섹션을 만듭니다 `<KeyBindings>` `<Commands>` 합니다(아직 없는 경우).

   > [!WARNING]
   > 키 바인딩에 대한 자세한 내용은 [키 바인딩을 참조하세요.](../extensibility/keybinding-element.md)

    섹션에서 `<KeyBindings>` `<KeyBinding>` 항목을 만듭니다.

    및 `guid`  `id` 특성을 호출하려는 명령의 특성으로 설정합니다.

    특성을 `mod1` **Control**, **Alt** 또는 **Shift** 로 설정합니다.

    KeyBindings 섹션은 다음과 같습니다.

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   바로 가기 키에 두 개 이상의 키가 필요한 경우 `mod2` 및 `key2` 특성을 설정합니다.

   대부분의 경우 **Shift 키를** 누르면 대부분의 영숫자 키가 대문자 또는 기호를 입력하게 되므로 두 번째 한정자 없이는 Shift 키를 사용하면 안 됩니다.

   가상 키 코드를 사용하면 연결된 문자가 없는 특수 키(예: 함수 키 및 **백스페이스** 키)에 액세스할 수 있습니다. 자세한 내용은 [가상 키 코드 를 참조하세요.](/windows/desktop/inputdev/virtual-key-codes)

   Visual Studio 편집기에서 명령을 사용할 수 있도록 하려면 `editor` 특성을 로 `guidVSStd97` 설정합니다.

   사용자 지정 편집기에서만 명령을 사용할 수 있도록 하려면 `editor` 사용자 지정 편집기를 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 포함하는 VSPackage를 만들 때 패키지 템플릿에서 생성된 사용자 지정 편집기의 이름으로 특성을 설정합니다. 이름 값을 찾으려면 섹션에서 `<Symbols>` `<GuidSymbol>` `name` 특성이 "."로 끝나는 노드를 `editorfactory` 찾습니다. 사용자 지정 편집기의 이름입니다.

## <a name="example-1"></a>예제 1
 이 예제에서는 바로 가기 키 **Ctrl** + **Alt** + **C를** 라는 패키지의 명령에 `cmdidMyCommand` 바인딩합니다. `MyPackage`

```
<CommandTable>
. . .
<Commands>
. . .
</Commands>
<KeyBindings>
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />
</KeyBindings>
. . .
</CommandTable>
```

## <a name="example-2"></a>예 2
 이 예제에서는 바로 가기 키 **Ctrl** + **B를** 라는 프로젝트의 라는 명령에 바인딩합니다. `cmdidBold` `TestEditor` 명령은 사용자 지정 편집기에서만 사용할 수 있으며 다른 편집기에서는 사용할 수 없습니다.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>참조
- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
