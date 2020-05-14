---
title: '연습: 여러 컴퓨터 빌드 환경 만들기'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11b158854a0026de28cb2fb0a582bbaf764eeaa4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68461533"
---
# <a name="walkthrough-create-a-multiple-computer-build-environment"></a>연습: 여러 컴퓨터 빌드 환경 만들기

호스트 컴퓨터에 Visual Studio를 설치한 다음 다른 컴퓨터가 빌드에 참여할 수 있도록 다양한 파일 및 설정을 해당 컴퓨터로 복사하여 조직 내에서 빌드 환경을 만들 수 있습니다. 다른 컴퓨터에 Visual Studio를 설치할 필요는 없습니다.

이 문서에서는 외부에 소프트웨어를 재배포하거나 타사에 빌드 환경을 제공하기 위한 권한에 대해 설명하지 않습니다.

> 고지 사항<br /><br /> 이 문서는 “있는 그대로” 제공됩니다. 개괄된 단계는 테스트를 거친 것이지만 모든 구성을 완전히 테스트할 수는 없습니다. Microsoft는 습득하는 추가 정보가 있을 경우 해당 정보로 이 문서를 최신 상태로 유지할 계획입니다. URL 및 기타 인터넷 웹 사이트 참조를 포함하여 이 설명서에 제공된 정보와 견해는 예고 없이 변경될 수 있습니다. Microsoft는 여기에 제공된 정보에 대해 어떠한 명시적 또는 묵시적 보증도 하지 않습니다. 정보의 사용으로 발생하는 위험은 귀하의 책임입니다.<br /><br /> 이 문서는 귀하에게 Microsoft 제품의 어떠한 지적 재산에 대한 법적 권리도 부여하지 않습니다. 귀하는 참조를 위해 내부적으로 이 문서를 복사하고 사용할 수 있습니다.<br /><br /> 귀하에게는 이 문서와 관련하여 Microsoft에 제안, 의견 또는 기타 피드백("피드백")을 제공해야 할 의무가 없습니다. 그러나 귀하가 자발적으로 제공하는 피드백은 Microsoft 제품 및 관련 사양이나 기타 설명서("Microsoft 제공 사항"으로 통칭)에 사용될 수 있으며, 이러한 제공 사항은 다른 타사가 자체 제품을 개발하는 데 사용할 수 있습니다. 이에 따라 귀하가 이 문서의 임의 버전이나 이 문서가 적용되는 Microsoft 제공 사항에 대한 피드백을 Microsoft에 제공할 경우 귀하는 (a) Microsoft가 귀하의 피드백을 임의의 Microsoft 제공 사항에서 자유롭게 사용, 재현, 사용 허가, 배포 및 기타 방식으로 상품화할 수 있다는 사실에 동의하게 됩니다. (b) 또한 귀하는 다른 제품이 귀하의 피드백을 포함하는 Microsoft 제품의 특정 부분을 사용하거나 해당 부분과 상호 작용하는 데 필요한 특허권만 요금 없이 타사에 부여하며, (c) (i) 특허권, 저작권 또는 타사의 기타 지적 재산권 청구/권리가 적용된다고 믿을 근거가 있거나 (ii) 피드백을 포함하거나 피드백에서 파생되는 MS 제공 사항 또는 기타 Microsoft 지적 재산을 타사에 사용 허가하거나 기타 방식으로 타사와 공유하게 만드는 사용 약관이 적용되는 피드백을 Microsoft에 제공하지 않습니다.

이 연습은 다음 운영 체제에 대한 유효성이 검사되었습니다.

- Windows 8(x86 및 x64)
- Windows 7 Ultimate
- Windows Server 2008 R2 Standard

이 연습의 단계를 완료한 후에는 다중 컴퓨터 환경을 사용하여 다음 종류의 앱을 빌드할 수 있습니다.

- Windows 8 SDK를 사용하는 C++ 데스크톱 앱
- .NET Framework 4.5를 대상으로 하는 Visual Basic 또는 C# 데스크톱 앱

