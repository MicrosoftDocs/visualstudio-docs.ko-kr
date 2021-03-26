---
title: 개발자용 명령줄 셸
description: .NET 및 C++ 도구를 더 쉽게 사용할 수 있는 Visual Studio 개발자 명령 프롬프트, Visual Studio 개발자 PowerShell, Visual Studio 터미널을 찾아 사용하는 방법을 알아봅니다.
ms.date: 03/04/2021
ms.custom: contperf-fy21q3
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: fb2c99037577528b77ab5c1b0c74bf7af9e73d1b
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672327"
---
# <a name="developer-command-prompt-and-developer-powershell"></a>개발자 명령 프롬프트 및 개발자 PowerShell

Visual Studio 2019에는 두 가지의 개발자용 명령줄 셸이 있습니다.

- **Visual Studio 개발자 명령 프롬프트** - 명령줄 개발자 도구를 더 쉽게 사용할 수 있도록 특정 환경 변수가 설정된 표준 명령 프롬프트입니다. Visual Studio 2015부터 사용할 수 있습니다.
- **Visual Studio 개발자 PowerShell** - 명령 프롬프트보다 더 강력합니다. 예를 들어 한 명령( *cmdlet* )의 출력을 다른 cmdlet에 전달할 수 있습니다. 이 셸의 환경 변수는 개발자 명령 프롬프트로 설정됩니다. Visual Studio 2019부터 사용할 수 있습니다.

두 셸 모두 명령줄 개발자 도구를 보다 쉽게 사용할 수 있도록 돕는 특정 환경 변수 집합이 있습니다. 이러한 셸 중 하나를 연 후에는 위치를 알 필요 없이 여러 유틸리티에 대한 명령을 입력할 수 있습니다. 실행할 수 있는 명령:

- [`MSBuild`](../../msbuild/msbuild-command-line-reference.md)는 프로젝트 또는 솔루션을 빌드합니다.
- [.NET Framework 도구](/dotnet/framework/tools/index)([`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool) 및 [`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler)).
- C/C++ 컴파일 도구(예: [`CL`](/cpp/build/reference/compiler-command-line-syntax) 및 [`NMAKE`](/cpp/build/reference/running-nmake)).
- 추가 C/C++ 빌드 도구(예: [`LIB`](/cpp/build/reference/lib-reference) 및 [`DUMPBIN`](/cpp/build/reference/dumpbin-reference)).
- [.NET CLI 명령](/dotnet/core/tools/index)(예: [`dotnet`](/dotnet/core/tools/dotnet) 및 [`dotnet run`](/dotnet/core/tools/dotnet-run)). (이러한 명령은 일반 명령 프롬프트에서도 사용할 수 있습니다.)

:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="clrver 도구를 보여주는 Visual Studio용 개발자 명령 프롬프트":::

Visual Studio 2019 버전 16.5부터 Visual Studio에 이러한 셸(개발자 명령 프롬프트 및 개발자 PowerShell)을 호스트할 수 있는 통합 **터미널** 이 포함되어 있습니다. 각 셸의 여러 탭을 열 수도 있습니다. Visual Studio 터미널은 [Windows 터미널](/windows/terminal/) 기반으로 빌드됩니다. Visual Studio에서 터미널을 열려면 **보기** > **터미널** 을 선택합니다.

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="여러 탭을 보여주는 Visual Studio 터미널":::

별도의 앱으로 또는 터미널 창에서 Visual Studio의 개발자 셸 중 하나를 여는 경우 (솔루션이 로드되어 있다면) 현재 솔루션의 디렉터리로 열립니다. 이 동작을 통해 솔루션 또는 그 프로젝트에 대해 명령을 편리하게 실행할 수 있습니다.

## <a name="start-the-shell-from-inside-visual-studio"></a>Visual Studio 내부에서 셸 시작

Visual Studio 내에서 다음 단계에 따라 개발자 명령 프롬프트 또는 개발자 PowerShell을 엽니다.

1. Visual Studio를 엽니다.

