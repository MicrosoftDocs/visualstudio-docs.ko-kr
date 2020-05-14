---
title: 메뉴 항목에 대한 키보드 단축키 바인딩 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94feafbc614be61aaa4eef9e26669c0fbe901ed5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740028"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>키보드 단축키를 메뉴 항목에 바인딩
키보드 단축키를 사용자 지정 메뉴 명령에 바인딩하려면 패키지의 *.vsct* 파일에 항목을 추가하면 됩니다. 이 항목에서는 키보드 단축을 사용자 지정 단추, 메뉴 항목 또는 도구 모음 명령에 매핑하는 방법과 기본 편집기에서 키보드 매핑을 적용하거나 사용자 지정 편집기로 제한하는 방법을 설명합니다.

 기존 Visual Studio 메뉴 항목에 키보드 단축키를 할당하려면 [키보드 단축키 식별 및 사용자 지정을](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)참조하십시오.

## <a name="choose-a-key-combination"></a>키 조합 선택
 많은 키보드 단축키는 이미 Visual Studio에서 사용되고 있습니다. 중복 바인딩을 감지하기 어렵고 예기치 않은 결과가 발생할 수 있으므로 둘 이상의 명령에 동일한 바로 가기를 할당해서는 안 됩니다. 따라서 바로 가기를 할당하기 전에 바로 가기를 사용할 수 있는지 확인하는 것이 좋습니다.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>바로 가기 키의 가용성을 확인하려면

1. **도구** > **옵션** > **환경** 창에서 **키보드**를 선택합니다.

2. **에서 새 바로 가기 사용이** **전역으로**설정되어 있는지 확인합니다.

3. 바로 **가기 키** 상자에서 사용하려는 바로 가기 키를 입력합니다.

    바로 가기는 Visual Studio에서 이미 사용 중인 경우 **현재 상자에서 사용하는 바로 가기에는** 바로 가기에서 현재 호출하는 명령이 표시됩니다.

4. 매핑되지 않은 키를 찾을 때까지 다른 키 조합을 사용해 보십시오.

   > [!NOTE]
   > **Alt를** 사용하는 바로 가기 키는 메뉴를 열고 명령을 직접 실행하지 않을 수 있습니다. 따라서 **Alt를**포함하는 바로 가기를 입력할 때 **현재 상자에서 사용하는** 바로 가기는 비어 있을 수 있습니다. 바로 가기 **옵션** 대화 상자를 닫은 다음 키를 눌러 메뉴를 열지 않는지 확인할 수 있습니다.

   다음 절차에서는 메뉴 명령이 있는 기존 VSPackage가 있다고 가정합니다. 도움이 필요한 경우 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)살펴보십시오.

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>명령에 키보드 단축을 할당하려면

1. 패키지에 대한 *.vsct* 파일을 엽니다.

2. 빈 `<KeyBindings>` 섹션이 아직 `<Commands>` 없는 경우 다음 을 만듭니다.

   > [!WARNING]
   > 키 바인딩에 대한 자세한 내용은 [키 바인딩](../extensibility/keybinding-element.md)을 참조하십시오.

    `<KeyBindings>` 섹션에서 `<KeyBinding>` 항목을 만듭니다.

    `guid` 호출할 `id` 명령의 속성과 특성을 설정합니다.

    특성을 `mod1` **제어,** **Alt**또는 **Shift로**설정합니다.

    KeyBindings 섹션은 다음과 같이 보입니다.

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   키보드 단축키에 두 개 이상의 키가 `mod2` `key2` 필요한 경우 및 특성을 설정합니다.

   대부분의 경우 **Shift를** 누르면 대부분의 상문자 또는 기호를 입력하는 대부분의 상형 키가 발생하므로 두 번째 수정자 없이는 사용하지 않아야 합니다.

   가상 키 코드를 사용하면 함수 키 및 **백스페이스** 키와 같은 문자가 없는 특수 키에 액세스할 수 있습니다. 자세한 내용은 [가상 키 코드를](/windows/desktop/inputdev/virtual-key-codes)참조하십시오.

   Visual Studio 편집기에서 명령을 사용할 수 `editor` 있도록 `guidVSStd97`하려면 특성을 로 설정합니다.

   사용자 지정 편집기에서만 명령을 사용할 `editor` 수 있도록 하려면 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 사용자 지정 편집기를 포함하는 VSPackage를 만들 때 패키지 템플릿에서 생성된 사용자 지정 편집기의 이름으로 특성을 설정합니다. 이름 값을 `<Symbols>` 찾으려면 `<GuidSymbol>` `name` 섹션에서 특성이 "로 끝나는 노드를`editorfactory`찾습니다. 사용자 지정 편집기의 이름입니다.

## <a name="example"></a>예제
 이 예제에서는 키보드 단축키 **Ctrl**+**Alt**+**C를** `cmdidMyCommand` `MyPackage`라는 패키지에 명명된 명령에 바인딩합니다.

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

## <a name="example"></a>예제
 이 예제에서는 키보드 단축커 **Ctrl**+**B를** 라는 `cmdidBold` `TestEditor`프로젝트에 명명된 명령에 바인딩합니다. 이 명령은 사용자 지정 편집기에서만 사용할 수 있으며 다른 편집기에서는 사용할 수 없습니다.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>참조
- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