다중 컴퓨터 환경을 사용하여 다음 종류의 앱을 빌드할 수는 없습니다.

- UWP 앱. UWP 앱을 빌드하려면 빌드 컴퓨터에 Visual Studio를 설치해야 합니다.
- .NET Framework 4 또는 그 이전 버전을 대상으로 하는 데스크톱 앱. 이러한 종류의 앱을 빌드하려면 빌드 컴퓨터에 Visual Studio나 .NET 참조 어셈블리 및 도구(Windows 7.1 SDK)를 설치해야 합니다.

## <a name="prerequisites"></a>사전 요구 사항

**.NET 데스크톱 개발** 워크로드가 설치된 Visual Studio.

## <a name="install-software-on-the-computers"></a>컴퓨터에 소프트웨어 설치

먼저 호스트 컴퓨터를 설정한 다음 빌드 컴퓨터를 설정합니다.

호스트 컴퓨터에 Visual Studio를 설치하여 나중에 빌드 컴퓨터로 복사할 파일 및 설정을 만듭니다. x86 또는 x64 컴퓨터에 Visual Studio를 설치할 수 있지만 빌드 컴퓨터의 아키텍처는 호스트 컴퓨터의 아키텍처와 일치해야 합니다.

1. 호스트 컴퓨터에 Visual Studio를 설치합니다.

2. 빌드 컴퓨터에 .NET Framework 4.5 이상을 설치합니다. 설치되어 있는지 확인하려면 레지스트리 하위 키 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**의 **버전** 항목 값이 **4.5** 이상인지 확인합니다.

## <a name="copy-files-from-the-host-computer-to-the-build-computer"></a>호스트 컴퓨터에서 빌드 컴퓨터로 파일 복사

이 단원에서는 특정 파일, 컴파일러, 빌드 도구, MSBuild 자산 및 레지스트리 설정을 호스트 컴퓨터에서 빌드 컴퓨터로 복사하는 방법에 대해 설명합니다. 다음 단계에서는 Visual Studio가 호스트 컴퓨터의 기본 위치에 설치되어 있다고 가정합니다. 다른 위치에 설치한 경우 단계를 적절하게 조정하십시오.

- x86 컴퓨터에서 기본 위치는 *C:\Program Files\Microsoft Visual Studio*입니다.
- x64 컴퓨터에서 기본 위치는 *C:\Program Files (x86)\Microsoft Visual Studio*입니다.

*Program Files* 폴더의 이름은 설치된 운영 체제에 따라 달라집니다. x86 컴퓨터에서는 이름이 *Program Files*이고, x64 컴퓨터에서는 이름이 *Program Files (x86)* 입니다. 시스템 아키텍처에 관계없이 이 연습에서는 *Program Files* 폴더를 *%ProgramFiles%* 로 나타냅니다.

> [!NOTE]
> 빌드 컴퓨터에서는 모든 관련 파일이 동일한 드라이브에 있어야 합니다. 하지만 해당 드라이브의 드라이브 문자는 호스트 컴퓨터에서 Visual Studio가 설치된 드라이브의 드라이브 문자와 다를 수 있습니다. 어떤 경우이든 이 문서의 뒷부분에 설명된 것처럼 레지스트리 항목을 만들 때는 파일의 위치를 감안해야 합니다.

### <a name="copy-the-windows-sdk-files-to-the-build-computer"></a>Windows SDK 파일을 빌드 컴퓨터로 복사

