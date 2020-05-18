---
title: JIT 최적화 및 디버깅 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae11860aaa64448cd4d23b5602cf4c2da1575ce3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916209"
---
# <a name="jit-optimization-and-debugging"></a>JIT 최적화 및 디버깅
코드를 디버그하려는 경우 코드가 최적화되지 **않은** 상태에서 더 쉽습니다. 코드가 최적화되면 컴파일러 및 런타임이 생성된 CPU 코드를 변경하여 더 빠르게 실행되지만 원래 소스 코드에 대하여 덜 직접적으로 매핑합니다. 매핑이 덜 직접적인 경우 디버거는 지역 변수의 값을 알 수 없는 경우가 많으며 단계별 코드 실행 및 중단점이 정상적으로 작동하지 않을 수 있습니다.

> [!NOTE]
> JIT(Just-In-Time) 디버깅에 대한 자세한 내용은 [이 설명서](../debugger/debug-using-the-just-in-time-debugger.md)를 참조하세요.

## <a name="how-optimizations-work-in-net"></a>.NET에서 최적화가 작동하는 방식 
일반적으로 릴리스 빌드 구성은 최적화된 코드를 만들고 디버그 빌드 구성은 그렇지 않습니다. `Optimize` MSBuild 속성은 컴파일러에게 코드를 최적화하도록 지시하는지 여부를 제어합니다.

.NET 에코시스템에서 코드는 2단계 프로세스를 거쳐 소스에서 CPU 명령으로 전환됩니다. 먼저 C# 컴파일러가 입력한 텍스트를 MSIL이라는 중간 이진 형식으로 변환하고 MSIL을 .dll 파일에 씁니다. 나중에 .NET 런타임에서 이 MSIL을 CPU 명령으로 변환합니다. 두 단계 모두 일정 수준까지 최적화할 수 있지만 .NET 런타임이 수행하는 두 번째 단계에서 더 중요한 최적화가 이루어집니다.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>'모듈을 로드할 때 JIT 최적화 기능 사용 안 함(관리 전용)' 옵션
디버거는 최적화를 사용하여 컴파일된 DLL이 대상 프로세스 내에서 로드될 때 발생하는 작업을 제어하는 옵션을 제공합니다. 이 옵션을 선택하지 않으면(기본 상태) .NET 런타임이 MSIL 코드를 CPU 코드로 컴파일할 때 최적화를 사용합니다. 이 옵션을 선택하면 디버거가 최적화를 사용하지 않도록 요청합니다.

**모듈을 로드할 때 JIT 최적화 기능 사용 안 함(관리 전용)** 옵션을 찾으려면 **도구** > **옵션**을 선택한 다음 **디버깅** 노드 아래에서 **일반** 페이지를 선택합니다.

![JIT 최적화 기능 사용 안 함](../debugger/media/suppress-jit-tool-options.png "JIT 최적화 기능 사용 안 함")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>'JIT 최적화 기능 사용 안 함' 옵션은 언제 선택해야 할까요?
NuGet 패키지와 같은 다른 소스에서 DLL을 다운로드하고 이 DLL의 코드를 디버그하려는 경우 이 옵션을 선택합니다. 사용 안 함 옵션이 유효하려면 이 DLL에 대한 기호(.pdb) 파일도 찾아야 합니다.

로컬로 빌드하는 코드를 디버그하려는 경우에만 이 옵션을 사용하지 않는 것이 가장 좋습니다. 이 옵션을 사용하도록 설정하면 디버깅이 크게 느려질 수 있습니다. 여기에는 두 가지 이유가 있습니다.

* 최적화된 코드는 더 빠르게 실행됩니다. 많은 코드에 대한 최적화를 해제하는 경우 성능 영향이 증가할 수 있습니다.
* 내 코드만이 사용하도록 설정된 경우 디버거는 최적화된 DLL에 대해 기호를 로드할 시도조차 하지 않습니다. 기호 찾기는 시간이 오래 걸릴 수 있습니다.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>'JIT 최적화 기능 사용 안 함' 옵션 제한 사항 
이 옵션을 설정하는 것이 유효하지 **않은** 두 가지 상황이 있습니다.

1. 디버거를 이미 실행 중인 프로세스에 연결하는 경우 디버거가 연결될 때 이미 로드된 모듈에는 이 옵션이 적용되지 않습니다.
2. 이 옵션은 네이티브 코드에 미리 컴파일된(즉 NGen이 실행된) DLL에는 영향을 주지 않습니다. 그러나 **'COMPlus_ReadyToRun'** 환경 변수를 **'0'** 으로 설정하고 프로세스를 시작하여 미리 컴파일된 코드의 사용을 비활성화할 수 있습니다. 이렇게 하면 .NET Core 런타임에 미리 컴파일된 이미지를 사용하지 않도록 지시하여 런타임을 강제로 JIT 컴파일 프레임워크 코드에 적용합니다. 

    > [!IMPORTANT]
    > .NET Framework 또는 이전 버전의 .NET Core(2.x 이하)를 대상으로 하는 경우 환경 변수 'COMPlus_ZapDisable'도 추가하고 '1'로 설정합니다.

    **Visual Studio에서 .NET Core 프로젝트에 대한 환경 변수를 설정하려면**
    1. **솔루션 탐색기**에서 프로젝트 파일을 **마우스 오른쪽 단추로 클릭**하고 **속성**을 선택합니다.
    2. **디버그** 탭으로 이동하고 **환경 변수**에서 **추가** 단추를 클릭합니다.
    3. 이름(키)을 **COMPlus_ReadyToRun**으로 설정하고 값을 **0**으로 설정합니다.

    ![COMPlus_ReadyToRun 환경 변수 설정](../debugger/media/environment-variables-debug-menu.png "COMPlus_ReadyToRun 환경 변수 설정")

## <a name="see-also"></a>참조
- [Dotnet Framework 소스를 디버그하는 방법](../debugger/how-to-debug-dotnet-framework-source.md)
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [디버거로 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)
- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [관리되는 실행 프로세스](/dotnet/standard/managed-execution-process)
