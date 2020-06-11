---
title: 디버거에서 기호 파일(.pdb) 및 소스 파일 설정
description: Visual Studio에서 기호 및 소스 파일을 구성하고 관리하는 방법
ms.custom: ''
ms.date: 10/31/2019
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19eed30074215b64301d7227e93ba6bf5b438d78
ms.sourcegitcommit: 2f64b3b231900018fceafb72b5a1c65140213a18
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "84183814"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio 디버거에서 기호 파일(.pdb) 및 소스 파일 지정(C#, C++, Visual Basic, F#)

기호 파일이라고도 하는 프로그램 데이터베이스( *.pdb*) 파일은 프로젝트의 소스 코드에 있는 식별자 및 문을 컴파일된 앱의 해당 식별자 및 명령에 매핑합니다. 이러한 매핑 파일은 디버거를 소스 코드에 연결하여 디버깅을 가능하게 합니다.

표준 디버그 빌드 구성을 사용하여 Visual Studio IDE에서 프로젝트를 빌드하는 경우 컴파일러에서 적절한 기호 파일을 만듭니다. 이 문서에서는 IDE에서 기호 파일을 관리하는 방법, [디버거 옵션에서 기호 위치를 지정하는 방법](#BKMK_Specify_symbol_locations_and_loading_behavior), 디버깅 중 [기호 로드 상태를 확인](#work-with-symbols-in-the-modules-window)하는 방법, [코드에서 기호 옵션을 설정](#compiler-symbol-options)하는 방법 등을 설명합니다.

기호 파일에 대한 자세한 설명은 다음을 참조하세요.

- [Understand symbol files and Visual Studio symbol settings](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)(기호 파일 및 Visual Studio 기호 설정 이해)

- [Why does Visual Studio require debugger symbol files to exactly match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)(Visual Studio에서 디버거 기호 파일이 빌드 기반이 된 이진 파일과 정확히 일치해야 하는 이유)

## <a name="how-symbol-files-work"></a>기호 파일의 작동 방식

*.pdb* 파일에는 앱의 디버그 구성에 대한 증분 링크를 허용하는 디버깅 및 프로젝트 상태 정보가 저장됩니다. Visual Studio 디버거는 디버깅 중 *.pdb* 파일을 사용하여 다음 두 가지 주요 정보를 확인합니다.

* Visual Studio IDE에 표시할 소스 파일 이름과 줄 번호
* 중단점에 대해 중지할 앱의 위치

기호 파일에는 소스 파일의 위치와 선택적으로 해당 파일을 검색할 서버도 표시됩니다.

디버거는 앱을 빌드할 때 생성된 *.pdb* 파일과 정확히 일치하는 *.pdb* 파일만 로드합니다(즉, 원래 *.pdb* 파일 또는 복사본). 코드 자체가 변경되지 않은 경우에도 앱 레이아웃이 변경될 수 있으므로 [정확한 중복](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)이 필요합니다.

> [!TIP]
> 프로젝트에서 호출하는 Windows 또는 타사 코드와 같은 프로젝트 소스 코드 외부의 코드를 디버그하려면 외부 코드의 *.pdb* 파일(및 필요에 따라 소스 파일)의 위치를 지정해야 하며 이러한 파일은 앱의 빌드와 정확히 일치해야 합니다.

## <a name="symbol-file-locations-and-loading-behavior"></a>기호 파일 위치 및 로드 동작

Visual Studio IDE에서 프로젝트를 디버그할 때 디버거는 프로젝트 폴더에 있는 기호 파일을 자동으로 로드합니다.

> [!NOTE]
> 원격 디바이스에서 관리 코드를 디버그하는 경우 모든 기호 파일은 로컬 머신이나 [디버거 옵션에 지정된](#BKMK_Specify_symbol_locations_and_loading_behavior) 위치에 있어야 합니다.

또한 디버거는 다음 위치에서 기호 파일을 검색합니다.

1. DLL 또는 실행 파일( *.exe*) 내의 지정된 위치

   기본적으로 컴퓨터에서 DLL 또는 *.exe* 파일을 빌드한 경우 링커는 DLL 또는 *.exe* 파일에 관련 *.pdb* 파일의 전체 경로와 파일 이름을 배치합니다. 디버거는 기호 파일이 해당 위치에 있는지 확인합니다.

2. DLL 또는 *.exe* 파일과 동일한 폴더

3. 기호 파일의 디버거 옵션에 지정된 위치. 기호 위치를 추가하고 사용하도록 설정하려면 [기호 위치 구성 및 로드 옵션](#BKMK_Specify_symbol_locations_and_loading_behavior)을 참조하세요.

   - 로컬 기호 캐시 폴더.

   - 선택한 경우 Microsoft 기호 서버와 같은 지정된 네트워크, 인터넷 또는 로컬 기호 서버 및 위치. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]는 `symsrv` 프로토콜을 구현하는 기호 서버에서 디버깅 기호 파일을 다운로드할 수 있습니다. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols)와 [Windows용 디버깅 도구](/windows-hardware/drivers/debugger/index)는 기호 서버를 사용할 수 있는 두 가지 도구입니다.

     사용할 수 있는 기호 서버는 다음과 같습니다.

     **공용 Microsoft 기호 서버**: 시스템 DLL이나 타사 라이브러리를 호출하는 동안 발생하는 크래시를 디버그하려면 시스템 *.pdb* 파일이 필요한 경우가 많습니다. 시스템 *.pdb* 파일에는 Windows DLL, *.exe* 파일 및 디바이스 드라이버용 기호가 포함되어 있습니다. 공용 Microsoft 기호 서버에서 Windows 운영 체제, MDAC, IIS, ISA 및 .NET용 기호를 가져올 수 있습니다.

     **내부 네트워크 또는 로컬 머신의 기호 서버**: 팀이나 회사는 사용자 고유 제품에 사용하기 위해서나 외부 소스의 기호에 대한 캐시로 기호 서버를 만들 수 있습니다. 기호 서버가 사용자의 컴퓨터에 있을 수도 있습니다.

     **타사 기호 서버**: Windows 애플리케이션 및 라이브러리의 타사 공급자는 인터넷에 있는 기호 서버에 대한 액세스를 제공할 수 있습니다.

     > [!WARNING]
     > 공용 Microsoft 기호 서버 이외의 기호 서버를 사용할 경우 기호 서버와 해당 경로를 신뢰할 수 있는지 확인합니다. 기호 파일은 임의의 실행 가능한 코드를 포함할 수 있으므로 보안 위협에 노출될 수 있습니다.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>기호 위치 및 로드 옵션 구성

**도구** > **옵션** > **디버깅** > **기호** 페이지에서 다음을 수행할 수 있습니다.

- Microsoft, Windows 또는 타사 구성 요소에 대한 검색 경로 및 기호 서버를 지정하고 선택합니다.
- 디버거에서 기호를 자동으로 로드하거나 로드하지 않을 모듈을 지정합니다.
- 본격적으로 디버그하는 동안 이러한 설정을 변경합니다. [디버그하는 동안 기호 관리](#manage-symbols-while-debugging)를 참조하세요.

**기호 위치 및 로드 옵션을 지정하려면:**

1. Visual Studio에서 **도구** > **옵션** > **디버깅** > **기호**(또는 **디버그** > **옵션** > **기호**)를 엽니다.

2. **기호 파일(.pdb) 위치**에서 다음을 수행합니다.
   - **Microsoft 기호 서버** 또는 **NuGet.org 기호 서버**를 사용하려면 확인란을 선택합니다.

   - 새 기호 서버 위치를 추가하려면 다음을 수행합니다.
     1. 도구 모음에서 **+** 기호를 선택합니다.
     1. 텍스트 필드에 기호 서버 또는 기호 위치의 URL(http), 네트워크 공유 또는 로컬 경로를 입력합니다. 문 완성 기능으로 올바른 형식을 찾을 수 있습니다.

     ![도구 &#45; 옵션 &#45; 디버깅 &#45; 기호 페이지](media/dbg-options-symbols.gif "도구 &#45; 옵션 &#45; 디버깅 &#45; 기호 페이지")

     >[!NOTE]
     >지정된 폴더만 검색합니다. 검색하려는 하위 폴더에 대한 항목을 추가해야 합니다.

   - 새 VSTS 기호 서버 위치를 추가하려면 다음을 수행합니다.
     1. 도구 모음에서 ![도구&#47; 옵션&#47; 디버깅&#47;기호 새 서버 아이콘](media/dbg_tools_options_foldersicon.png "도구 &#45; 옵션 &#45; 디버깅 &#45; 기호 새 서버 아이콘") 아이콘을 선택합니다.
     1. **VSTS 기호 서버에 연결** 대화 상자에서 사용 가능한 기호 서버 중 하나를 선택하고 **연결**을 선택합니다.

   - 기호 위치의 로드 순서를 변경하려면 **Ctrl**+**Up** 및 **Ctrl**+**Down** 또는 **위쪽** 및 **아래쪽** 화살표 아이콘을 사용합니다.
   - URL 또는 경로를 편집하려면 항목을 두 번 클릭하거나, 항목을 선택하고 **F2** 키를 누릅니다.
   - 항목을 제거하려면 항목을 선택하고 **-** 아이콘을 선택합니다.

3. (선택 사항) 기호 로드 성능을 향상하려면 **이 디렉터리에서 기호 캐시** 아래에서 기호 서버에서 기호를 복사할 수 있는 로컬 폴더 경로를 입력합니다.

   > [!NOTE]
   > 로컬 기호 캐시를 C:\Windows 또는 하위 폴더와 같은 보호된 폴더에 두지 마세요. 대신 읽기/쓰기 폴더를 사용하십시오.

   > [!NOTE]
   > C++ 프로젝트의 경우 `_NT_SYMBOL_PATH` 환경 변수를 설정하면 **이 디렉터리에서 기호 캐시** 아래에서 설정된 값이 재정의됩니다.

4. 디버거가 시작될 때 **기호 파일(.pdb) 위치**에서 로드하려는 모듈을 지정합니다.

   - **Load all modules, unless excluded**(제외되지 않은 모든 모듈 로드)(기본값)를 선택하여 명시적으로 제외한 모델을 제외하고 기호 파일 위치에 있는 모든 모듈의 모든 기호를 로드합니다. 특정 모듈을 제외하려면 **제외된 모듈 지정**을 선택하고 **+** 아이콘을 선택한 다음, 제외할 모듈의 이름을 입력하고 **확인**을 선택합니다.

   - 기호 파일 위치에서 지정하는 모듈만 로드하려면 **지정된 모듈만 로드**를 선택합니다. **포함된 모듈 지정**을 선택하고 **+** 아이콘을 선택한 다음, 포함할 모듈의 이름을 입력하고 **확인**을 선택합니다. 다른 모듈의 기호 파일은 로드되지 않습니다.

5. **확인**을 선택합니다.

## <a name="other-symbol-options-for-debugging"></a>디버깅을 위한 기타 기호 옵션

**도구** > **옵션** > **디버깅** > **일반**(또는 **디버그** > **옵션** > **일반**)에서 추가 기호 옵션을 선택할 수 있습니다.

- **dll 내보내기 로드(네이티브 전용)**

  C/C++에 대한 DLL 내보내기 테이블이 로드됩니다. 자세한 내용은 [DLL 내보내기 테이블](#use-dumpbin-exports)을 참조하세요. DLL 내보내기 정보를 읽으면 약간의 오버헤드가 발생하므로 내보내기 테이블 로드는 기본적으로 꺼져 있습니다. C/C++ 빌드 명령줄에서 `dumpbin /exports`를 사용할 수도 있습니다.

- **주소 수준 디버깅 사용** 및 **소스를 사용할 수 없는 경우 디스어셈블리 표시**

  소스 또는 기호 파일을 찾을 수 없는 경우 항상 디스어셈블리를 표시합니다.

  ![옵션 &#47; 디버깅 &#47; 일반 디스어셈블리 옵션](../debugger/media/dbg_options_general_disassembly_checkbox.png "옵션 &#47; 디버깅 &#47; 일반 디스어셈블리 옵션")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **소스 서버 지원 사용**

  로컬 머신에 소스 코드가 없거나 *.pdb* 파일이 소스 코드와 일치하지 않는 경우 소스 서버를 사용하여 앱을 디버그할 수 있습니다. 소스 서버에서는 파일에 대한 요청을 전달받고 소스 제어에서 실제 파일을 반환합니다. 소스 서버는 *srcsrv.dll*이라는 DLL을 사용하여 실행되어 앱의 *.pdb* 파일을 읽습니다. *.pdb* 파일에는 소스 코드 리포지토리에 대한 포인터와 리포지토리에서 소스 코드를 검색하는 데 사용되는 명령이 포함되어 있습니다.

  *srcsrv.ini*라는 파일에 허용되는 명령을 나열하여 *srcsrv.dll*이 앱의 *.pdb* 파일에서 실행할 수 있는 명령을 제한할 수 있습니다. *srcsrv.ini* 파일을 *srcsrv.dll* 및 *devenv.exe*와 동일한 폴더에 저장합니다.

  >[!IMPORTANT]
  >임의 명령이 앱의 *.pdb* 파일에 포함될 수 있으므로 실행하려는 명령만 *srcsrv.ini* 파일에 삽입해야 합니다. *srcsvr.ini* 파일에 포함되지 않은 명령을 실행하려고 하면 확인 대화 상자가 나타납니다. 자세한 내용은 다음을 참조하세요. [보안 경고: 디버거가 신뢰할 수 없는 명령을 실행해야 합니다](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >명령 매개 변수에 대해서는 유효성 검사를 수행하지 않으므로 신뢰되는 명령에 대해 주의를 기울여야 합니다. 예를 들어 *cmd.exe*를 *srcsrv.ini*에 나열한 경우 악의적인 사용자가 *cmd.exe*에 이 명령을 위험하게 만드는 매개 변수를 지정할 수도 있습니다.

  이 항목과 원하는 자식 항목을 선택합니다. **부분 트러스트 어셈블리에 대한 소스 서버 허용(관리형만 해당)** 및 **항상 묻지 않고 신뢰하지 않는 소스 서버 명령 실행**은 보안 위험을 증가시킬 수 있습니다.

  ![소스 서버 옵션 사용](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>컴파일러 기호 옵션

Visual Studio IDE에서 프로젝트를 빌드하고 표준 **디버그** 빌드 구성을 사용하면 C++ 및 관리형 컴파일러에서 코드에 적절한 기호 파일을 만듭니다. 코드에서 컴파일러 옵션을 설정할 수도 있습니다.

### <a name="net-options"></a>.NET 옵션

**/debug**로 빌드하여 *.pdb* 파일을 만듭니다. **/debug:full** 또는 **/debug:pdbonly**를 사용하여 애플리케이션을 빌드할 수 있습니다. **/debug:full** 을 사용하여 빌드하면 디버깅 가능한 코드가 생성됩니다. **/debug:pdbonly**를 사용하여 빌드하면 *.pdb* 파일이 생성되지만 디버그 정보를 사용할 수 있다는 사실을 JIT 컴파일러에 알리는 `DebuggableAttribute`는 생성되지 않습니다. 디버깅할 수 없도록 하려는 릴리스 빌드에 대해 *.pdb* 파일을 생성하려면 **/debug:pdbonly**를 사용합니다. 자세한 내용은 [/debug(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) 또는 [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug)를 참조하세요.

### <a name="cc-options"></a>C/C++ 옵션

- *VC\<x>.pdb* 및 *\<project>.pdb* 파일

  C/C++의 *.pdb* 파일은 [/ZI 또는 /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)를 사용하여 빌드할 때 만들어집니다. [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]의 [/Fd](/cpp/build/reference/fd-program-database-file-name) 옵션은 컴파일러에서 만드는 *.pdb* 파일의 이름을 지정합니다. IDE를 사용하여 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 프로젝트를 만드는 경우 이름이 *\<project>.pdb*인 *.pdb* 파일을 만들도록 **/Fd** 옵션이 설정됩니다.

  메이크파일을 사용하여 C/C++ 애플리케이션을 빌드하고 **/Fd** 없이 **/ZI** 또는 **/Zi**를 지정하는 경우 컴파일러에서 *.pdb* 파일 2개를 만듭니다.

  - *VC\<x>.pdb*. 여기서 *\<x>* 는 Microsoft C++ 컴파일러의 버전을 나타냅니다(예: *VC11.pdb*).

    *VC\<x>.pdb* 파일에는 각 개체 파일에 대한 디버깅 정보가 모두 들어 있으며 프로젝트 메이크파일과 동일한 디렉터리에 저장됩니다. C/C++ 컴파일러는 개체 파일을 만들 때마다 *VC\<x>.pdb*에 디버그 정보를 병합합니다. 따라서 *\<windows.h>* 와 같은 공통 헤더 파일은 모든 소스 파일에 포함되지만, 해당 헤더의 typedef는 모든 개체 파일에 포함되지 않고 한 번만 저장됩니다. 삽입되는 정보에는 유형 정보가 포함되지만 함수 정의와 같은 기호 정보는 포함되지 않습니다.

  - *\<project>.pdb*

    *\<project>.pdb* 파일은 프로젝트 *.exe* 파일의 모든 디버그 정보를 저장하며 *\debug* 하위 디렉터리에 있습니다. *\<project>.pdb* 파일에는 *VC\<x>.pdb*에 있는 형식 정보뿐만 아니라 함수 프로토타입을 비롯한 전체 디버그 정보가 포함됩니다.

  *VC\<x>.pdb* 및 *\<project>.pdb* 파일은 모두 증분 업데이트를 허용합니다. 링커에서는 작성되는 *.exe* 파일이나 *.dll* 파일에 *.pdb* 파일의 경로도 포함합니다.

- <a name="use-dumpbin-exports"></a>DLL 내보내기 테이블

  DLL의 내보내기 테이블에서 사용할 수 있는 기호를 확인하려면 `dumpbin /exports`를 사용합니다. Windows 메시지, Windows 프로시저(WindowProcs), COM 개체, 마샬링 또는 기호가 없는 DLL을 사용하여 작업하는 경우 DLL 내보내기 테이블의 기호 정보가 유용할 수 있으며 모든 32비트 시스템 DLL에 기호를 사용할 수 있습니다. 호출은 현재 함수(가장 안쪽에 중첩된)가 맨 위에 표시되어 호출한 순서로 나열됩니다.

  `dumpbin /exports` 출력을 읽으면 영숫자가 아닌 문자를 포함하여 정확한 함수 이름을 확인할 수 있습니다. 함수에서 중단점을 설정할 때 정확한 함수 이름을 확인하면 유용합니다. 디버거의 다른 곳에서는 함수 이름이 잘릴 수 있기 때문입니다. 자세한 내용은 [dumpbin /exports](/cpp/build/reference/dash-exports)를 참조하십시오.

### <a name="web-applications"></a>웹 애플리케이션

ASP.NET 애플리케이션의 *web.config* 파일을 디버그 모드로 설정합니다. 디버그 모드에서는 동적으로 생성된 파일에 대한 기호가 ASP.NET에서 생성되며 디버거가 ASP.NET 애플리케이션에 연결될 수 있습니다. 웹 프로젝트 템플릿에서 프로젝트를 만든 경우 디버그를 시작하면 Visual Studio가 이를 자동으로 설정합니다.

## <a name="manage-symbols-while-debugging"></a>디버그하는 동안 기호 관리

**모듈**, **호출 스택**, **로컬**, **자동** 또는 **조사식** 창을 사용하여 디버그하는 동안 기호를 로드하거나 기호 옵션을 변경할 수 있습니다. 자세한 내용은 [디버거가 앱에 연결되는 방식 자세히 알아보기](../debugger/debugger-tips-and-tricks.md#modules_window)를 참조하세요.

### <a name="work-with-symbols-in-the-modules-window"></a>모듈 창에서 기호 작업

디버그하는 동안 **모듈** 창에서는 디버거가 사용자 코드로 처리하는 코드 모듈, 즉 내 코드와 모듈의 기호 로드 상태를 확인할 수 있습니다. **모듈** 창에서 기호 로드 상태를 모니터링하고 기호를 로드하며 기호 옵션을 변경할 수도 있습니다.

**디버그하는 동안 기호 위치 또는 옵션을 모니터링하거나 변경하려면:**

1. 디버깅 중에 **모듈** 창을 열려면 **디버그** > **Windows** > **모듈**을 선택합니다.
1. **모듈** 창에서 **기호 상태** 또는 **기호 파일** 헤더 또는 모듈을 마우스 오른쪽 단추로 클릭합니다.
1. 팝업 메뉴에서 다음 옵션 중 하나를 선택합니다.

|옵션|설명|
|------------|-----------------|
|**기호 로드**|건너뛰거나, 찾을 수 없거나, 로드되지 않은 기호가 포함된 모듈에 대해 표시됩니다. **옵션** > **디버깅** > **기호** 페이지에 지정된 위치에서 기호를 로드하려고 합니다. 기호 파일을 찾을 수 없거나 로드되지 않는 경우 **파일 탐색기**가 시작되므로 검색할 새 위치를 지정할 수 있습니다.|
|**기호 로드 정보**|로드된 기호 파일의 위치 또는 디버거가 파일을 찾을 수 없는 경우 검색된 위치를 표시합니다.|
|**기호 설정**|기호 위치를 편집하고 추가할 수 있는 **옵션** > **디버깅** > **기호** 페이지를 엽니다.|
|**항상 자동으로 로드**|선택한 기호 파일을 디버거에서 자동으로 로드되는 파일 목록에 추가합니다.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>로드된 기호 없음/로드된 소스 없음 페이지 사용

디버거가 기호 또는 소스 파일을 사용할 수 없는 코드를 중단할 수 있는 방법은 여러 가지가 있습니다.

- 한 단계씩 코드를 실행합니다.
- 중단점 또는 예외에서 코드를 중단합니다.
- 다른 스레드로 전환합니다.
- **호출 스택** 창의 프레임을 두 번 클릭하여 스택 프레임을 변경합니다.

이 경우 디버거는 **로드된 기호 없음** 또는 **로드된 소스 없음** 페이지를 표시하여 필요한 기호나 소스를 찾고 로드할 수 있게 해줍니다.

 ![로드된 기호가 없음 페이지](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**로드된 기호 없음 문서 페이지를 사용하여 누락된 기호를 찾고 로드할 수 있게 하려면:**

- 검색 경로를 변경하려면 선택되지 않은 경로를 선택합니다. 또는 **새 경로**나 **새 VSTS 경로**를 선택하고 새 경로를 입력하거나 선택합니다. 경로를 다시 검색하고 발견되는 기호 파일을 로드하려면 **로드**를 선택합니다.
- 기호 옵션을 재정의하고 검색 경로를 다시 시도하려면 **\<executable-name> 찾아보기**를 선택합니다. 기호 파일이 발견되는 경우 로드되거나, **파일 탐색기**가 열려서 기호 파일을 수동으로 선택할 수 있습니다.
- **옵션** > **디버깅** > **기호** 페이지를 열려면 **기호 설정 변경**을 선택합니다.
- 새 창에 디스어셈블리를 한 번 표시하려면 **디스어셈블리 보기**를 선택하거나, **옵션 대화 상자**를 선택하여 소스 또는 기호 파일을 찾을 수 없는 경우 항상 디스어셈블리를 표시하도록 옵션을 설정합니다.
- 검색된 위치와 결과를 표시하려면 **기호 로드 정보**를 확장합니다.

옵션 중 하나를 실행한 후 디버거가 *.pdb* 파일을 찾고 *.pdb* 파일의 정보를 사용하여 소스 파일을 검색할 수 있으면 소스가 표시됩니다. 그러지 않으면 문제를 설명하고 문제를 해결할 수 있는 작업에 대한 링크를 포함하는 **로드된 소스 없음** 페이지가 표시됩니다.

**솔루션에 소스 파일 검색 경로를 추가하려면:**

디버거가 소스 파일을 검색하는 위치를 지정하고 검색에서 특정 파일을 제외할 수 있습니다.

1. **솔루션 탐색기**에서 솔루션을 선택한 다음에 **속성** 아이콘을 선택하거나, **Alt**+**Enter**를 누르거나, 마우스 오른쪽 단추를 클릭하여 **속성**을 선택합니다.

1. **소스 파일 디버그**를 선택합니다.

1. **소스 코드가 포함되어 있는 디렉터리**에서 검색할 소스 코드 위치를 입력하거나 선택합니다. **새 줄** 아이콘을 사용하여 위치를 추가하거나, **위쪽** 및 **아래쪽** 화살표 아이콘을 사용하여 위치 순서를 바꾸거나, **X** 아이콘을 사용하여 위치를 삭제합니다.

   >[!NOTE]
   >디버거가 지정된 디렉터리만 검색합니다. 검색하려는 하위 디렉터리에 대한 항목을 추가해야 합니다.

1. **다음 소스 파일을 찾지 않음**에서 검색에서 제외할 소스 파일의 이름을 입력합니다.

1. **확인** 또는 **적용**을 선택합니다.

## <a name="see-also"></a>참조
- [Understand symbol files and Visual Studio symbol settings](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)(기호 파일 및 Visual Studio 기호 설정 이해)

- [Visual Studio 2012 및 2013의 .NET 원격 기호 로드 변경 내용](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
