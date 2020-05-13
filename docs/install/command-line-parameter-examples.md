---
title: 설치에 대한 명령줄 매개 변수 예제
description: 이러한 예제를 사용자 지정하여 Visual Studio의 고유한 명령줄 설치를 만듭니다.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8fc43cef8526b2ca79bb0b88a1d56ef4f4a2a65a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275259"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Visual Studio 설치에 대한 명령줄 매개 변수 예

[명령줄 매개 변수를 사용하여 Visual Studio를 설치](use-command-line-parameters-to-install-visual-studio.md)하는 방법을 보여 주기 위해 사용자의 요구에 맞게 사용자 지정할 수 있는 몇 가지 예를 제공합니다.

각 예에서 `vs_enterprise.exe`, `vs_professional.exe` 및 `vs_community.exe`는 다운로드 프로세스를 시작하는 1MB 정도 크기의 작은 파일인 Visual Studio 부트스트래퍼의 해당 버전을 나타냅니다. 다른 버전을 사용하는 경우에는 적절한 부트스트래퍼 이름으로 대체합니다.

> [!NOTE]
> 모든 명령에는 관리자 권한 상승이 필요하며 상승된 프롬프트에서 프로세스가 시작되지 않는 경우 사용자 계정 컨트롤 프롬프트가 표시됩니다.
>
> [!NOTE]
> 명령줄의 끝에 `^` 문자를 사용하여 여러 줄을 하나의 명령으로 연결할 수 있습니다. 또는 이러한 줄을 한꺼번에 단일 행에 배치할 수도 있습니다. PowerShell에서 일치하는 항목은 억음 악센트(`` ` ``) 문자입니다.

명령줄을 사용하여 설치할 수 있는 워크로드 및 구성 요소 목록은 [Visual Studio 워크로드 및 구성 요소 ID](workload-and-component-ids.md) 페이지를 참조하세요.

## <a name="using---installpath"></a>--installPath 사용

* 대화형 프롬프트 없이 진행률이 표시되는 Visual Studio의 최소 인스턴스를 설치합니다.

  ```cmd
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* 대화형 프롬프트 없이 진행률이 표시되는 명령줄을 사용하여 Visual Studio 인스턴스를 업데이트합니다.

   ```cmd
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > 두 명령 모두 사용하는 것이 좋습니다. 첫 번째 명령은 Visual Studio 설치 관리자를 업데이트합니다. 두 번째 명령은 Visual Studio 인스턴스를 업데이트합니다. [사용자 계정 컨트롤] 대화 상자를 사용하지 않으려면 명령 프롬프트를 관리자 권한으로 실행합니다.

* 제품을 설치해야만 반환되는 프랑스어 언어 팩을 포함한 Visual Studio의 데스크톱 인스턴스를 자동으로 설치합니다.

  ```cmd
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>--wait 사용

* 배치 파일 또는 스크립트에서 다음 명령을 실행하기 전에 Visual Studio 설치 관리자가 완료될 때까지 기다리는 데 사용합니다. 일괄 처리 파일의 경우 `%ERRORLEVEL%`명령줄 매개 변수를 사용하여 Visual Studio 설치[ 페이지에 나오는 대로 ](use-command-line-parameters-to-install-visual-studio.md) 환경 변수가 명령의 반환 값을 포함합니다. 일부 명령 유틸리티는 추가 매개 변수가 있어야 완료될 때까지 기다리고 설치 관리자의 반환 값을 가져올 수 있습니다. 다음은 PowerShell 스크립트 명령 ‘Start-Process’와 함께 사용되는 추가 매개 변수에 대한 예제입니다.

   ```cmd
   start /wait vs_professional.exe --installPath "C:\VS" --passive --wait > nul
   echo %errorlevel%
   ```

   ```powershell
   $exitCode = Start-Process -FilePath vs_enterprise.exe -ArgumentList "--installPath", "C:\VS", "--passive", "--wait" -Wait -PassThru
   ```

   또는

   ```powershell
    $startInfo = New-Object System.Diagnostics.ProcessStartInfo
    $startInfo.FileName = "vs_enterprise.exe"
    $startInfo.Arguments = "--all --quiet --wait"
    $process = New-Object System.Diagnostics.Process
    $process.StartInfo = $startInfo
    $process.Start()
    $process.WaitForExit()
   ```

* 첫 번째 ‘--wait’는 Visual Studio 설치 관리자에서 사용되며, 두 번째 ‘-Wait’는 ‘Start-Process’에서 완료될 때까지 기다리는 데 사용됩니다. ‘-PassThru’ 매개 변수는 ‘Start-Process’에서 해당 반환 값의 설치 관리자 종료 코드를 사용하는 데 필요합니다.

## <a name="using---layout"></a>--layout 사용

* Visual Studio 핵심 편집기를 다운로드합니다(최소한의 Visual Studio 구성). 영어 언어 팩만 포함:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* .NET 데스크톱 및 .NET 웹 워크로드를 모든 권장 구성 요소 및 GitHub 확장명과 함께 다운로드합니다. 영어 언어 팩만 포함:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>--all 사용

* Visual Studio Enterprise Edition에서 사용할 수 있는 모든 워크로드 및 구성 요소의 대화형 설치를 시작합니다.

   ```cmd
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>--includeRecommended 사용

* Node.js 개발 지원을 통해 Visual Studio Community 버전이 이미 설치된 머신에 Visual Studio Professional의 두 번째 명명된 인스턴스를 설치합니다.

   ```cmd
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>--remove 사용

::: moniker range="vs-2017"

* 기본 설치된 Visual Studio 인스턴스에서 프로파일링 도구 구성 요소를 제거합니다.

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* 기본 설치된 Visual Studio 인스턴스에서 프로파일링 도구 구성 요소를 제거합니다.

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>--path 사용

::: moniker range="vs-2017"

이러한 명령줄 매개 변수는 **15.7의 새로운 기능**입니다. 이에 대한 자세한 내용은 [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md) 페이지를 참조하세요.

::: moniker-end

* 설치, 캐시 및 공유 경로 사용:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* 설치 및 캐시 경로만 사용:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* 설치 및 공유 경로만 사용:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* 설치 경로만 사용:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>내보내기 사용

::: moniker range="vs-2017"

이 명령줄 명령은 **15.9의 새 기능**입니다. 이에 대한 자세한 내용은 [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md) 페이지를 참조하세요.

::: moniker-end

* 내보내기를 사용하여 설치에서 선택 사항을 저장합니다.

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* 내보내기를 사용하여 사용자 지정 선택 사항을 처음부터 저장합니다.

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>--Config 사용

::: moniker range="vs-2017"

이 명령줄 매개 변수는 **15.9의 새 기능**입니다. 이에 대한 자세한 내용은 [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md) 페이지를 참조하세요.

::: moniker-end

* --config를 사용하여 이전에 저장한 설치 구성 파일에서 워크로드 및 구성 요소를 설치합니다.

  ```cmd
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* --config를 사용하여 기존 설치에 워크로드 및 구성 요소를 추가합니다.

  ```cmd
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
* [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio의 오프라인 설치 만들기](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio 작업 및 구성 요소 ID](workload-and-component-ids.md)
