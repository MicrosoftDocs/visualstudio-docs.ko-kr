---
title: 디버깅 중에 .NET 코드 디컴파일 | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508747"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>디버깅 중에 .NET 어셈블리에서 소스 코드 생성

.NET 애플리케이션을 디버깅할 때 없는 소스 코드를 확인할 수 있습니다. 예를 들어 예외를 중단하거나 호출 스택을 사용하여 소스 위치로 이동합니다.

> [!NOTE]
> * 소스 코드 생성(디컴파일)은 .NET 애플리케이션에만 사용할 수 있으며 오픈 소스 [ILSpy](https://github.com/icsharpcode/ILSpy) 프로젝트를 기반으로 합니다.
> * 디컴파일은 Visual Studio 2019 16.5 이상에서만 사용할 수 있습니다.
> * 어셈블리 또는 모듈에 [SuppressIldasmAttribute](https://docs.microsoft.com/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) 특성을 적용하면 Visual Studio에서 디컴파일을 시도할 수 없습니다.

## <a name="generate-source-code"></a>소스 코드 생성

디버깅 중에 소스 코드를 사용할 수 없는 경우 Visual Studio에 **소스를 찾을 수 없음** 문서가 표시되거나 어셈블리에 대한 기호가 없는 경우 **로드된 기호가 없음** 문서가 표시됩니다. 두 문서에는 현재 위치에 대한 C# 코드를 생성하는 **디컴파일 소스 코드** 옵션이 있습니다. 생성된 C# 코드를 다른 소스 코드와 마찬가지로 사용할 수 있습니다. 코드 보기, 변수 검사, 중단점 설정 등을 할 수 있습니다.

### <a name="no-symbols-loaded"></a>로드된 기호 없음

다음 그림에서는 **로드된 기호 없음** 메시지를 보여줍니다.

![로드된 기호가 없는 문서의 스크린샷](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>소스를 찾을 수 없음

다음 그림에서는 **소스를 찾을 수 없음** 메시지를 보여줍니다.

![소스를 찾을 수 없는 문서의 스크린샷](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>어셈블리에 대한 소스 생성 및 포함

특정 위치에 대한 소스 코드를 생성하는 것 외에도 지정된 .NET 어셈블리에 대한 소스 코드를 모두 생성할 수 있습니다. 이렇게 하려면 **모듈** 창과 .NET 어셈블리의 바로 가기 메뉴에서 **소스 코드 디컴파일** 명령을 선택합니다. Visual Studio에서는 어셈블리에 대한 기호 파일을 생성한 다음, 소스를 기호 파일에 포함합니다. 이후 단계에서 포함된 소스 코드를 [추출](#extract-and-view-the-embedded-source-code)할 수 있습니다.

![디컴파일 소스 명령이 있는 모듈 창의 어셈블리 바로 가기 메뉴 스크린샷.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>포함된 소스 코드 추출 및 보기

**모듈** 창의 바로 가기 메뉴에서 **소스 코드 추출** 명령을 사용하여 기호 파일에 포함된 소스 파일을 추출할 수 있습니다.

![추출 소스 명령이 있는 모듈 창의 어셈블리 바로 가기 메뉴 스크린샷.](media/decompilation-extract-source-code.png)

추출된 소스 파일은 [기타 파일](../ide/reference/miscellaneous-files.md)로 솔루션에 추가됩니다. 기타 파일 기능은 Visual Studio에서 기본적으로 해제되어 있습니다. **도구** > **옵션** > **환경** > **문서** > **솔루션 탐색기에서 기타 파일 표시** 확인란에서 이 기능을 사용하도록 설정할 수 있습니다. 이 기능을 활성화하지 않으면 추출된 소스 코드를 열 수 없습니다.

![기타 파일 옵션이 활성화된 도구 옵션 페이지의 스크린샷.](media/decompilation-tools-options-misc-files.png)

추출된 소스 파일은 **솔루션 탐색기**의 기타 파일에 표시됩니다.

![기타 파일이 있는 솔루션 탐색기의 스크린샷.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>알려진 제한 사항

### <a name="requires-break-mode"></a>중단 모드 필요

디버거가 중단 모드에 있고 애플리케이션이 일시 중지된 경우에만 디컴파일을 사용하여 소스 코드를 생성할 수 있습니다. 예를 들어 Visual Studio는 중단점 또는 예외에 도달할 때 중단 모드로 전환됩니다. **모두 중단** 명령(![모두 중단 아이콘](media/decompilation-break-all.png))을 사용하여 다음에 코드를 실행할 때 Visual Studio를 쉽게 트리거할 수 있습니다.

### <a name="decompilation-limitations"></a>디컴파일 제한 사항

.NET 어셈블리에 사용되는 중간 형식(IL)에서 소스 코드를 생성하는 데는 몇 가지 고유 제한 사항이 있습니다. 따라서 생성된 소스 코드는 원래 소스 코드와 같지 않습니다. 대부분의 차이점은 런타임에 원래 소스 코드의 정보가 필요하지 않은 위치에 있습니다. 예를 들어 공백, 주석 및 지역 변수 이름과 같은 정보는 런타임에 필요하지 않습니다. 원래 소스 코드를 대체하는 것이 아니라 생성된 소스를 사용하여 프로그램이 실행되는 방식을 이해하는 것이 좋습니다.

### <a name="debug-optimized-or-release-assemblies"></a>최적화된 어셈블리 또는 릴리스 어셈블리 디버그

컴파일러 최적화를 사용하여 컴파일된 어셈블리에서 디컴파일된 코드를 디버깅할 때 다음과 같은 문제가 발생할 수 있습니다.
- 중단점은 일치하는 소싱 위치에 항상 바인딩할 수 없습니다.
- 단계별 실행은 항상 올바른 위치로 이동하지 않을 수 있습니다.
- 지역 변수의 이름이 정확하지 않을 수 있습니다.
- 일부 변수는 평가에 사용할 수 없습니다.

자세한 내용은 GitHub 문제에서 찾을 수 있습니다. [ICSharpCode.Decompiler를 VS 디버거로 통합](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>디컴파일 안정성

디컴파일 시도가 상대적으로 적으면 실패할 수 있습니다. 이는 ILSpy의 시퀀스 포인트 null 참조 오류 때문입니다.  이러한 문제를 포착하고 디컴파일 시도를 정상적으로 실패함으로써 오류를 완화했습니다.

자세한 내용은 GitHub 문제에서 찾을 수 있습니다. [ICSharpCode.Decompiler를 VS 디버거로 통합](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>비동기 코드의 제한 사항

비동기/대기 코드 패턴이 있는 디컴파일 모듈의 결과가 완전하지 않거나 실패할 수 있습니다. 비동기/대기 및 yield 상태 머신의 ILSpy 구현은 부분적으로만 구현됩니다. 

자세한 내용은 GitHub 문제에서 찾을 수 있습니다. [PDB 생성기 상태](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>내 코드만

[JMC(내 코드만)](https://docs.microsoft.com/visualstudio/debugger/just-my-code) 설정을 통해 Visual Studio에서 시스템, 프레임워크, 라이브러리 및 기타 비사용자 호출을 한 단계씩 실행할 수 있습니다. 디버깅 세션 중에 **모듈** 창에는 디버거가 내 코드(사용자 코드)로 취급하는 코드 모듈이 표시됩니다.

최적화된 모듈 또는 릴리스 모듈을 디컴파일하면 비사용자 코드가 생성됩니다. 예를 들어 디버거가 디컴파일된 비사용자 코드에서 중단되면 **소스 없음** 창이 나타납니다. 내 코드만을 사용하지 않도록 설정하려면 **도구** > **옵션**(또는 **디버그** > **옵션**) > **디버깅** > **일반**으로 이동한 다음, **내 코드만 사용**을 선택 취소합니다.

### <a name="extracted-sources"></a>추출된 소스

어셈블리에서 추출된 소스 코드에는 다음과 같은 제한 사항이 있습니다.
- 생성된 파일의 이름과 위치는 구성할 수 없습니다.
- 파일은 일시적이며 Visual Studio에서 삭제됩니다.
- 파일은 단일 폴더에 배치되며 원래 소스가 가지고 있던 폴더 계층은 사용되지 않습니다.
- 각 파일의 파일 이름에는 파일의 체크섬 해시가 포함되어 있습니다.

### <a name="generated-code-is-c-only"></a>생성된 코드는 C# 전용입니다.
디컴파일은 C#에서만 소스 코드 파일을 생성합니다. 다른 언어로 파일을 생성하는 옵션은 없습니다.