1. Windows SDK for Windows 8만 설치되어 있는 경우 호스트 컴퓨터에서 빌드 컴퓨터로 다음 폴더를 재귀적으로 복사합니다.

   - %ProgramFiles%\Windows Kits\8.0\bin\

   - %ProgramFiles%\Windows Kits\8.0\Catalogs\

   - %ProgramFiles%\Windows Kits\8.0\DesignTime\

   - %ProgramFiles%\Windows Kits\8.0\include\

   - %ProgramFiles%\Windows Kits\8.0\Lib\

   - %ProgramFiles%\Windows Kits\8.0\Redist\

   - %ProgramFiles%\Windows Kits\8.0\References\

   다음과 같은 기타 Windows 8 키트도 있을 경우

   - Microsoft Windows 평가 및 배포 키트

   - Microsoft Windows 드라이버 키트

   - Microsoft Windows 하드웨어 인증 키트

   이전 단계에 나열된 *%ProgramFiles%\Windows Kits\8.0* 폴더에 여러 파일이 설치되었을 수 있으며, 해당 사용 약관에 따라 해당 파일에 대한 빌드 서버 권한이 허용되지 않을 수 있습니다. 설치된 모든 Windows 키트에 대한 사용 약관에서 파일을 빌드 컴퓨터로 복사할 수 있는지 여부를 확인합니다. 사용 약관에 따라 빌드 서버 권한이 허용되지 않으면 빌드 컴퓨터에서 파일을 제거합니다.

2. 호스트 컴퓨터에서 빌드 컴퓨터로 다음 폴더를 재귀적으로 복사합니다.

    - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\

    - %ProgramFiles%\Common Files\Merge Modules\

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\VC\

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\Tools\ProjectComponents\

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETFramework\v4.5\

3. 호스트 컴퓨터에서 빌드 컴퓨터로 다음 파일을 복사합니다.

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\IDE\msobj110.dll

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\IDE\mspdb110.dll

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\IDE\mspdbcore.dll

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\IDE\mspdbsrv.exe

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\IDE\msvcdis110.dll

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\Tools\makehm.exe

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\Tools\VCVarsQueryRegistry.bat

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\Tools\vsvars32.bat

4. 다음 Visual C++ 런타임 라이브러리는 빌드 컴퓨터에서 빌드 출력을 자동화된 테스트의 일환 등으로 실행하는 경우에만 필요합니다. 파일은 시스템 아키텍처에 따라 일반적으로 *%ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\VC\redist\x86* 또는 *%ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\VC\redist\x64* 폴더 아래의 하위 폴더에 있습니다. x86 시스템에서는 x86 이진 파일을 *Windows\System32* 폴더로 복사합니다. x64 시스템에서는 x86 이진 파일을 *Windows\SysWOW64* 폴더로 복사하고, x64 이진 파일을 *Windows\System32* 폴더로 복사합니다.

    - \Microsoft.VC110.ATL\atl110.dll

    - \Microsoft.VC110.CRT\msvcp110.dll

    - \Microsoft.VC110.CRT\msvcr110.dll

    - \Microsoft.VC110.CXXAMP\vcamp110.dll

    - \Microsoft.VC110.MFC\mfc110.dll

    - \Microsoft.VC110.MFC\mfc110u.dll

    - \Microsoft.VC110.MFC\mfcm110.dll

    - \Microsoft.VC110.MFC\mfcm110u.dll

    - \Microsoft.VC110.MFCLOC\mfc110chs.dll

    - \Microsoft.VC110.MFCLOC\mfc110cht.dll

    - \Microsoft.VC110.MFCLOC\mfc110deu.dll

    - \Microsoft.VC110.MFCLOC\mfc110enu.dll

    - \Microsoft.VC110.MFCLOC\mfc110esn.dll

    - \Microsoft.VC110.MFCLOC\mfc110fra.dll

    - \Microsoft.VC110.MFCLOC\mfc110ita.dll

    - \Microsoft.VC110.MFCLOC\mfc110jpn.dll

    - \Microsoft.VC110.MFCLOC\mfc110kor.dll

    - \Microsoft.VC110.MFCLOC\mfc110rus.dll

    - \Microsoft.VC110.OPENMP\vcomp110.dll

