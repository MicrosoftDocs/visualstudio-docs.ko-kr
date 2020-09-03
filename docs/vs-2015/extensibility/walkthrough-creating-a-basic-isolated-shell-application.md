---
title: '연습: 기본 격리 셸 응용 프로그램 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6192eb5583e7d0bc37518e995aacccad643cc9ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850345"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>연습: 기본 격리 셸 애플리케이션 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 격리 된 셸 솔루션을 만들고, 도구 창에 대 한 도움말을 사용자 지정 하 고, 격리 된 셸을 설치 하는 설치 프로그램을 만드는 방법을 보여 줍니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요. 격리 된 셸을 배포 하려면 Visual Studio Shell (격리) 재배포 가능 패키지도 사용 해야 합니다.  
  
## <a name="creating-an-isolated-shell-solution"></a>격리 셸 솔루션 만들기  
 이 섹션에서는 Visual Studio Shell 격리 프로젝트 템플릿을 사용 하 여 격리 된 셸 솔루션을 만드는 방법을 보여 줍니다. 솔루션에는 다음 프로젝트가 포함 되어 있습니다.  
  
- *SolutionName*입니다. AboutBoxPackage 프로젝트를 사용 하 여 도움말/정보 상자의 모양을 사용자 지정할 수 있습니다.  
  
- ShellExtensionsVSIX 프로젝트-격리 셸 응용 프로그램의 다양 한 구성 요소를 정의 하는 source.extension.vsixmanifest 파일이 포함 되어 있습니다.  
  
- *SolutionName* 프로젝트는 격리 셸 응용 프로그램을 호출 하는 실행 파일을 생성 합니다. 이 프로젝트에는 격리 된 셸 응용 프로그램의 모양과 동작을 customiz 수 있는 셸 사용자 지정 폴더가 포함 되어 있습니다.  
  
- *SolutionName* UI 프로젝트는 활성 메뉴 명령과 지역화 가능한 문자열을 정의 하는 위성 어셈블리를 생성 합니다.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>기본 격리 셸 솔루션을 만들려면  
  
1. Visual Studio를 연 다음 새 프로젝트를 만듭니다.  
  
2. **새 프로젝트** 창에서 **기타 프로젝트 형식** , **확장성**을 차례로 확장 합니다. **Visual Studio Shell 격리** 프로젝트 템플릿을 선택 합니다.  
  
3. 프로젝트 이름을 `MyVSShellStub` 지정 하 고 위치를 지정 합니다. **솔루션용 디렉터리 만들기** 가 선택 되어 있는지 확인 한 다음 **확인**을 클릭 합니다.  
  
     새 솔루션이 **솔루션 탐색기**에 나타납니다.  
  
4. 솔루션을 빌드하고 격리 된 셸 응용 프로그램의 디버깅을 시작 합니다.  
  
     Visual Studio 격리 셸이 나타납니다. 제목 표시줄은 **Myvsshellstub**을 읽습니다. 제목 표시줄 아이콘은 \MyVSShellStub\Resource Files\ApplicationIcon.ico.에서 생성 됩니다.  
  
## <a name="customizing-the-application-name-and-icon"></a>응용 프로그램 이름 및 아이콘 사용자 지정  
 제목 표시줄에 회사의 이름과 로고를 사용 하 여 응용 프로그램의 브랜드를 지정할 수 있습니다. 다음 단계에서는 패키지 정의 파일 MyVSShellStub을 변경 하 여 사용자 지정 응용 프로그램 제목 표시줄에 표시 되는 이름 및 아이콘을 변경 하는 방법을 보여 줍니다.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>응용 프로그램 이름 및 아이콘을 사용자 지정 하려면  
  
1. MyVSShellStub 프로젝트에서 \Shell Customization\MyVSShellStub.Application.pkgdef.을 엽니다.  
  
2. `AppName`요소 값을 **"AppName" = "Fabrikam Music Editor"** 로 변경 합니다.  
  
3. 응용 프로그램 아이콘을 변경 하려면 다른 아이콘을 \MyVSShellStub\MyVSShellStub\MyVSShellStub\ 디렉터리에 복사 합니다. 기존 ApplicationIcon .ico 파일의 이름을 ApplicationIcon1로 바꿉니다. 새 파일의 이름을 ApplicationIcon .ico로 바꿉니다.  
  
