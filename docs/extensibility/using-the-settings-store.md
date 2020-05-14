---
title: 설정 저장소 사용 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3bbc09586f883e067e32f525a0331c1a9e253f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698513"
---
# <a name="using-the-settings-store"></a>설정 저장소 사용
설정 저장소에는 두 가지 종류가 있습니다.

- 읽기 전용 Visual Studio 및 VSPackage 설정인 구성 설정입니다. Visual Studio는 알려진 모든 .pkgdef 파일의 설정을 이 저장소에 병합합니다.

- **옵션** 대화 상자, 속성 페이지 및 기타 특정 대화 상자의 페이지에 표시되는 설정과 같은 쓰기 가능한 설정입니다. Visual Studio 확장은 소량의 데이터를 로컬로 저장하는 데 사용할 수 있습니다.

  이 연습에서는 구성 설정 저장소에서 데이터를 읽는 방법을 보여 주며 이 연습입니다. [사용자 설정 저장소에 쓰는](../extensibility/writing-to-the-user-settings-store.md) 방법에 대한 설명은 사용자 설정 저장소에 쓰기를 참조하십시오.

## <a name="creating-the-example-project"></a>예제 프로젝트 만들기
 이 섹션에서는 데모를 위한 메뉴 명령을 사용하여 간단한 확장 프로젝트를 만드는 방법을 보여 줍니다.

1. 모든 Visual Studio 확장은 확장 자산을 포함하는 VSIX 배포 프로젝트로 시작합니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 라는 VSIX 프로젝트를 `SettingsStoreExtension`만듭니다. **시각적 C# / 확장성**에서 **새 프로젝트** 대화 상자에서 VSIX 프로젝트 템플릿을 찾을 수 있습니다.

2. 이제 **SettingsStoreCommand이라는**사용자 지정 명령 항목 템플릿을 추가합니다. 새 **항목 추가** 대화 상자에서 **시각적 C# / 확장성으로** 이동하여 **사용자 지정 명령을 선택합니다.** 창 아래쪽의 **이름** 필드에서 명령 파일 이름을 **SettingsStoreCommand.cs.** 사용자 지정 명령을 만드는 방법에 대한 자세한 내용은 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md) 참조하십시오.

## <a name="using-the-configuration-settings-store"></a>구성 설정 저장소 사용
 이 섹션에서는 구성 설정을 검색하고 표시하는 방법을 보여 주었습니다.

1. SettingsStorageCommand.cs 파일에서 지시문을 사용하여 다음을 추가합니다.

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. 에서 `MenuItemCallback`메서드의 본문을 제거하고 이러한 줄을 추가하면 구성 설정 저장소가 표시됩니다.

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    는 <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> 서비스를 통해 관리되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> 도우미 클래스입니다.

3. 이제 Windows Phone 도구가 설치되어 있는지 확인합니다. 코드는 다음과 같아야 합니다.

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

5. 실험인스턴스에서 **도구** 메뉴에서 설정 **스토어명령 호출을**클릭합니다.

    당신은 **마이크로 소프트 윈도우 폰 개발자 도구를** 말하는 메시지 상자를 볼 수 있습니다 : **참** 또는 **거짓**뒤에 .

   Visual Studio는 시스템 레지스트리에 설정 저장소를 유지합니다.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>레지스트리 편집기를 사용하여 구성 설정을 확인하려면

1. Regedit.exe를 엽니다.

2. HKEY_CURRENT_USER\소프트웨어\Microsoft\VisualStudio\14.0Exp_Config설치제품.\\

    > [!NOTE]
    > \14.0Exp_Config\가 아닌 \14.0_Config\\포함된 키를 보고 있는지 확인합니다. Visual Studio의 실험 인스턴스를 실행하면 구성 설정이 레지스트리 하이브 "14.0Exp_Config"에 있습니다.

3. \설치된 제품\ 노드를 확장합니다. 이전 단계의 메시지가 **마이크로 소프트 윈도우 폰 개발자 도구 설치**인 경우 : True , 설치된 제품 \은 마이크로 소프트 윈도우 폰 개발자 도구 노드를 포함해야합니다. 메시지가 마이크로 **소프트 윈도우 폰 개발자 도구 설치 인**경우 : 거짓 , 다음 \설치 제품 \ 마이크로 소프트 윈도우 폰 개발자 도구 노드를 포함하지 않아야합니다.
