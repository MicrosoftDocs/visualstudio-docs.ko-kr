---
title: 설정 저장소 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b6c2810a81ada06152faea06e86a27f7907a643
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842147"
---
# <a name="using-the-settings-store"></a>설정 저장소 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

설정 저장소에는 다음과 같은 두 가지 종류가 있습니다.  
  
- 읽기 전용 Visual Studio 및 VSPackage 설정에 해당 하는 구성 설정입니다. Visual Studio는 알려진 모든 .pkgdef 파일의 설정을이 저장소로 병합 합니다.  
  
- **옵션** 대화 상자, 속성 페이지 및 기타 특정 대화 상자에서 페이지에 표시 되는 설정 등의 쓰기 가능한 설정 인 사용자 설정 Visual Studio 확장에서는 소량의 데이터를 로컬 저장소로 사용할 수 있습니다.  
  
  이 연습에서는 구성 설정 저장소에서 데이터를 읽는 방법을 보여 줍니다. 사용자 설정 저장소에 쓰는 방법에 대 한 설명은 [사용자 설정 저장소에 쓰기](../extensibility/writing-to-the-user-settings-store.md) 를 참조 하세요.  
  
## <a name="creating-the-example-project"></a>예제 프로젝트 만들기  
 이 섹션에서는 데모용 메뉴 명령을 사용 하 여 간단한 확장 프로젝트를 만드는 방법을 보여 줍니다.  
  
1. 모든 Visual Studio 확장은 확장 자산을 포함 하는 VSIX 배포 프로젝트로 시작 합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]이라는 VSIX 프로젝트를 만듭니다 `SettingsStoreExtension` . **새 프로젝트** 대화 상자의 **Visual c #/확장성**에서 VSIX 프로젝트 템플릿을 찾을 수 있습니다.  
  
2. 이제 **SettingsStoreCommand**이라는 사용자 지정 명령 항목 템플릿을 추가 합니다. **새 항목 추가** 대화 상자에서 **Visual c #/확장성** 으로 이동 하 고 **사용자 지정 명령**을 선택 합니다. 창 맨 아래에 있는 **이름** 필드에서 명령 파일 이름을 **SettingsStoreCommand.cs**로 변경 합니다. 사용자 지정 명령을 만드는 방법에 대 한 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md) 를 참조 하세요.  
  
## <a name="using-the-configuration-settings-store"></a>구성 설정 저장소 사용  
 이 섹션에서는 구성 설정을 검색 하 고 표시 하는 방법을 보여 줍니다.  
  
1. SettingsStorageCommand.cs 파일에서 다음 using 문을 추가 합니다.  
  
   ```  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Settings;  
   using Microsoft.VisualStudio.Shell.Settings;  
   using System.Windows.Forms;  
   ```  
  
2. 에서 `MenuItemCallback` 메서드의 본문을 제거 하 고 다음 줄을 추가 하 여 구성 설정 저장소를 가져옵니다.  
  
   ```  
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
   ```  
  
    는 <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> 서비스에 대 한 관리 되는 도우미 클래스입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> .  
  
3. 이제 Windows Phone 도구가 설치 되어 있는지 확인 합니다. 코드는 다음과 같습니다.  
  
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
  
4. 코드를 테스트 합니다. 프로젝트를 빌드하고 디버깅을 시작합니다.  
  
5. 실험적 인스턴스의 **도구** 메뉴에서 **SettingsStoreCommand 호출**을 클릭 합니다.  
  
    **Microsoft Windows Phone 개발자 도구:** 다음에 **True** 또는 **False**를 알려 주는 메시지 상자가 표시 됩니다.  
  
   Visual Studio는 설정 저장소를 시스템 레지스트리에 보관 합니다.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>레지스트리 편집기를 사용 하 여 구성 설정을 확인 하려면  
  
1. Regedit.exe를 엽니다.  
  
2. HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp_Config \InstalledProducts로 이동 \\ 합니다.  
  
    > [!NOTE]
    > \ 14를 포함 하는 키를 확인 하 고 있는지 확인 합니다. \ 14 \\ . 0_Config를 0Exp_Config 합니다. Visual Studio의 실험적 인스턴스를 실행 하는 경우 구성 설정은 레지스트리 hive "14.0Exp_Config"에 있습니다.  
  
3. \Installed Products \ node를 확장 합니다. 이전 단계의 메시지가 **microsoft Windows Phone 개발자 도구 설치**되어 있으면 True이 고, 그렇지 않으면 \ 설치 된 제품 \에 microsoft Windows Phone 개발자 도구 노드가 포함 되어 있어야 합니다. 메시지가 **microsoft Windows Phone 개발자 도구 설치**되어 있으면 False이 고, 그렇지 않으면 \ 설치 된 제품 \에 microsoft Windows Phone 개발자 도구 노드가 포함 되지 않아야 합니다.
