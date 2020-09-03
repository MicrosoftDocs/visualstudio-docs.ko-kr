---
title: Devenv 명령줄 스위치 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- builds [Team System], command-line
- applications [Visual Studio], executing
- compiling source code, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
- environment, Devenv commands
- compilers, Devenv commands
- switches
- Devenv, syntax and list of switches
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b8b0683024e2881f76bb6c54d9420d351fced08a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668723"
---
# <a name="devenv-command-line-switches"></a>Devenv 명령줄 스위치
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Devenv를 사용하면 IDE(통합 개발 환경)에 대한 다양한 옵션을 설정하고 명령줄에서 프로젝트를 빌드, 디버그 및 배포할 수도 있습니다. 이러한 스위치를 사용하여 스크립트 또는 .bat 파일(예: 야간 빌드 스크립트)에서 IDE를 실행하거나 특정 구성으로 IDE를 시작할 수 있습니다.

> [!NOTE]
> 빌드 관련 작업의 경우 devenv 대신 MSBuild를 사용하는 것이 좋습니다. 자세한 내용은 [명령줄 참조](../../msbuild/msbuild-command-line-reference.md)를 참조 하세요.

> [!NOTE]
> [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) 및 [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) 스위치를 사용하려면 관리자 권한으로 devenv를 실행해야 합니다.

## <a name="devenv-switch-syntax"></a>devenv 스위치 구문
 기본적으로 devenv 명령은 devenv.com 유틸리티에 스위치를 전달합니다.

 devenv.com 유틸리티는 `stdout`, `stderr` 등의 표준 시스템 스트림을 통해 출력을 전달하고 출력을 .txt 파일 등에 캡처하는 경우 적절한 I/O 리디렉션을 결정합니다. `devenv.exe`로 시작하는 명령은 동일한 스위치를 사용할 수 있지만 devenv.com 유틸리티를 무시하고 devenv.exe 프로그램으로 보냅니다.

 `devenv` 스위치의 구문 규칙은 다른 DOS 명령줄 유틸리티의 구문 규칙과 비슷합니다. 다음 구문 규칙은 모든 `devenv` 스위치 및 해당 인수에 적용됩니다.

- 명령이 `devenv`로 시작합니다.

- 스위치가 대/소문자를 구분하지 않습니다.

- 솔루션 또는 프로젝트를 지정하는 경우 첫 번째 인수는 파일 경로를 포함하여 솔루션 파일 또는 프로젝트 파일의 이름입니다.

- 첫 번째 인수가 솔루션 또는 프로젝트가 아닌 파일인 경우 해당 파일이 새 IDE 인스턴스의 적절한 편집기에서 열립니다.

- 솔루션 파일 이름 대신 프로젝트 파일 이름을 제공하는 경우 `devenv` 명령은 프로젝트 파일의 부모 폴더에서 이름이 같은 솔루션 파일을 검색합니다. 예를 들어 `devenv /build myproject1.vbproj` 명령은 부모 폴더에서 이름이 "myproject1.sln"인 솔루션 파일을 검색합니다.

    > [!NOTE]
    > 이 프로젝트를 참조하는 솔루션 파일 하나만 해당 부모 폴더에 있어야 합니다. 부모 폴더에 이 프로젝트를 참조하는 솔루션 파일이 없거나 두 개 이상 있는 경우 이 프로젝트를 따서 이름이 지정되고 참조하는 임시 솔루션 파일이 생성됩니다.

- 파일 경로 및 파일 이름에 공백이 포함된 경우 큰따옴표("")로 묶어야 합니다. 예를 들어 "c:\project a\\"입니다.

- 동일한 줄에 있는 스위치와 인수 사이에 공백 문자를 하나 삽입합니다. 예를 들어 **devenv /log output.txt** 명령은 IDE를 열고 해당 세션에 대한 모든 로그 정보를 output.txt에 출력합니다.

- `devenv` 명령에서는 패턴 일치 구문을 사용할 수 없습니다.

## <a name="devenv-switches"></a>devenv 스위치
 다음 명령줄 스위치를 사용하여 IDE를 표시하고 설명된 작업을 수행할 수 있습니다.

