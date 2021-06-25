---
title: 설정 저장소 | 사용 Microsoft Docs
description: 읽기 전용 Visual Studio 및 VSPackage 설정인 구성 설정 저장소에서 데이터를 읽는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d7fff5bc3eeeb3b4515e2e47027f5b88fb7807d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898385"
---
# <a name="using-the-settings-store"></a>설정 저장소 사용
설정 저장소에는 두 가지 종류가 있습니다.

- 구성 설정- 읽기 전용 Visual Studio 및 VSPackage 설정입니다. Visual Studio 알려진 모든 .pkgdef 파일의 설정을 이 저장소에 병합합니다.

- 사용자 설정 - **옵션** 대화 상자, 속성 페이지 및 기타 특정 대화 상자의 페이지에 표시되는 설정과 같은 쓰기 가능한 설정입니다. Visual Studio 확장은 소량의 데이터를 로컬 스토리지에 사용할 수 있습니다.

  이 연습에서는 구성 설정 저장소에서 데이터를 읽는 방법을 보여 줍니다. [사용자 설정 저장소에 쓰는](../extensibility/writing-to-the-user-settings-store.md) 방법에 대한 설명은 사용자 설정 저장소에 쓰기를 참조하세요.

## <a name="creating-the-example-project"></a>예제 프로젝트 만들기
 이 섹션에서는 데모용 메뉴 명령을 사용하여 간단한 확장 프로젝트를 만드는 방법을 보여줍니다.

1. 모든 Visual Studio 확장은 확장 자산을 포함하는 VSIX 배포 프로젝트로 시작합니다. 라는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX 프로젝트를 `SettingsStoreExtension` 만듭니다. VSIX 프로젝트 템플릿은 **Visual C# /확장성** **아래의 새 프로젝트** 대화 상자에서 찾을 수 있습니다.

2. 이제 **SettingsStoreCommand라는** 사용자 지정 명령 항목 템플릿을 추가합니다. 새 **항목 추가** 대화 상자에서 **Visual C# /확장성으로** 이동하여 **사용자 지정 명령을** 선택합니다. 창 아래쪽의 **이름** 필드에서 명령 파일 이름을 **SettingsStoreCommand.cs 로 변경합니다.** 사용자 지정 명령을 만드는 방법에 대한 자세한 내용은 메뉴 명령을 [사용하여 확장 만들기를 참조하세요.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>구성 설정 저장소 사용
 이 섹션에서는 구성 설정을 검색하고 표시하는 방법을 보여 줍니다.

1. SettingsStorageCommand.cs 파일에서 다음 using 지시문을 추가합니다.

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. 에서 `MenuItemCallback` 메서드의 본문을 제거하고 다음 줄을 추가하면 구성 설정 저장소가 표시됩니다.

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>는 서비스에 대한 관리되는 도우미 클래스입니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>

3. 이제 Windows Phone 도구가 설치되어 있는지 확인합니다. 코드는 다음과 유사합니다.

   ```
   private void MenuItemCallback(object sender, EventArgs e)
   {
       SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
       SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
       bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");
       string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;
       MessageBox.Show(message);
   }
   ```

4. 코드를 테스트합니다. 프로젝트를 빌드하고 디버깅을 시작합니다.

5. 실험적 인스턴스의 **도구** 메뉴에서 **설정 호출스토어명령을** 클릭합니다.

    **Microsoft Windows Phone 개발자 도구:** **True** 또는 **False라는** 메시지 상자가 표시됩니다.

   Visual Studio 설정 저장소를 시스템 레지스트리에 유지합니다.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>레지스트리 편집기를 사용하여 구성 설정을 확인하려면

1. Regedit.exe 엽니다.

2. HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\ 으로 이동합니다.

    > [!NOTE]
    > \14.0_Config 아닌 \14.0Exp_Config\가 포함된 키를 보고 있는지 \\ 확인합니다. Visual Studio 실험적 인스턴스를 실행하면 구성 설정이 레지스트리 하이브 "14.0Exp_Config"에 있습니다.

3. \Installed Products\ 노드를 확장합니다. 이전 단계의 메시지가 **Microsoft Windows Phone 개발자 도구 설치: True** 이면 \Installed Products\에 Microsoft Windows Phone 개발자 도구 노드가 포함되어야 합니다. 메시지가 Microsoft **Windows Phone 개발자 도구 설치: False** 이면 \Installed Products\에 Microsoft Windows Phone 개발자 도구 노드가 포함되지 않아야 합니다.
