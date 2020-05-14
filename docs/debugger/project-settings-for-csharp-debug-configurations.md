---
title: C# 디버그 구성에 대한 프로젝트 설정 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5108e195e5df245c72436752316e8ee91781e7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62904064"
---
# <a name="project-settings-for--c-debug-configurations"></a>C# 디버그 구성을 위한 프로젝트 설정

프로젝트 속성 페이지의 [디버그 탭](#debug-tab) 및 [빌드 탭](#build-tab)에서 C# 프로젝트 디버그 설정을 변경할 수 있습니다.

속성 페이지를 열려면 **솔루션 탐색기**에서 C/C++ DLL 프로젝트를 선택한 다음 **속성** 아이콘을 선택하거나 프로젝트를 마우스 오른쪽 단추로 클릭하여 **속성**을 선택합니다.

자세한 내용은 [디버그 및 릴리스 구성](how-to-set-debug-and-release-configurations.md)을 참조하세요.

>[!IMPORTANT]
>이러한 설정은 .NET Core, ASP.NET 또는 UWP 앱에 적용되지 않습니다. UWP 앱에 대한 디버그 설정을 구성하려면 [UWP 앱에 대한 디버깅 세션 시작](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)을 참조하세요.

## <a name="debug-tab"></a>디버그 탭

|설정|설명|
|-------------------------------------| - |
| **구성** | 앱을 빌드하기 위한 모드를 설정합니다. 드롭다운 목록에서 **활성(디버그)** , **디버그**, **릴리스**, 또는 **모든 구성**을 선택합니다. |
| **시작 작업** | 디버그 구성에서 **시작**을 선택하는 경우 작업을 지정합니다.<br />기본값인 - **시작 프로젝트**를 선택하면 디버깅을 위한 시작 프로젝트가 실행됩니다. 자세한 내용은 [시작 프로젝트 선택](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100))을 참조하세요.<br />- **외부 프로그램 시작**은 시작하고 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로젝트의 일부가 아닌 앱에 연결합니다. 자세한 내용은 [디버거를 사용하여 실행 중인 프로세스에 연결](attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조하세요.<br />- **URL를 사용하여 브라우저를 시작**을 사용하여 웹앱을 디버그할 수 있습니다. |
| **시작 옵션** > **명령줄 인수** | 디버깅될 앱에 대한 명령줄 인수를 지정합니다. 명령 이름은 **시작 외부 프로그램**에 지정된 앱 이름입니다. |
| **시작 옵션** > **작업 디렉터리** | 디버깅 중인 앱의 작업 디렉터리를 지정합니다. C#에서 작업 디렉터리는 기본적으로 *\bin\debug*입니다.
| **시작 옵션** > **원격 컴퓨터 사용**|원격 디버깅의 경우 이 옵션을 선택하고 원격 디버깅 대상의 이름을 입력하거나 [Msvsmon 서버 이름](../debugger/remote-debugging.md)을 입력합니다. <br />원격 컴퓨터에 있는 앱의 위치는 **빌드** 탭에 있는 **출력 경로** 속성으로 지정됩니다. 이 위치는 원격 컴퓨터의 공유할 수 있는 디렉터리여야 합니다.
| **디버거 엔진** > **비관리 코드 디버깅 사용** | 관리형 앱에서 네이티브(비관리) Win32 코드에 대한 호출을 디버깅합니다. |
| **디버거 엔진** > **디버깅 SQL Server 사용** | SQL Server 데이터베이스 개체를 디버그합니다. |

## <a name="build-tab"></a>빌드 탭

|설정|설명|
|-------------|-----------------|
|**일반** > **조건부 컴파일 기호:**|선택한 경우 DEBUG 및 TRACE 상수를 정의합니다.<br /><br /> 이 상수를 사용하면 조건에 따라 [Debug 클래스](/dotnet/api/system.diagnostics.debug)와 [Trace 클래스](/dotnet/api/system.diagnostics.trace)를 컴파일할 수 있습니다. 이 상수를 정의하면 Debug 및 Trace 클래스 메서드의 결과가 [출력 창](../ide/reference/output-window.md)에 표시됩니다. 이 상수를 정의하지 않으면 Debug 및 Trace 클래스 메서드가 컴파일되지 않으므로 결과가 생성되지 않습니다.<br /><br />Debug 상수는 일반적으로 빌드의 디버그 버전에 정의되고 릴리스 버전에는 정의되지 않습니다. TRACE는 일반적으로 디버그 및 릴리스 버전에 모두 정의됩니다.|
|**일반** > **코드 최적화**|버그가 최적화된 코드에만 표시되는 경우를 제외하고 디버그 빌드에 대해서는 이 설정을 선택하지 않은 상태로 둡니다. 코드를 최적화하면 명령이 소스 코드에 있는 문에 직접 대응되지 않기 때문에 디버깅하기 어렵습니다.|
|**출력** > **출력 경로**|디버깅 작업에서는 일반적으로 *bin\Debug*로 설정합니다.|
|**고급** 단추|고급 디버깅 옵션에 대한 자세한 내용은 [고급 빌드 설정 대화 상자(C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)를 참조하세요. 기호( *.pdb*) 파일에 대한 이식 가능한 형식은 .NET Core 앱에 대한 최신 플랫폼 간 형식입니다.

## <a name="see-also"></a>참조
- [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)