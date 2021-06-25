---
title: 설정 저장소 | 서비스 정보 얻기 Microsoft Docs
description: 설정 저장소를 사용하여 사용 가능한 모든 서비스를 찾거나 특정 서비스가 설치되어 있는지 확인하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb014803945ea88cd6c2c27eee8c120059014a18
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900644"
---
# <a name="get-service-information-from-the-settings-store"></a>설정 저장소에서 서비스 정보 얻기
설정 저장소를 사용하여 사용 가능한 모든 서비스를 찾거나 특정 서비스가 설치되어 있는지 확인할 수 있습니다. 서비스 클래스의 형식을 알고 있어야 합니다.

## <a name="to-list-the-available-services"></a>사용 가능한 서비스를 나열하려면

1. 라는 VSIX 프로젝트를 만든 `FindServicesExtension` 다음 라는 사용자 지정 명령을 추가합니다. `FindServicesCommand` 사용자 지정 명령을 만드는 방법에 대한 자세한 내용은 메뉴 명령을 [사용하여 확장 만들기를 참조하세요.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. *FindServicesCommand.cs에서* 다음 using 지시문을 추가합니다.

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. 구성 설정 저장소를 가져옵니다. 그런 다음 Services라는 하위 데이터 정렬을 찾습니다. 이 컬렉션에는 사용 가능한 모든 서비스가 포함됩니다. `MenuItemCommand`메서드에서 기존 코드를 제거하고 다음으로 대체합니다.

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

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 나타납니다.

5. 실험적 인스턴스의 **도구** 메뉴에서 **FindServices 호출명령을** 클릭합니다.

     모든 서비스를 나열하는 메시지 상자가 표시됩니다.

     이러한 설정을 확인하려면 레지스트리 편집기를 사용할 수 있습니다.

## <a name="find-a-specific-service"></a>특정 서비스 찾기
 메서드를 사용하여 <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> 특정 서비스가 설치되어 있는지 여부를 확인할 수도 있습니다. 서비스 클래스의 형식을 알고 있어야 합니다.

1. 이전 절차에서 만든 프로젝트의 MenuItemCallback에서 `Services` 서비스의 GUID로 이름이 지정된 하위 컬렉션이 있는 컬렉션에 대한 구성 설정 저장소를 검색합니다. 이 경우 도움말 서비스를 찾습니다.

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

3. 실험적 인스턴스의 **도구** 메뉴에서 **FindServices 호출명령을** 클릭합니다.

     **도움말 서비스 사용 가능:** 뒤에 **True** 또는 **False라는** 텍스트가 있는 메시지가 표시됩니다. 이 설정을 확인하려면 이전 단계와 같이 레지스트리 편집기를 사용할 수 있습니다.
