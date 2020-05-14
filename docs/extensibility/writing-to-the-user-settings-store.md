---
title: 사용자 설정 저장소에 쓰기 | 마이크로 소프트 문서
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bed721cc084042c3ebe57639af28b7e9f13d206
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740369"
---
# <a name="writing-to-the-user-settings-store"></a>사용자 설정 저장소에 쓰기
사용자 설정은 **도구 / 옵션** 대화 상자, 속성 창 및 특정 다른 대화 상자의 것과 같은 쓰기 가능한 설정입니다. Visual Studio 확장은 이러한 확장을 사용하여 소량의 데이터를 저장할 수 있습니다. 이 연습에서는 사용자 설정 저장소를 읽고 작성하여 Visual Studio에 메모를 외부 도구로 추가하는 방법을 보여 주며 이 연습에서는 메모를 외부 도구로 추가하는 방법을 보여 주며, 이를 통해

## <a name="writing-to-the-user-settings-store"></a>사용자 설정 저장소에 쓰기

1. UserSettingsStoreExtension이라는 VSIX 프로젝트를 만든 다음 UserSettingsStoreCommand라는 사용자 지정 명령을 추가합니다. 사용자 지정 명령을 만드는 방법에 대한 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md) 참조하십시오.

2. UserSettingsStoreCommand.cs 지시문을 사용하여 다음을 추가합니다.

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. MenuItemCallback에서 메서드의 본문을 삭제하고 다음과 같이 사용자 설정 저장소를 가져옵니다.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. 이제 메모장이 이미 외부 도구로 설정되어 있는지 확인하십시오. 다음과 같이 ToolCmd 설정이 "메모장"인지 여부를 확인하려면 모든 외부 도구를 반복해야 합니다.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already an External Tool.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }
    }

    ```

5. 메모장을 외부 도구로 설정하지 않은 경우 다음과 같이 설정합니다.

    ```vb
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already installed.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }

        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";
         if (!hasNotepad)
        {
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);

            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);
        }
    }
    ```

6. 코드를 테스트합니다. 메모장을 외부 도구로 추가하므로 레지스트리를 다시 실행하기 전에 롤백해야 합니다.

7. 코드를 빌드하고 디버깅을 시작합니다.

8. **도구** 메뉴에서 **사용자 설정 스토어 명령 호출을**클릭합니다. 그러면 **도구** 메뉴에 메모장이 추가됩니다.

9. 이제 도구 / 옵션 메뉴에 메모장이 표시되고 **메모장을** 클릭하면 메모장이 표시됩니다.