|명령줄 스위치|설명|
|-------------------------|-----------------|
|[/명령 (devenv.exe)](../../ide/reference/command-devenv-exe.md)|IDE를 시작하고 지정한 명령을 실행합니다.|
|[/DebugExe (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|디버거의 제어로 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 실행 파일을 로드합니다. 이 스위치는 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 또는 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 실행 파일에 사용할 수 없습니다. 자세한 내용은 [디버거에서 자동으로 프로세스 시작](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger)을 참조하세요.|
|[/LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) 또는 `/l`|IDE의 기본 언어를 설정합니다. 지정한 언어가 Visual Studio 설치에 포함되어 있지 않은 경우 이 설정은 무시됩니다.|
|[/Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]를 시작하고 모든 작업을 로그 파일에 기록합니다.|
|[/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) or `/r`|지정한 솔루션을 컴파일하고 실행합니다.|
|[/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|지정한 솔루션을 컴파일 및 실행하고, 솔루션 실행 시 IDE를 최소화하고, 솔루션 실행이 완료되면 IDE를 닫습니다.|
|[/UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|IDE에서 **옵션** 대화 상자, **프로젝트** 옵션의 VC++ 디렉터리 섹션에 지정된 설정 대신 PATH, INCLUDE 및 LIB 환경 변수를 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 컴파일에 사용하도록 합니다. 자세한 내용은 [명령줄 빌드에 대 한 경로 및 환경 변수 설정](https://msdn.microsoft.com/library/99389528-deb5-43b9-b99a-03c8773ebaf4) 을 참조 하세요.|
|[/Edit (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|이 애플리케이션의 실행 중인 인스턴스에서 지정한 파일을 엽니다. 실행 중인 인스턴스가 없으면 간단한 창 레이아웃을 사용하여 새 인스턴스를 시작합니다.|
|[/ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|지정한 추가 기능을 로드하지 않고 Visual Studio IDE 인스턴스를 시작합니다.|
|[/안전 (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|안전 모드에서 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]를 시작하고 기본 환경 및 서비스와 타사 패키지의 배송된 버전만 로드합니다.|
|[/ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|문제 VSPackage를 로드하지 않으려는 사용자가 VSPackage에 추가한 SkipLoading 태그를 모두 지웁니다.|
|[/Setup(devenv.exe)](../../ide/reference/setup-devenv-exe.md)|Visual Studio가 사용 가능한 모든 VSPackage에서 메뉴, 도구 모음 및 명령 그룹을 설명하는 리소스 메타데이터를 강제로 병합하도록 합니다.|

 다음 명령줄 스위치를 사용하여 설명된 작업을 수행할 수 있습니다. 이러한 명령줄 스위치는 IDE를 표시하지 않습니다.

|명령줄 스위치|설명|
|-------------------------|-----------------|
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|**명령 프롬프트 창**에 devenv 스위치에 대한 도움말을 표시합니다.<br /><br /> **Devenv /?**|
|[/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)|지정한 솔루션의 구성에 따라 지정한 솔루션 또는 프로젝트를 빌드합니다.<br /><br /> **Devenv myproj.csproj /build**|
|[/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|소스 파일에 영향을 주지 않고 빌드 명령에 의해 생성된 파일을 삭제합니다.<br /><br /> **Devenv myproj.csproj /clean**|
|[/배포 (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)|솔루션 구성에 따라 배포에 필요한 파일과 함께 솔루션을 빌드합니다.<br /><br /> **Devenv myproj.csproj /deploy**|
|[/Diff](../../ide/reference/diff.md)|두 파일을 비교합니다.  네 개의 매개 변수 SourceFile, TargetFile, SourceDisplayName(선택 사항), TargetDisplayName(선택 사항)을 가져옵니다.|
|[/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|*\<VisualStudioInstallDir>* *\<VisualStudioInstallDir>* **새 프로젝트** 및 **새 항목 추가** 대화 상자를 통해 액세스할 수 있도록 \Common7\IDE\ProjectTemplates 또는 \Common7\IDE\ItemTemplates에 있는 프로젝트 또는 항목 템플릿을 등록 합니다.<br /><br /> **Devenv /InstallVSTemplates**|
|[/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)|빌드 시 오류를 받을 파일을 지정할 수 있습니다.<br /><br /> **Devenv myproj.csproj /build /out log.txt**|
|[/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|빌드, 정리 또는 배포할 프로젝트입니다. /build, /rebuild, /clean 또는 /deploy 스위치도 제공한 경우에만 이 스위치를 사용할 수 있습니다.|
|[/Svconfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|빌드 또는 배포할 프로젝트 구성을 지정합니다. /project 스위치도 제공한 경우에만 이 스위치를 사용할 수 있습니다.|
|[/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|지정한 솔루션의 구성에 따라 지정한 솔루션 또는 프로젝트를 정리한 후 빌드합니다.|
|[/ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|Visual Studio 기본 설정을 복원합니다. 필요에 따라 설정을 지정한 .vssettings 파일로 초기화합니다.|
|[/Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에 시스템의 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 패키지를 병합하고 MEF 캐시에서 변경 내용을 확인하도록 알립니다.|
|[/Upgrade (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|지정한 솔루션 파일 및 모든 프로젝트 파일이나 지정한 프로젝트 파일을 이러한 파일의 현재 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 형식으로 업그레이드합니다.|

## <a name="see-also"></a>관련 항목
 [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)