5. [디버그 실행 파일을 실행하기 위한 테스트 컴퓨터 준비](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)에 설명된 대로 다음 파일만 *Debug_NonRedist\x86* 또는 *Debug_NonRedist\x64* 폴더에서 빌드 컴퓨터로 복사됩니다. 다른 파일은 복사할 수 없습니다.

    - \Microsoft.VC110.DebugCRT\msvcp110d.dll

    - \Microsoft.VC110.DebugCRT\msvcr110d.dll

    - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110ud.dll

    - \Microsoft.VC110.DebugMFC\mfcm110d.dll

    - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

    - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="create-registry-settings"></a>레지스트리 설정 만들기

MSBuild에 대한 설정을 구성하려면 레지스트리 항목을 만들어야 합니다.

1. 레지스트리 항목의 부모 폴더를 식별합니다. 모든 레지스트리 항목이 동일한 부모 키 아래에 생성됩니다. x86 컴퓨터에서는 부모 키가 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft**입니다. x64 컴퓨터에서는 부모 키가 **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft**입니다. 시스템 아키텍처에 관계없이 이 연습에서는 부모 키를 %RegistryRoot%로 나타냅니다.

    > [!NOTE]
    > 호스트 컴퓨터의 아키텍처가 빌드 컴퓨터의 아키텍처와 다를 경우 각 컴퓨터에서 적절한 부모 키를 사용해야 합니다. 이는 내보내기 프로세스를 자동화하는 경우 특히 중요합니다.
    >
    > 또한 호스트 컴퓨터에서 사용하고 있는 것과 다른 드라이브 문자를 빌드 컴퓨터에서 사용하고 있는 경우 레지스트리 항목의 값이 일치하도록 변경해야 합니다.

2. 빌드 컴퓨터에서 다음 레지스트리 항목을 만듭니다. 이러한 항목은 모두 문자열(레지스트리에서 종류=“REG_SZ”)입니다. 다음 항목의 값을 호스트 컴퓨터에 있는 유사 항목의 값과 동일하게 설정합니다.

   - **%RegistryRoot%\\.NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild Public Assemblies@(기본값)**

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder</strong>

   - **%RegistryRoot%\VisualStudio\11.0@Source 디렉터리**

   - <strong>%RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64</strong>

   - **%RegistryRoot%\VisualStudio\SxS\VC7@11.0**

   - **%RegistryRoot%\VisualStudio\SxS\VS7@11.0**

   - <strong>%RegistryRoot%\Windows Kits\Installed Roots@KitsRoot</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

   x64 빌드 컴퓨터에서는 다음 레지스트리 항목도 만들고 호스트 컴퓨터를 참조하여 설정 방법을 확인합니다.

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder</strong>

   빌드 컴퓨터가 x64이고 64비트 버전의 MSBuild를 사용하려고 하거나 x64 컴퓨터에서 Team Foundation Server 빌드 서비스를 사용하고 있는 경우 네이티브 64비트 레지스트리에서 다음 레지스트리 항목을 만듭니다. 호스트 컴퓨터를 참조하여 다음 항목을 설정하는 방법을 확인합니다.

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

## <a name="set-environment-variables-on-the-build-computer"></a>빌드 컴퓨터에서 환경 변수 설정

빌드 컴퓨터에서 MSBuild를 사용하려면 PATH 환경 변수를 설정해야 합니다. *vcvarsall.bat*를 사용하여 변수를 설정하거나 수동으로 변수를 구성할 수 있습니다.

### <a name="use-vcvarsallbat-to-set-environment-variables"></a>vcvarsall.bat를 사용하여 환경 변수 설정

빌드 컴퓨터에서 **명령 프롬프트** 창을 열고 *%Program Files%\Microsoft Visual Studio\\\<version>\\\<edition>\VC\vcvarsall.bat*를 실행합니다. 명령줄 인수를 사용하여 사용할 도구 집합을 지정할 수 있습니다(x86, 네이티브 x64 또는 x64 크로스 컴파일러). 명령줄 인수를 지정하지 않으면 x86 도구 집합이 사용됩니다.

다음 표에서는 *vcvarsall.bat*에 대해 지원되는 인수를 설명합니다.