1. 메뉴 모음에서 **도구** > **명령줄** > **개발자 명령 프롬프트** 또는 **개발자 PowerShell** 을 선택합니다.

   ![Visual Studio의 명령 프롬프트 메뉴 항목](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="use-the-windows-start-menu"></a>Windows 시작 메뉴 사용

설치한 Visual Studio의 버전과 추가 SDK 및 워크로드에 따라 여러 개의 명령 프롬프트가 표시될 수 있습니다. 다음 단계가 작동하지 않는 경우 [머신에서 수동으로 파일 찾기](#manually-locate-the-file) 또는 [Visual Studio 내에서 셸 시작](#start-the-shell-from-inside-visual-studio)을 시도해 볼 수 있습니다.

### <a name="windows-10"></a>Windows 10

1. **시작** ![키보드의 Windows 로고 키](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)를 선택합니다. **V** 문자로 스크롤합니다.

1. **Visual Studio 2019** 폴더를 확장합니다.

1. **VS 2019용 개발자 명령 프롬프트** 또는 **VS 2019용 개발자 PowerShell** 을 선택합니다.

   또는 작업 표시줄의 검색 상자에서 셸의 이름을 입력하고 결과 목록에 검색 일치가 표시되기 시작할 때 원하는 결과를 선택할 수 있습니다.

   ![Windows 10의 검색 동작을 보여 주는 애니메이션 gif](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Windows 로고 키 ![키보드에서 Windows 로고 키](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)를 눌러 **시작** 화면으로 이동합니다. 예를 들어 키보드에서

1. **시작** 화면에서 **Ctrl**+**Tab** 을 눌러 **앱** 목록을 열고 **V** 를 누릅니다. 그러면 설치된 모든 Visual Studio 명령 프롬프트가 포함된 목록을 가져옵니다.

1. **VS 2019용 개발자 명령 프롬프트** 또는 **VS 2019용 개발자 PowerShell** 을 선택합니다.

### <a name="windows-7"></a>Windows 7

1. **시작** 을 선택한 다음 **모든 프로그램** 을 확장합니다.

1. **Visual Studio 2019** > **Visual Studio 도구** > **VS 2019용 개발자 명령 프롬프트** 또는 **VS 2019용 개발자 PowerShell** 을 선택합니다.

   ![명령 프롬프트가 강조 표시된 Windows 7 시작 메뉴](./media/developer-command-prompt-for-vs/windows-7-menu.png)

[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 또는 [이전 버전](https://developer.microsoft.com/windows/downloads/sdk-archive)과 같은 다른 SDK를 설치한 경우 추가 명령 프롬프트가 표시될 수 있습니다. 각 도구의 설명서를 확인하여 사용할 명령 프롬프트 버전을 결정합니다.

## <a name="manually-locate-the-file"></a>수동으로 파일 찾기

일반적으로 설치한 셸의 바로 가기는 *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools* 와 같이 Visual Studio에 대한 **시작 메뉴** 폴더에 배치됩니다. 하지만 명령 프롬프트를 검색했는데 예상된 결과가 나타나지 않는 경우, 컴퓨터에서 수동으로 파일을 찾을 수 있습니다.

### <a name="developer-command-prompt"></a>개발자 명령 프롬프트

*VsDevCmd.bat* 와 같은 명령 프롬프트 파일의 이름 검색을 시도하거나 *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* 와 같은 Visual Studio용 도구 폴더로 이동합니다(경로는 Visual Studio 버전, 에디션 및 설치 위치에 따라 바뀜).

명령 프롬프트 파일을 찾은 후에는 일반 명령 프롬프트 창에서 다음 명령을 입력하여 엽니다.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

또는 Windows **실행** 대화 상자에서 다음 명령을 입력합니다.

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> Visual Studio 설치와 일치하도록 경로를 편집해야 합니다.

### <a name="developer-powershell"></a>개발자 PowerShell

이름이 *Launch-VsDevShell.ps1* 인 PowerShell을 검색하거나 Visual Studio에 대한 도구 폴더(예: *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools*)로 이동합니다. (경로는 Visual Studio 버전, 에디션 및 설치 위치에 따라 변경됩니다.) PowerShell 파일을 찾으면 Windows PowerShell 또는 PowerShell 6 프롬프트에서 다음 명령을 입력하여 실행합니다.

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

기본적으로 실행되는 개발자 PowerShell은 설치 경로가 *Launch-VsDevShell.ps1* 파일이 있는 경로인 Visual Studio 설치에 대해 구성됩니다.

> [!TIP]
> cmdlet의 실행을 위해 [실행 정책](/powershell/module/microsoft.powershell.core/about/about_execution_policies)이 설정되어야 합니다.

## <a name="see-also"></a>추가 정보

- [개발자 PowerShell](https://devblogs.microsoft.com/visualstudio/the-powershell-you-know-and-love-now-with-a-side-of-visual-studio/)
- [새 Visual Studio 터미널 시작](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/)
- [Windows 터미널](/windows/terminal/)
- [.NET Framework 도구](/dotnet/framework/tools/index)
- [외부 도구 관리](../managing-external-tools.md)
- [명령줄에서 Microsoft C++ 도구 집합 사용](/cpp/build/building-on-the-command-line)
