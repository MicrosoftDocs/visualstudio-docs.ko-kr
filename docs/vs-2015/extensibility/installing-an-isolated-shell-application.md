---
title: 격리 셸 응용 프로그램 설치 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0adc81cfe9ea4462940c31a02c6429be89709565
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75944256"
---
# <a name="installing-an-isolated-shell-application"></a>격리 셸 애플리케이션 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

셸 앱을 설치 하려면 다음 단계를 수행 해야 합니다.  
  
- 솔루션을 준비 합니다.  
  
- 응용 프로그램에 대 한 Windows Installer (MSI) 패키지를 만듭니다.  
  
- 설치 부트스트래퍼를 만듭니다.  
  
  이 문서의 모든 예제 코드는 MSDN 웹 사이트의 코드 갤러리에서 다운로드할 수 있는 [셸 배포 샘플](https://code.msdn.microsoft.com/Sample-setup-program-for-81ca73f7)에서 제공 됩니다. 이 샘플에서는 이러한 각 단계를 수행한 결과를 보여 줍니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 항목에서 설명 하는 절차를 수행 하려면 컴퓨터에 다음 도구가 설치 되어 있어야 합니다.  
  
- Visual Studio SDK  
  
- [WINDOWS INSTALLER XML 도구 집합](https://documentation.help/WiX-Toolset/index.html/) 버전 3.6  
  
  이 샘플에는 모든 셸에서 필요로 하지 않는 Microsoft 시각화 및 모델링 SDK도 필요 합니다.  
  
## <a name="preparing-your-solution"></a>솔루션 준비  
 기본적으로 셸 템플릿은 VSIX 패키지에 빌드 되지만이 동작은 주로 디버깅을 위해 사용 됩니다. 셸 응용 프로그램을 배포 하는 경우 MSI 패키지를 사용 하 여 레지스트리 액세스를 허용 하 고 설치 중에 다시 시작 해야 합니다. MSI 배포용 응용 프로그램을 준비 하려면 다음 단계를 수행 합니다.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>MSI 배포용 셸 응용 프로그램을 준비 하려면  
  
1. 솔루션에서 각. source.extension.vsixmanifest 파일을 편집 합니다.  
  
     요소에서 `Identifier` `InstalledByMSI` 요소와 `SystemComponent` 요소를 추가 하 고 해당 값을로 설정 `true` 합니다.  
  
     이러한 요소를 통해 VSIX 설치 관리자는 **확장 및 업데이트** 대화 상자를 사용 하 여 구성 요소를 설치 하지 않으며 사용자가 구성 요소를 제거할 수 없습니다.  
  
2. VSIX 매니페스트가 포함 된 각 프로젝트에 대해 빌드 작업을 편집 하 여 MSI를 설치할 위치에 콘텐츠를 출력 합니다. Vsix 매니페스트를 빌드 출력에 포함 하지만 .vsix 파일을 빌드하지는 않습니다.  
  
## <a name="creating-an-msi-for-your-shell"></a>셸에 대 한 MSI 만들기  
 MSI 패키지를 빌드하려면 표준 설치 프로젝트 보다 유연성을 향상 시킬 수 있으므로 [WINDOWS INSTALLER XML 도구 집합](https://documentation.help/WiX-Toolset/index.html) 을 사용 하는 것이 좋습니다.  
  
 제품. wxs 파일에서 검색 블록과 셸 구성 요소의 레이아웃을 설정 합니다.  
  
 그런 다음 솔루션에 대 한 .reg 파일 및 ApplicationRegistry에서 레지스트리 항목을 만듭니다.  
  
### <a name="detection-blocks"></a>검색 블록  
 검색 블록은 `Property` 검색할 필수 구성 요소를 지정 하는 요소 및 `Condition` 필수 구성 요소가 컴퓨터에 없는 경우 반환할 메시지를 지정 하는 요소로 구성 됩니다. 예를 들어 셸 응용 프로그램에는 Microsoft Visual Studio Shell 재배포 가능가 필요 하 고, 검색 블록은 다음과 같이 표시 됩니다.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>셸 구성 요소의 레이아웃  
 대상 디렉터리 구조와 설치할 구성 요소를 식별 하는 요소를 추가 해야 합니다.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>셸 구성 요소의 레이아웃을 설정 하려면  
  
1. `Directory`다음 예제가 보여 주는 것 처럼 대상 컴퓨터의 파일 시스템에서 만들 모든 디렉터리를 나타내는 요소 계층 구조를 만듭니다.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     이러한 디렉터리는 `Id` 설치 해야 하는 파일이 지정 된 경우에 의해 참조 됩니다.  
  
2. 다음 예제와 같이 Shell 응용 프로그램에 필요한 구성 요소를 확인 합니다.  
  
    > [!NOTE]
    > 일부 요소는 다른. wxs 파일의 정의를 참조할 수 있습니다.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1. `ComponentRef`요소는 현재 구성 요소에 필요한 파일을 식별 하는 다른. wxs 파일을 참조 합니다. 예를 들어 일반 프로필에 대 한 도움말에는 다음 정의가 있습니다. wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         `DirectoryRef`요소는 이러한 파일이 사용자의 컴퓨터에서 이동 하는 위치를 지정 합니다. `Directory`요소는 하위 디렉터리에 설치 되도록 지정 하 고 각 `File` 요소는 솔루션의 일부로 존재 하는 파일을 나타내며 MSI 파일을 만들 때 해당 파일을 찾을 수 있는 위치를 식별 합니다.  
  
    2. `ComponentGroupRef`요소는 다른 구성 요소 (또는 구성 요소 및 구성 요소 그룹) 그룹을 참조 합니다. 예를 들어 `ComponentGroupRef` ApplicationGroup은 application. wxs에서 다음과 같이 정의 됩니다.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    > Shell (격리) 응용 프로그램에 필요한 종속성은 DebuggerProxy, MasterPkgDef, Resources (특히. winprf 파일), 응용 프로그램 및 PkgDefs입니다.  
  
### <a name="registry-entries"></a>레지스트리 항목  
 Shell (격리) 프로젝트 템플릿에는 설치 시 병합할 레지스트리 키에 대 한 *ProjectName*.reg 파일이 포함 되어 있습니다. 이러한 레지스트리 항목은 설치 및 정리를 위해 MSI의 일부 여야 합니다. 또한 ApplicationRegistry에서 일치 하는 레지스트리 블록을 만들어야 합니다.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>MSI에 레지스트리 항목을 통합 하려면  
  
1. **Shell 사용자 지정** 폴더에서 *ProjectName*.reg를 엽니다.  
  
2. $RootFolder $ token의 모든 인스턴스를 대상 설치 디렉터리의 경로로 바꿉니다.  
  
3. 응용 프로그램에 필요한 다른 레지스트리 항목을 추가 합니다.  
  
4. ApplicationRegistry를 엽니다.  
  
5. 다음 예제와 같이 *ProjectName*.reg의 각 레지스트리 항목에 대해 해당 하는 레지스트리 블록을 추가 합니다.  
  
    |*ProjectName*.reg|ApplicationRegisty|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT \CLSID \\ {bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @ = "사진 스튜디오 DTE 개체"|\<RegistryKey Id='DteClsidRegKey' Root='HKCR' Key='$(var.DteClsidRegKey)' Action='createAndRemoveOnUninstall'><br /><br /> \<RegistryValue Type='string' Name='@' Value='$(var.ShortProductName) DTE Object' /><br /><br /> \</RegistryKey>|  
    |[HKEY_CLASSES_ROOT \CLSID \\ {bb431796-a179-4df7-b65d-c0df6bda7cc6} \LocalServer32]<br /><br /> @ = "$RootFolder $\PhotoStudio.exe"|\<RegistryKey Id='DteLocSrv32RegKey' Root='HKCR' Key='$(var.DteClsidRegKey)\LocalServer32' Action='createAndRemoveOnUninstall'><br /><br /> \<RegistryValue Type='string' Name='@' Value='[INSTALLDIR]$(var.ShortProductName).exe' /><br /><br /> \</RegistryKey>|  
  
     이 예에서 DteClsidRegKey는 맨 위 행의 레지스트리 키로 확인 됩니다. ShortProductName은로 확인 됩니다 `PhotoStudio` .  
  
## <a name="creating-a-setup-bootstrapper"></a>설치 부트스트래퍼 만들기  
 모든 필수 구성 요소가 먼저 설치 된 경우에만 완료 된 MSI를 설치 합니다. 최종 사용자 환경을 용이 하 게 하기 위해 응용 프로그램을 설치 하기 전에 모든 필수 구성 요소를 수집 하 고 설치 하는 설치 프로그램을 만듭니다. 설치를 성공적으로 수행 하려면 다음 작업을 수행 합니다.  
  
- 관리자가 설치를 적용 합니다.  
  
- Visual Studio Shell (격리)이 설치 되어 있는지 여부를 검색 합니다.  
  
- 셸 설치 관리자 중 하나 또는 둘 다를 순서 대로 실행 합니다.  
  
- 다시 시작 요청을 처리 합니다.  
  
- MSI를 실행 합니다.  
  
### <a name="enforcing-installation-by-administrator"></a>관리자에의 한 설치 적용  
 이 절차는 설치 프로그램에서 파일 (예: 파일 \ 파일)과 같은 필수 디렉터리에 액세스할 수 있도록 하는 데 필요 \\ 합니다.  
  
##### <a name="to-enforce-installation-by-administrator"></a>관리자가 설치를 적용 하려면  
  
1. 설치 프로젝트에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.  
  
2. **구성 속성/링커/매니페스트 파일**아래에서 **UAC 실행 수준을** **requireAdministrator**로 설정 합니다.  
  
     이 속성은 프로그램을 관리자 권한으로 포함 된 매니페스트 파일에 실행 해야 하는 특성을 배치 합니다.  
  
### <a name="detecting-shell-installations"></a>셸 설치 검색  
 Visual Studio Shell (격리)을 설치 해야 하는지 여부를 확인 하려면 먼저 HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.의 레지스트리 값을 확인 하 여 이미 설치 되어 있는지 확인 합니다.  
  
> [!NOTE]
> 이러한 값은 wxs의 셸 검색 블록 에서도 읽을 수 있습니다.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder는 Visual Studio 셸이 설치 된 위치를 지정 하 고 해당 위치에서 파일을 확인할 수 있습니다.  
  
 셸 설치를 검색 하는 방법에 대 한 예제는 `GetProductDirFromReg` Shell Deployment 샘플에서 Utilities 함수를 참조 하세요.  
  
 패키지에 필요한 Visual Studio 셸 중 하나 이상이 컴퓨터에 설치 되어 있지 않은 경우 설치할 구성 요소 목록에 추가 해야 합니다. 예제는 `ComponentsPage::OnInitDialog` Shell Deployment 샘플에서 ComponentsPage의 함수를 참조 하세요.  
  
### <a name="running-the-shell-installers"></a>셸 설치 관리자 실행  
 셸 설치 관리자를 실행 하려면 올바른 명령줄 인수를 사용 하 여 Visual Studio Shell 재배포 가능 패키지를 호출 합니다. 최소한 다음에 수행 해야 할 작업을 결정 하려면 명령줄 인수 **/norestart/q** 를 사용 하 고 반환 코드를 감시 해야 합니다. 다음 예에서는 Shell (격리) 재배포 가능 패키지를 실행 합니다.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Shell 언어 팩 설치 관리자 실행  
 셸 또는 셸이 설치 되어 있고 언어 팩만 필요한 것으로 확인 된 경우 다음 예제와 같이 언어 팩을 설치할 수 있습니다.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>이름을 해독 반환 값  
 일부 운영 체제에서는 Visual Studio Shell (격리) 설치를 다시 시작 해야 합니다. 이 상태는에 대 한 호출의 반환 코드에 의해 결정 될 수 있습니다 `ExecCmd` .  
  
|반환 값|설명|  
|------------------|-----------------|  
|ERROR_SUCCESS|설치가 완료 되었습니다. 이제 응용 프로그램을 설치할 수 있습니다.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|설치가 완료 되었습니다. 컴퓨터를 다시 시작한 후에 응용 프로그램을 설치할 수 있습니다.|  
|3015|설치가 진행 중입니다. 설치를 계속 하려면 컴퓨터를 다시 시작 해야 합니다.|  
  
### <a name="handling-restarts"></a>다시 시작 처리  
 **/Norestart** 인수를 사용 하 여 셸 설치 관리자를 실행 하는 경우 컴퓨터를 다시 시작 하거나 컴퓨터를 다시 시작 하지 않도록 지정 했습니다. 그러나 다시 시작 해야 하는 경우에는 컴퓨터를 다시 시작한 후 설치 관리자가 계속 작동 하는지 확인 해야 합니다.  
  
 다시 시작을 올바르게 처리 하려면 설치 프로그램을 다시 시작으로 설정 하 고 다시 시작 프로세스가 올바르게 처리 되도록 설정 해야 합니다.  
  
 ERROR_SUCCESS_REBOOT_REQUIRED 또는 3015이 반환 되는 경우 설치를 계속 하기 전에 코드에서 컴퓨터를 다시 시작 해야 합니다.  
  
 다시 시작을 처리 하려면 다음 작업을 수행 합니다.  
  
- Windows가 시작 될 때 설치를 다시 시작 하도록 레지스트리를 설정 합니다.  
  
- 부트스트래퍼를 두 번 다시 시작 합니다.  
  
- Shell installer ResumeData 키를 삭제 합니다.  
  
- Windows를 다시 시작 합니다.  
  
- MSI의 시작 경로를 다시 설정 합니다.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Windows를 시작할 때 설치를 다시 시작 하도록 레지스트리 설정  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ 레지스트리 키는 관리자 권한으로 시스템 시작 시 실행 된 후 삭제 됩니다. HKEY_CURRENT_USER는 유사한 키를 포함 하지만 일반 사용자로 실행 되며 설치에 적합 하지 않습니다. 설치 관리자를 호출 하는 RunOnce 키에 문자열 값을 추가 하 여 설치를 다시 시작할 수 있습니다. 그러나 **/restart** 또는 유사한 매개 변수를 사용 하 여 설치 관리자를 호출 하 여 응용 프로그램을 시작 하는 대신 다시 시작 하 고 있음을 알리는 것이 좋습니다. 설치 프로세스의 위치를 나타내는 매개 변수를 포함할 수도 있습니다 .이는 여러 번 다시 시작 해야 할 수 있는 설치에서 특히 유용 합니다.  
  
 다음 예에서는 설치를 다시 시작 하기 위한 RunOnce 레지스트리 키 값을 보여 줍니다.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>부트스트래퍼의 두 번 다시 시작 설치  
 RunOnce에서 직접 설치를 사용 하는 경우에는 데스크톱을 완전히 로드할 수 없습니다. 전체 사용자 인터페이스를 사용할 수 있도록 하려면 설치 프로그램의 다른 실행을 만들고 RunOnce 인스턴스를 종료 해야 합니다.  
  
 올바른 사용 권한을 얻을 수 있도록 설치 프로그램을 다시 실행 해야 하 고, 다음 예제와 같이 다시 시작 하기 전에 중지 한 위치를 알 수 있도록 충분 한 정보를 제공 해야 합니다.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Shell Installer ResumeData 키를 삭제 하는 중  
 셸 설치 관리자는 다시 시작한 후 설치를 다시 시작 하기 위해 데이터를 사용 하 여 HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData 레지스트리 키를 설정 합니다. 셸 설치 관리자가 아닌 응용 프로그램이 다시 시작 되므로 다음 예제와 같이 해당 레지스트리 키를 삭제 합니다.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Windows 다시 시작  
 필요한 레지스트리 키를 설정한 후에는 Windows를 다시 시작할 수 있습니다. 다음 예에서는 다양 한 Windows 운영 체제에 대 한 다시 시작 명령을 호출 합니다.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>MSI의 시작 경로를 다시 설정 하는 중  
 다시 시작 하기 전에 현재 디렉터리는 설치 프로그램의 위치 이지만 다시 시작한 후 위치는 system32 디렉터리가 됩니다. 다음 예제에 나와 있는 것 처럼 설치 프로그램은 각 MSI 호출 전에 현재 디렉터리를 다시 설정 해야 합니다.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>응용 프로그램 MSI 실행  
 Visual Studio Shell 설치 관리자가 ERROR_SUCCESS를 반환한 후 응용 프로그램에 대해 MSI를 실행할 수 있습니다. 설치 프로그램에서 사용자 인터페이스를 제공 하기 때문에 다음 예제에 나와 있는 것 처럼 자동 모드 (**/q**) 및 로깅 (**/L**)으로 MSI를 시작 합니다.  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>관련 항목  
 [연습: 기본 격리 셸 애플리케이션 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