4. 솔루션을 빌드하고 디버깅을 시작합니다. 격리 된 셸 IDE가 나타납니다. 제목 표시줄에는 **Fabrikam 음악 편집기**라는 단어 옆에 새 아이콘이 표시 됩니다.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>기본 웹 브라우저 홈 페이지 사용자 지정  
 이 섹션에서는 패키지 정의 파일을 변경 하 여 **웹 브라우저** 창의 기본 홈 페이지를 변경 하는 방법을 보여 줍니다.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>기본 웹 브라우저 홈 페이지를 사용자 지정 하려면  
  
1. MyVSShellStub 파일에서 `DefaultHomePage` 요소 값을 ""로 변경 <https://www.microsoft.com> 합니다.  
  
2. MyVSShellStub 프로젝트를 다시 빌드합니다.  
  
3. 솔루션을 빌드하고 디버깅을 시작합니다.  
  
4. **보기/기타 창**에서 **웹 브라우저**를 클릭 합니다. **웹 브라우저** 창에 Microsoft Corporation 홈 페이지가 표시 됩니다.  
  
## <a name="removing-the-print-command"></a>인쇄 명령 제거  
 격리 된 셸 UI 프로젝트의. vsct 파일은 form 요소의 선언 집합으로 구성 됩니다. `<Define name=No_` *Element* `>` 여기서 *요소* 는 표준 Visual Studio 메뉴 및 명령 중 하나입니다.  
  
 선언이 주석 처리가 제거 인 경우 해당 메뉴 또는 명령은 격리 된 셸에서 제외 됩니다. 반대로, 선언이 주석 처리 된 경우 메뉴 또는 명령이 격리 된 셸에 포함 됩니다.  
  
 다음 단계에서는. vsct 파일에서 인쇄 명령의 주석 처리를 제거 합니다.  
  
#### <a name="to-remove-the-print-command"></a>인쇄 명령을 제거 하려면  
  
1. 격리 된 셸 응용 프로그램의 **파일** 메뉴에 **인쇄** 명령이 표시 되는지 확인 합니다.  
  
2. MyVSShellStubUI 프로젝트에서 \Resource Files\MyVSShellStubUI.vsct를 편집용으로 엽니다.  
  
3. 이 줄의 주석 처리를 제거 합니다.  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4. 그러면 인쇄 명령이 제거 됩니다.  
  
5. 격리 된 셸 응용 프로그램 디버깅을 시작 합니다. **파일/인쇄** 명령이 사라졌는지 확인 합니다.  
  
## <a name="removing-features-from-the-isolated-shell"></a>격리 된 셸에서 기능 제거  
 사용자 지정 격리 셸 응용 프로그램에서 해당 기능을 사용 하지 않으려는 경우 .pkgundef 파일을 편집 하 여 Visual Studio를 사용 하 여 로드 된 패키지 중 일부를 제거할 수 있습니다. $RootKey $ \Packages 레지스트리 키의 하위 키 중 하나에 패키지를 지정 합니다.  
  
> [!NOTE]
> Visual Studio 기능의 Guid를 찾으려면 [Visual Studio 기능의 패키지 guid](../extensibility/package-guids-of-visual-studio-features.md)를 참조 하세요.  
  
 다음 절차에서는 격리 된 셸에서 XML 편집기를 제거 하는 방법을 보여 줍니다.  
  
#### <a name="to-remove-the-xml-editor"></a>XML 편집기를 제거 하려면  
  
1. MyVSShellStub 프로젝트의 셸 사용자 지정 폴더에서 .pkgundef 파일을 엽니다.  
  
