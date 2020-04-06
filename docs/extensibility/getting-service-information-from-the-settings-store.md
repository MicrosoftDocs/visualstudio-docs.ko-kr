---
title: 설정 저장소에서 서비스 정보 얻기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b15d5c9f122ca66d21940b9998969b0d39d1a74d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711367"
---
# <a name="get-service-information-from-the-settings-store"></a>설정 저장소에서 서비스 정보 받기
설정 저장소를 사용하여 사용 가능한 모든 서비스를 찾거나 특정 서비스가 설치되어 있는지 확인할 수 있습니다. 서비스 클래스의 유형을 알고 있어야 합니다.

## <a name="to-list-the-available-services"></a>사용 가능한 서비스를 나열하려면

1. 명명된 `FindServicesExtension` VSIX 프로젝트를 만든 다음 . `FindServicesCommand` 사용자 지정 명령을 만드는 방법에 대한 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md) 참조하십시오.

2. *FindServicesCommand.cs*지시문을 사용하여 다음을 추가합니다.

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. 구성 설정 저장소를 가져옵니다. 이 컬렉션에는 사용 가능한 모든 서비스가 포함됩니다. 메서드에서 `MenuItemCommand` 기존 코드를 제거 하 고 다음으로 대체 합니다.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string message = "Available services:\n";
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");
        int n = 0;
        foreach (string service in collection)
        {
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";
        }

        MessageBox.Show(message);
    }
    ```

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다.

5. 실험인스턴스에서 **도구** 메뉴에서 **FindServicesCommand 호출을**클릭합니다.

     모든 서비스를 나열하는 메시지 상자가 표시됩니다.

     이러한 설정을 확인하려면 레지스트리 편집기를 사용할 수 있습니다.

## <a name="find-a-specific-service"></a>특정 서비스 찾기
 메서드를 <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> 사용하여 특정 서비스가 설치되었는지 여부를 확인할 수도 있습니다. 서비스 클래스의 유형을 알고 있어야 합니다.

1. 이전 절차에서 만든 프로젝트의 MenuItemCallback에서 서비스의 GUID에 의해 명명된 하위 컬렉션이 있는 `Services` 컬렉션에 대한 구성 설정 저장소를 검색합니다. 이 경우 도움말 서비스를 찾습니다.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);
        string message = "Help Service Available: " + hasHelpService;

        MessageBox.Show(message);
    }
    ```

2. 프로젝트를 빌드하고 디버깅을 시작합니다.

3. 실험인스턴스에서 **도구** 메뉴에서 **FindServicesCommand 호출을**클릭합니다.

     사용 가능한 도움말 서비스 텍스트가 있는 메시지가 **True** **표시됩니다.** **False** 이 설정을 확인하려면 이전 단계에 표시된 대로 레지스트리 편집기를 사용할 수 있습니다.
