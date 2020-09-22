---
title: 사용자 설정 저장소에 쓰는 중 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 764d9b81297c6bbefd1f5fdf7c77e4d514bb5045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842046"
---
# <a name="writing-to-the-user-settings-store"></a>사용자 설정 저장소에 쓰기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 설정은 **도구/옵션** 대화 상자, 속성 창 및 기타 특정 대화 상자와 같은 쓰기 가능한 설정입니다. Visual Studio 확장에서는이를 사용 하 여 소량의 데이터를 저장할 수 있습니다. 이 연습에서는 사용자 설정 저장소에서 읽고 쓰는 방법으로 Visual Studio에 메모장을 외부 도구로 추가 하는 방법을 보여 줍니다.  
  
### <a name="backing-up-your-user-settings"></a>사용자 설정 백업  
  
1. 프로시저를 디버깅 하 고 반복할 수 있도록 외부 도구 설정을 다시 설정할 수 있어야 합니다. 이렇게 하려면 필요할 때 복원할 수 있도록 원래 설정을 저장 해야 합니다.  
  
2. Regedit.exe를 엽니다.  
  
3. HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp\External Tools로 이동 \\ 합니다.  
  
    > [!NOTE]
    > \14.0Exp\ 및 \ 14.0가 아닌 키를 확인 하 고 있는지 확인 \\ 합니다. Visual Studio의 실험적 인스턴스를 실행 하는 경우 사용자 설정은 레지스트리 hive "14.0 Exp"에 있습니다.  
  
4. \External Tools \ 하위 키를 마우스 오른쪽 단추로 클릭 한 다음 **내보내기**를 클릭 합니다. **선택한 분기가** 선택 되어 있는지 확인 합니다.  
  
5. 결과 외부 도구 .reg 파일을 저장 합니다.  
  
6. 나중에 외부 도구 설정을 다시 설정 하려면 HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp\External Tools \ 레지스트리 키를 선택 하 고 상황에 맞는 메뉴에서 **삭제** 를 클릭 합니다.  
  
7. **키 삭제 확인** 대화 상자가 나타나면 **예**를 클릭 합니다.  
  
8. 이전에 저장 한 외부 Tools .reg 파일을 마우스 오른쪽 단추로 클릭 하 고 **연결 프로그램**을 클릭 한 다음 **레지스트리 편집기**를 클릭 합니다.  
  
## <a name="writing-to-the-user-settings-store"></a>사용자 설정 저장소에 쓰기  
  
1. Usersettings사용자 확장 이라는 VSIX 프로젝트를 만든 다음 UserSettingsStoreCommand 이라는 사용자 지정 명령을 추가 합니다. 사용자 지정 명령을 만드는 방법에 대 한 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md) 를 참조 하세요.  
  
2. UserSettingsStoreCommand.cs에서 다음 using 문을 추가 합니다.  
  
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