|Vcvarsall.bat 인수|컴파일러|빌드 컴퓨터 아키텍처|출력 아키텍처 빌드|
| - |--------------| - | - |
|x86(기본값)|32비트 네이티브|x86, x64|x86|
|x86_amd64|x64 크로스|x86, x64|X64|
|amd64|x64 네이티브|X64|X64|

*vcvarsall.bat*이 실행되면, 즉 오류 메시지가 표시되지 않으면 다음 단계를 건너뛰고 이 문서의 [빌드 컴퓨터의 GAC(전역 어셈블리 캐시)에 MSBuild 어셈블리 설치](#install-msbuild-to-gac) 섹션에서 계속할 수 있습니다.

### <a name="manually-set-environment-variables"></a>환경 변수를 수동으로 설정

1. 명령줄 환경을 수동으로 구성하려면 PATH 환경 변수에 다음 경로를 추가합니다.

    - %Program Files%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\IDE

2. 선택적으로 보다 쉽게 MSBuild를 사용하여 솔루션을 빌드할 수 있도록 PATH 변수에 다음 경로를 추가할 수도 있습니다.

   네이티브 32비트 MSBuild를 사용하려면 PATH 변수에 다음 경로를 추가합니다.

   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools

   - %windir%\Microsoft.NET\Framework\v4.0.30319

   네이티브 64비트 MSBuild를 사용하려면 PATH 변수에 다음 경로를 추가합니다.

   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="install-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a><a name="install-msbuild-to-gac" /> 빌드 컴퓨터의 GAC(전역 어셈블리 캐시)에 MSBuild 어셈블리 설치

MSBuild를 사용하려면 빌드 컴퓨터의 GAC에 일부 추가 어셈블리를 설치해야 합니다.

1. 호스트 컴퓨터에서 빌드 컴퓨터로 다음 어셈블리를 복사합니다. 해당 어셈블리는 GAC에 설치되기 때문에 빌드 컴퓨터에서 어셈블리를 어디에 넣든 상관이 없습니다.

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. GAC에 어셈블리를 설치하려면 빌드 컴퓨터에서 *gacutil.exe*를 찾습니다. 일반적으로 이는 %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\\에 있습니다. 이 폴더를 찾을 수 없으면 이 연습의 [호스트 컴퓨터에서 빌드 컴퓨터로 파일 복사](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) 섹션에 있는 단계를 반복합니다.

     관리 권한이 있는 **명령 프롬프트** 창을 열고 각 파일에 대해 다음 명령을 실행합니다.

     **gacutil -i \<file>**

    > [!NOTE]
    > 어셈블리가 GAC에 완전히 설치되려면 다시 부팅해야 할 수도 있습니다.

## <a name="build-projects"></a>프로젝트 빌드

Visual Studio 프로젝트 및 솔루션은 Azure Pipelines를 사용하여 빌드하거나 명령줄에서 빌드할 수 있습니다. Azure Pipelines를 사용하여 프로젝트를 빌드하면 시스템 아키텍처에 해당하는 MSBuild 실행 파일이 호출됩니다. 명령줄에서는 32비트 MSBuild 또는 64비트 MSBuild를 사용할 수 있으며, PATH 환경 변수를 설정하거나 아키텍처별 MSBuild 실행 파일을 직접 호출하여 MSBuild의 아키텍처를 선택할 수 있습니다.

명령 프롬프트에서 *msbuild.exe*를 사용하려면 다음 명령을 실행합니다. 여기서 *solution.sln*은 솔루션 이름에 대한 자리 표시자입니다.

**msbuild** *solution.sln*

명령줄에서 MSBuild를 사용하는 방법에 대한 자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)를 참조하세요.

## <a name="create-the-build-environment-so-that-it-can-be-checked-into-source-control"></a>소스 제어로 체크 인할 수 있도록 빌드 환경 만들기