2. 다음 줄의 주석 처리를 제거 합니다.  
  
     [$RootKey $ \Packages \\ {87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3. 솔루션을 다시 빌드하고 격리 된 셸 디버깅을 시작 합니다. XML 파일 (예: \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct.)을 엽니다. 파일의 XML 키워드에 색이 지정 되지 않고 줄에 "<"을 입력 해도 XML 도구 설명이 표시 되지 않는지 확인 합니다.  
  
## <a name="customizing-the-helpabout-box"></a>도움말/정보 상자 사용자 지정  
 격리 된 셸 프로젝트 템플릿의 일부로 생성 되는 도움말/정보 상자를 사용자 지정할 수 있습니다.  
  
#### <a name="to-customize-the-company-name"></a>회사 이름을 사용자 지정 하려면  
  
1. 회사 이름, 저작권 정보, 제품 버전 및 제품 설명은 \Properties\AssemblyInfo.cs 파일의 MyVSShellStub 프로젝트에 있습니다. 이 파일을 엽니다.  
  
2. 값을 `AssemblyCompany` **fabrikam**, `AssemblyProduct` 및 값을 fabrikam `AssemblyTitle` **음악 편집기**로, `AssemblyCopyright` 값을 **저작권 © fabrikam 2015**으로 변경 합니다.  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3. 제품에 대 한 설명을 추가 하려면 `AssemblyDescription` 값을 **Fabrikam Music editor의 설명으로 변경 합니다.**  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4. 디버깅을 시작 하 고 격리 된 셸 응용 프로그램에서 **도움말/정보** 상자를 엽니다. 변경 된 문자열이 표시 되어야 합니다. 도움말/정보 상자의 제목은 `AssemblyTitle` AssemblyInfo.cs의 값과 동일 합니다.  
  
5. **도움말/정보** 상자 자체의 속성은 MyVSShellStub 파일에 있습니다. 도움말/정보 상자의 너비를 변경 하려면 블록으로 이동 하 여 `AboutDialogStyle` `Width` 속성을 200으로 설정 합니다.  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6. 솔루션을 다시 빌드하고 격리 된 셸 디버깅을 시작 합니다. 도움말/정보 상자는 대략 사각형 이어야 합니다.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>격리 된 셸 응용 프로그램을 배포 하기 전에  
 격리 된 셸 응용 프로그램은 Visual Studio Shell (격리) 재배포 가능 패키지가 있는 모든 컴퓨터에 설치할 수 있습니다. 재배포 가능 패키지에 대 한 자세한 내용은 [Visual Studio 확장성 다운로드](https://msdn.microsoft.com/vstudio/bb984878.aspx) 웹 사이트를 참조 하세요.  
  
## <a name="deploying-the-isolated-shell-application"></a>격리 된 셸 응용 프로그램 배포  
 설치 프로젝트를 만들어 대상 컴퓨터에 격리 된 셸 응용 프로그램을 배포 합니다. 다음 항목을 지정 해야 합니다.  
  
- 대상 컴퓨터에 있는 폴더와 파일의 레이아웃입니다.  
  
- .NET Framework 및 Visual Studio shell 런타임이 대상 컴퓨터에 설치 되도록 보장 하는 시작 조건입니다.  
  
  다음 절차에서는 컴퓨터에 InstallShield Edition을 설치 해야 합니다.  
  
#### <a name="to-create-the-setup-project"></a>설치 프로젝트를 만들려면  
  
1. **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭 한 다음 **새 프로젝트 추가**를 클릭 합니다.  
  
2. **새 프로젝트** 대화 상자에서 **기타 프로젝트 형식** 을 확장 한 다음 **설치 및 배포**를 선택 합니다. InstallShield 템플릿을 선택 합니다. 새 프로젝트의 이름을 `MySetup` 지정한 다음 **확인을**클릭 합니다.  
  
3. InstallShield 제한 된 버전이 이미 설치 되어 있는 경우 다음 단계를 계속 합니다.  
  
    InstallShield 제한 된 버전이 아직 설치 되지 않은 경우 InstallShield 다운로드 페이지가 나타납니다. 지침에 따라 제품을 다운로드 하 여 설치 하 고, 해당 버전의 Visual Studio와 호환 되는 InstallShield 버전을 선택 합니다. InstallShield 설치를 등록 하거나 평가로 사용할지 여부를 결정 해야 합니다. 설치를 완료 한 후 Visual Studio를 다시 시작 해야 합니다.  
  
   > [!IMPORTANT]
   > InstallShield 프로젝트를 만들려면 먼저 Visual Studio를 관리자 권한으로 시작 해야 합니다. 이렇게 하지 않으면 프로젝트를 빌드할 때 오류가 발생 합니다.  
  
   다음 단계에서는 설치 프로젝트를 구성 하는 방법을 보여 줍니다.  
  
> [!IMPORTANT]
> 설치 프로젝트를 구성 하기 전에 격리 된 셸 프로젝트의 릴리스 구성을 한 번 이상 빌드 했는지 확인 합니다.  
  
#### <a name="to-configure-the-setup-project"></a>설치 프로젝트를 구성 하려면  
  
1. **솔루션 탐색기**의 **Mysetup.bat** 프로젝트에서 **프로젝트 도우미**를 선택 합니다. **프로젝트 도우미** 창의 맨 아래 행에서 **응용 프로그램 정보**를 선택 합니다. 회사 이름 및 **Fabrikam 음악 편집기** 로 **fabrikam** 을 응용 프로그램 이름으로 입력 합니다. **프로젝트 도우미**의 오른쪽 아래에 있는 앞으로 화살표를 선택 합니다.  
  
2. **응용 프로그램에서 컴퓨터에 소프트웨어를 설치 해야 합니까?** 에서 **예** 를 선택 하 고 **Microsoft .NET Framework 4.5 전체 패키지**를 선택 합니다.  
  
3. 창의 맨 아래에 있는 **응용 프로그램 파일** 단추를 선택 하 고 **Fabrikam 음악 편집기** 폴더가 선택 되어 있는지 확인 합니다.  
  
4. **파일 추가** 단추를 선택 합니다. **파일 추가** 대화 상자에서 **MyVSShellStub\Release** 폴더의 다음 파일을 추가 합니다.  
  
    1. MyVSShellStub.exe.config  
  
    2. DebuggerProxy.dll  
  
    3. DebuggerProxy.dll 매니페스트  
  
    4. MyVSShellStub  
  
    5. MyVSShellStub  
  
    6. MyVSShellStub. winprf  
  
    7. Splash.bmp  
  
5. **프로젝트 출력 추가** 단추를 클릭 하 고 **Myvsshellstub/기본 출력**을 추가 합니다. **확인**을 클릭합니다.  
  
6. 왼쪽 창의 **대상 컴퓨터**에서 **Fabrikam 음악 편집기 [INSTALLDIR]** 노드를 마우스 오른쪽 단추로 클릭 하 고 **확장명**이라는 **새 폴더** 를 추가 합니다.  
  
7. 왼쪽 창에서 **확장** 노드를 마우스 오른쪽 단추로 클릭 하 고 **응용 프로그램**이라는 새 폴더를 추가 합니다.  
  
8. **응용 프로그램** 폴더를 선택 하 고 **프로젝트 출력 추가** 단추를 클릭 한 다음 myvsshellstub 프로젝트에서 기본 출력을 선택 합니다.  
  
9. **파일 추가** 단추를 클릭 하 고 \MyVSShellStub\Release\Extensions\Application\ 폴더에서 다음 파일을 추가 합니다.  
  
    - MyVSShellStub. .pkgdef  
  
    - MyVSShellStub  
  
10. 왼쪽 창에서 **Fabrikam 음악 편집기 [INSTALLDIR]** 노드를 마우스 오른쪽 단추로 클릭 하 고 이름이 **1033**인 새 폴더를 추가 합니다.  
  
11. 1033 폴더를 선택 하 고 **프로젝트 출력 추가** 단추를 클릭 한 다음 MyVSShellStubUI 프로젝트에서 기본 출력을 선택 합니다.  
  
12. **응용 프로그램 바로 가기** 창으로 이동 합니다.  
  
13. **새로** 만들기를 클릭 하 여 바로 가기를 만들고 **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**을 선택 합니다.  
  
14. **설치 인터뷰** 창으로 이동 합니다.  
  
15. 모든 항목을 **아니요**로 설정 합니다.  
  
16. **솔루션 탐색기**의 mysetup.bat 프로젝트에서 **설치 요구 사항 및 작업 정의 \ 요구 사항 정의**를 엽니다. **요구 사항** 창이 열립니다.  
  
17. **시스템 소프트웨어 요구 사항** 을 마우스 오른쪽 단추로 클릭 하 고 **새 시작 조건 만들기**를 선택 합니다. **시스템 검색 마법사** 가 나타납니다.  
  
18. **찾으려는 항목** 을 선택 하십시오. 창의 드롭다운 목록에서 **레지스트리 항목** 을 선택 하 고 **다음**을 클릭 합니다.  
  
19. **어떻게 찾을 수 있나요?** 창에서 레지스트리 루트로 **HKEY_LOCAL_MACHINE** 를 선택 합니다. 64 비트 시스템의 경우 **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** 을 입력 하 고 32 비트 시스템에는 **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** 를 입력 하 고 **설치** 를 레지스트리 값으로 입력 합니다. **다음**을 클릭합니다.  
  
20. 값을 **선택** 하십시오. 창에서이 제품을 입력 하려면 **Visual Studio 2015 격리 셸 재배포 가능 패키지가 설치 되어 있어야 합니다.** 텍스트를 표시 하 고 **마침**을 클릭 합니다.  
  
21. 격리 셸 솔루션을 다시 빌드하여 설치 프로젝트를 만듭니다.  
  
     다음 폴더에서 setup.exe 파일을 찾을 수 있습니다.  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>설치 프로그램 테스트  
 설치를 테스트 하려면 setup.exe 파일을 다른 컴퓨터에 복사 하 고 설치 프로그램 실행 파일을 실행 합니다. 격리 된 셸 응용 프로그램을 실행할 수 있습니다.
