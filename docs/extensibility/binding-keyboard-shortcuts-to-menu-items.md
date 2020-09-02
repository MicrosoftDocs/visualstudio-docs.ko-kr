---
title: 메뉴 항목에 바로 가기 키 바인딩 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740028"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>메뉴 항목에 바로 가기 키 바인딩
사용자 지정 메뉴 명령에 바로 가기 키를 바인딩하려면 패키지에 대 한 *vsct* 파일에 항목을 추가 하면 됩니다. 이 항목에서는 사용자 지정 단추, 메뉴 항목 또는 도구 모음 명령에 바로 가기 키를 매핑하는 방법과 기본 편집기에서 키보드 매핑을 적용 하거나 사용자 지정 편집기로 제한 하는 방법에 대해 설명 합니다.

 기존 Visual Studio 메뉴 항목에 바로 가기 키를 할당 하려면 [바로 가기 키 식별 및 사용자 지정](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)을 참조 하세요.

## <a name="choose-a-key-combination"></a>키 조합 선택
 많은 키보드 바로 가기 키가 Visual Studio에서 이미 사용 되 고 있습니다. 중복 바인딩이 검색 하기 어렵고 예측할 수 없는 결과가 발생할 수도 있으므로 둘 이상의 명령에 동일한 바로 가기를 할당 하면 안 됩니다. 따라서 할당 하기 전에 바로 가기의 가용성을 확인 하는 것이 좋습니다.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>바로 가기 키의 사용 가능 여부를 확인 하려면

1. **도구**  >  **옵션**  >  **환경** 창에서 **키보드**를 선택 합니다.

2. **에서 새 바로 가기 사용** 이 **전역**으로 설정 되어 있는지 확인 합니다.

3. **바로 가기 키 누르기** 상자에 사용 하려는 바로 가기 키를 입력 합니다.

    Visual Studio에서 바로 가기를 이미 사용 하는 경우 현재 상자에 사용 되는 **바로** 가기에서 현재 호출 하는 명령이 표시 됩니다.

4. 매핑되지 않은 키를 찾을 때까지 다른 키 조합을 사용해 보세요.

   > [!NOTE]
   > **Alt** 키를 사용 하는 바로 가기 키는 메뉴를 열고 명령을 직접 실행 하지 않을 수 있습니다. 따라서 **Alt**키를 포함 하는 바로 가기를 입력 하면 **현재 box에서 사용 하는 바로 가기가** 비어 있을 수 있습니다. **옵션** 대화 상자를 닫은 다음 키를 눌러 바로 가기에서 메뉴가 열리지 않는지 확인할 수 있습니다.

   다음 절차에서는 기존 VSPackage 메뉴 명령을 사용 하는 것으로 가정 합니다. 이 작업을 수행 하는 데 도움이 필요 하면 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 살펴보세요.

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>명령에 바로 가기 키를 할당 하려면

1. 패키지에 대 한 *. vsct* 파일을 엽니다.

2. `<KeyBindings>`가 아직 없는 경우에는 빈 섹션을 만듭니다 `<Commands>` .

   > [!WARNING]
   > 키 바인딩에 대 한 자세한 내용은 [Keybinding](../extensibility/keybinding-element.md)를 참조 하세요.

    섹션에서 `<KeyBindings>` 항목을 만듭니다 `<KeyBinding>` .

    `guid`및 특성을 `id` 호출 하려는 명령의 명령으로 설정 합니다.

    특성을 `mod1` **Control**, **Alt**또는 **Shift**로 설정 합니다.

    KeyBindings 섹션은 다음과 같습니다.

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   바로 가기 키에 세 개 이상의 키가 필요한 경우 `mod2` 및 특성을 설정 `key2` 합니다.

   대부분의 경우 두 번째 한정자 없이 **shift** 를 사용 하면 안 됩니다 .이 경우에는 대부분의 영숫자 키에 대문자 또는 기호가 입력 되기 때문입니다.

   가상 키 코드를 사용 하면 함수 키와 **백스페이스** 키와 같이 연결 된 문자가 없는 특수 키에 액세스할 수 있습니다. 자세한 내용은 [가상 키 코드](/windows/desktop/inputdev/virtual-key-codes)를 참조 하세요.

   Visual Studio 편집기에서 명령을 사용할 수 있도록 하려면 특성을로 설정 `editor` `guidVSStd97` 합니다.

   사용자 지정 편집기 에서만 명령을 사용할 수 있도록 하려면 `editor` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 사용자 지정 편집기를 포함 하는 VSPackage를 만들 때 패키지 템플릿에서 생성 된 사용자 지정 편집기의 이름으로 특성을 설정 합니다. 이름 값을 찾으려면 `<Symbols>` `<GuidSymbol>` `name` 특성이 "."로 끝나는 노드에 대 한 섹션을 확인 합니다 `editorfactory` . 사용자 지정 편집기의 이름입니다.

## <a name="example"></a>예제
 이 예제에서는 바로 가기 **키 Ctrl** + **Alt** + **C** 를 `cmdidMyCommand` 이름이 인 패키지의 명령에 바인딩합니다 `MyPackage` .

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
 이 예제에서는 바로 가기 **키 Ctrl** + **B** 를 `cmdidBold` 라는 프로젝트의 명령에 바인딩합니다 `TestEditor` . 명령은 사용자 지정 편집기 에서만 사용할 수 있으며 다른 편집기에서는 사용할 수 없습니다.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>참조
- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