다양한 컴퓨터에 배포할 수 있고 파일을 “GAC”화하거나 레지스트리 설정을 수정할 필요가 없는 빌드 환경을 만들 수 있습니다. 다음 단계는 이 작업을 수행하는 한 방법일 뿐입니다. 빌드 환경의 고유한 특성에 맞게 이러한 단계를 조정하십시오.

> [!NOTE]
> 빌드하는 동안 *tracker.exe*가 오류를 throw하지 않도록 증분 빌드가 사용되지 않도록 설정해야 합니다. 증분 빌드가 사용되지 않도록 설정하려면 다음 빌드 매개 변수를 설정하십시오.
>
> **msbuild** *solution.sln* **/p:TrackFileAccess=false**

1. 호스트 컴퓨터에서 *Depot* 디렉터리를 만듭니다.

     이러한 단계에서는 디렉터리를 %Depot%으로 나타냅니다.

2. 이 연습의 [호스트 컴퓨터에서 빌드 컴퓨터로 파일 복사](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) 섹션에 설명된 대로 디렉터리 및 파일을 복사하되 해당 항목을 방금 만든 *%Depot%* 디렉터리에 붙여넣습니다. 예를 들어 *%ProgramFiles%\Windows Kits\8.0\bin*에서 *%Depot%\Windows Kits\8.0\bin*으로 복사합니다.

3. *%Depot%* 에 파일을 붙여넣었으면 다음 변경 내용을 적용합니다.

    - %Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\ 및 \Microsoft.CppCommon.targets\\에서 다음의 모든 인스턴스를 변경합니다.

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         다음으로 변경:

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

         첫 번째 이름 지정 방식에서는 어셈블리가 GAC화되어야 합니다.

    - %Depot% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets에서 모든 다음 인스턴스를 변경합니다.

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         다음으로 변경:

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

4. *.props* 파일(예: *Partner.AutoImports.props*)을 만들어 프로젝트가 포함된 폴더의 루트에 넣습니다. 이 파일은 다양한 리소스를 찾기 위해 MSBuild에 사용되는 변수를 설정하는 데 사용됩니다. 이 파일로 변수를 설정하지 않으면 레지스트리 값을 사용하는 다른 *.props* 파일 및 *.targets* 파일로 변수가 설정됩니다. 레지스트리 값을 설정하지 않을 것이기 때문에 이러한 변수가 비게 되고 빌드가 실패합니다. 대신 *Partner.AutoImports.props*에 다음을 추가합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <!-- This file must be imported by all project files at the top of the project file. -->
    <Project ToolsVersion="4.0"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio\2017\Enterprise\VC\</VCInstallDir_110>
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>
    </PropertyGroup>
    </Project>
    ```

5. 각 프로젝트 파일의 맨 위에서 `<Project Default Targets...>` 줄 다음에 아래 줄을 추가합니다.

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

::: moniker range="vs-2017"

6. 명령줄 환경을 다음과 같이 변경합니다.

    - Depot=*1단계에서 만든 Depot 디렉터리의 위치* 설정

    - Set path=%path%;’컴퓨터에서 MSBuild의 위치’;%Depot%\Windows\System32;%Depot%\Windows\SysWOW64;%Depot%\Microsoft Visual Studio 15.0\Common7\IDE\ 

       네이티브 64비트 빌드의 경우 MSBuild의 64비트 버전을 가리킵니다.

::: moniker-end

::: moniker range=">=vs-2019"

6. 명령줄 환경을 다음과 같이 변경합니다.

    - Depot=*1단계에서 만든 Depot 디렉터리의 위치* 설정

    - Set path=%path%;*컴퓨터에서 MSBuild의 위치*;%Depot%\Windows\System32;%Depot%\Windows\SysWOW64;%Depot%\Microsoft Visual Studio 16.0\Common7\IDE\

       네이티브 64비트 빌드의 경우 MSBuild의 64비트 버전을 가리킵니다.

::: moniker-end

## <a name="see-also"></a>참조

- [디버그 실행 파일을 실행하기 위한 테스트 컴퓨터 준비](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)
- [명령줄 참조](../msbuild/msbuild-command-line-reference.md)