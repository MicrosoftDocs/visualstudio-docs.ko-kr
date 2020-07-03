---
title: 사용자 설정 저장소에 쓰는 중 | Microsoft Docs
ms.date: 05/23/2019
ms.topic: how-to
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec4d9cdda975d0f80e9d8523ec18a19c24c9418a
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85906205"
---
# <a name="writing-to-the-user-settings-store"></a>사용자 설정 저장소에 쓰기
사용자 설정은 **도구/옵션** 대화 상자, 속성 창 및 기타 특정 대화 상자와 같은 쓰기 가능한 설정입니다. Visual Studio 확장에서는이를 사용 하 여 소량의 데이터를 저장할 수 있습니다. 이 연습에서는 사용자 설정 저장소에서 읽고 쓰는 방법으로 Visual Studio에 메모장을 외부 도구로 추가 하는 방법을 보여 줍니다.

## <a name="writing-to-the-user-settings-store"></a>사용자 설정 저장소에 쓰기

1. Usersettings사용자 확장 이라는 VSIX 프로젝트를 만든 다음 UserSettingsStoreCommand 이라는 사용자 지정 명령을 추가 합니다. 사용자 지정 명령을 만드는 방법에 대 한 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md) 를 참조 하세요.

2. UserSettingsStoreCommand.cs에서 다음 using 지시문을 추가 합니다.

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. MenuItemCallback에서 메서드의 본문을 삭제 하 고 다음과 같이 사용자 설정 저장소를 가져옵니다.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. 이제 메모장이 외부 도구로 이미 설정 되어 있는지 확인 합니다. 모든 외부 도구를 반복 하 여 다음과 같이 ToolCmd 설정이 "Notepad" 인지 여부를 확인 해야 합니다.

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

5. 메모장을 외부 도구로 설정 하지 않은 경우 다음과 같이 설정 합니다.

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

6. 코드를 테스트 합니다. 메모장은 외부 도구로 추가 되므로 두 번째로 실행 하기 전에 레지스트리를 롤백해야 합니다.

7. 코드를 빌드하고 디버깅을 시작 합니다.

8. **도구** 메뉴에서 **UserSettingsStoreCommand 호출**을 클릭 합니다. 그러면 메모장이 **도구** 메뉴에 추가 됩니다.

9. 이제 도구/옵션 메뉴에 메모장이 표시 되 고 **메모장** 을 클릭 하면 메모장의 인스턴스가 표시 됩니다.
