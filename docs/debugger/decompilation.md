---
title: 디버깅 하는 동안 .NET 코드 디컴파일 | 마이크로 소프트 문서
ms.date: 2/2/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: d63c05120842d52dd54359e128d0cc5f2a195817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508747"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>디버깅하는 동안 .NET 어셈블리에서 소스 코드 생성

.NET 응용 프로그램을 디버깅할 때 가지고 있지 않은 소스 코드를 보려는 경우가 있습니다. 예를 들어 예외를 끊거나 호출 스택을 사용하여 원본 위치로 이동합니다.

> [!NOTE]
> * 소스 코드 생성(디컴파일)은 .NET 응용 프로그램에서만 사용할 수 있으며 오픈 소스 [ILSpy](https://github.com/icsharpcode/ILSpy) 프로젝트를 기반으로 합니다.
> * 디컴파일은 Visual Studio 2019 16.5 이상에서만 사용할 수 있습니다.
> * 어셈블리 또는 모듈에 [SuppressIldasmAttribute 특성을](https://docs.microsoft.com/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) 적용하면 Visual Studio에서 디컴파일을 시도하지 않습니다.

## <a name="generate-source-code"></a>소스 코드 생성

디버깅 중이고 소스 코드를 사용할 수 없는 경우 Visual Studio에서 **찾을 수 없는 원본** 문서를 표시하거나 어셈블리에 대한 기호가 없는 경우 기호 로드되지 않은 문서가 **표시됩니다.** 두 문서 모두 현재 위치에 대한 C# 코드를 생성하는 **디컴파일 소스 코드** 옵션이 있습니다. 그런 다음 생성된 C# 코드를 다른 소스 코드와 마찬가지로 사용할 수 있습니다. 코드를 보고, 변수를 검사하고, 중단점을 설정하는 등의 등을 수행할 수 있습니다.

### <a name="no-symbols-loaded"></a>로드된 기호 없음

다음 그림에서는 기호 로드 없음 메시지를 보여 **주며 있습니다.**

![기호로드 문서의 스크린 샷](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>소스를 찾을 수 없습니다.

다음 그림에서는 **찾을 수 없는 소스** 메시지를 보여 주실 수 있습니다.

![찾을 수 없는 문서의 스크린샷](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>어셈블리에 대한 소스 생성 및 포함

특정 위치에 대한 소스 코드를 생성하는 것 외에도 지정된 .NET 어셈블리에 대한 모든 소스 코드를 생성할 수 있습니다. 이렇게 하려면 **모듈** 창및 .NET 어셈블리의 컨텍스트 메뉴로 이동한 다음 **디컴파일 소스 코드** 명령을 선택합니다. Visual Studio는 어셈블리에 대한 기호 파일을 생성한 다음 소스를 심볼 파일에 포함시됩니다. 이후 단계에서는 포함된 소스 코드를 [추출할](#extract-and-view-the-embedded-source-code) 수 있습니다.

![디컴파일 소스 명령이 있는 모듈 창에서 어셈블리 컨텍스트 메뉴의 스크린샷입니다.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>포함된 소스 코드 추출 및 보기

모듈 창의 컨텍스트 메뉴에서 소스 코드 **추출** 명령을 사용하여 기호 파일에 포함된 원본 파일을 추출할 수 **있습니다.**

![추출 소스 명령이 있는 모듈 창에서 어셈블리 컨텍스트 메뉴의 스크린샷입니다.](media/decompilation-extract-source-code.png)

추출된 소스 파일은 [솔루션에 기타 파일로](../ide/reference/miscellaneous-files.md)추가됩니다. 기타 파일 기능은 Visual Studio에서 기본적으로 꺼져 있습니다. **도구** > **옵션** > **환경** > **문서에서** > 이 기능을 활성화할 수**있습니다솔루션 탐색기 확인란에서 기타 파일 표시.** 이 기능을 사용하도록 설정하지 않으면 추출된 소스 코드를 열 수 없습니다.

![기타 파일 옵션을 사용하도록 설정한 도구 옵션 페이지의 스크린샷입니다.](media/decompilation-tools-options-misc-files.png)

추출된 원본 파일은 **솔루션 탐색기**의 기타 파일에 나타납니다.

![기타 파일이 있는 솔루션 탐색기의 스크린샷입니다.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>알려진 제한 사항

### <a name="requires-break-mode"></a>브레이크 모드 필요

디버거가 중단 모드에 있고 응용 프로그램이 일시 중지된 경우에만 디컴파일을 사용하여 소스 코드를 생성할 수 있습니다. 예를 들어 Visual Studio는 중단점이나 예외에 도달하면 중단 모드로 들어갑니다. 모든 **모든 작업 중단** 명령(모든![아이콘](media/decompilation-break-all.png)나누기)을 사용하여 다음에 코드가 실행될 때 Visual Studio를 쉽게 트리거할 수 있습니다.

### <a name="decompilation-limitations"></a>디컴파일 제한 사항

.NET 어셈블리에 사용되는 중간 형식(IL)에서 소스 코드를 생성하는 방법에는 몇 가지 고유한 제한이 있습니다. 따라서 생성된 소스 코드는 원래 소스 코드와 같지 않습니다. 대부분의 차이점은 런타임에 원래 소스 코드의 정보가 필요하지 않은 위치에 있습니다. 예를 들어 런타임에 공백, 주석 및 지역 변수의 이름과 같은 정보는 필요하지 않습니다. 생성된 소스를 사용하여 프로그램이 실행되는 방식을 이해하는 것이지 원래 소스 코드를 대체하는 것이 아니라는 점을 이해하는 것이 좋습니다.

### <a name="debug-optimized-or-release-assemblies"></a>디버그 최적화 또는 릴리스 어셈블리

컴파일러 최적화를 사용하여 컴파일된 어셈블리에서 디컴파일된 코드를 디버깅할 때 다음과 같은 문제가 발생할 수 있습니다.
- 중단점이 항상 일치하는 소싱 위치에 바인딩되지 않을 수 있습니다.
- 스테핑이 항상 올바른 위치로 이동하지 않을 수 있습니다.
- 지역 변수에는 정확한 이름이 없을 수 있습니다.
- 일부 변수는 평가에 사용할 수 없을 수 있습니다.

자세한 내용은 GitHub 문제에서 찾을 수 있습니다: [ICSharpCode.De컴파일러 VS 디버거에 통합](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>분해 신뢰성

디컴파일 시도의 비율이 상대적으로 적으면 실패할 수 있습니다. 이는 ILSpy의 시퀀스 포인트 null-참조 오류 때문입니다.  이러한 문제를 파악하고 디컴파일 시도를 정상적으로 실패하여 오류를 완화했습니다.

자세한 내용은 GitHub 문제에서 찾을 수 있습니다: [ICSharpCode.De컴파일러 VS 디버거에 통합](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>비동기 코드의 제한 사항

비동기/await 코드 패턴이 있는 모듈을 디컴파일한 결과는 불완전하거나 완전히 실패할 수 있습니다. 비동기/await 및 yield 상태 컴퓨터의 ILSpy 구현은 부분적으로만 구현됩니다. 

자세한 내용은 GitHub 문제에서 찾을 수 있습니다: [PDB 생성기 상태.](https://github.com/icsharpcode/ILSpy/issues/1422)

### <a name="just-my-code"></a>내 코드만

[JMC(저함 내 코드)](https://docs.microsoft.com/visualstudio/debugger/just-my-code) 설정을 사용하면 Visual Studio에서 시스템, 프레임워크, 라이브러리 및 기타 비사용자 호출을 단계별로 수행할 수 있습니다. 디버깅 세션 중에 **모듈** 창에는 디버거가 내 코드(사용자 코드)로 취급하는 코드 모듈이 표시됩니다.

최적화된 또는 릴리스 모듈의 분해는 비사용자 코드를 생성합니다. 디버거가 디컴파일된 비사용자 코드에서 중단되는 경우(예: **소스 없음)** 창이 나타납니다. 내 코드만 비활성화하려면 **도구** > **옵션(또는** **디버그** > **옵션)>** **일반 디버깅으로 이동한** > **General**다음 내 코드 만 **사용하도록 선택**해제합니다.

### <a name="extracted-sources"></a>추출된 소스

어셈블리에서 추출된 소스 코드에는 다음과 같은 제한 사항이 있습니다.
- 생성된 파일의 이름과 위치는 구성할 수 없습니다.
- 파일은 일시적이며 Visual Studio에서 삭제됩니다.
- 파일은 단일 폴더에 배치되며 원래 원본이 사용한 폴더 계층 구조가 사용되지 않습니다.
- 각 파일의 파일 이름에는 파일의 체크섬 해시가 포함되어 있습니다.

### <a name="generated-code-is-c-only"></a>생성된 코드는 C#입니다.
디컴파일은 C#에서만 소스 코드 파일을 생성합니다. 다른 언어로 파일을 생성하는 옵션은 없습니다.
