---
title: 디버깅 하는 동안 .NET 코드를 디컴파일 합니다. | Microsoft Docs
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
ms.openlocfilehash: 46c6110cb977e3a309f27fc5a014522494f18c9a
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77506518"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>디버깅 하는 동안 .NET 어셈블리에서 소스 코드 생성

.NET 응용 프로그램을 디버깅 하는 경우에는 없는 소스 코드를 확인할 수 있습니다. 예를 들어 예외를 위반 하거나 호출 스택을 사용 하 여 소스 위치로 이동 합니다.

> [!NOTE]
> * 디컴파일을 (소스 코드 생성)는 .NET 응용 프로그램에만 사용할 수 있으며 오픈 소스 [Ilspy](https://github.com/icsharpcode/ILSpy) 프로젝트를 기반으로 합니다.
> * 디컴파일을는 Visual Studio 2019 16.5 이상 에서만 사용할 수 있습니다.

## <a name="generate-source-code"></a>소스 코드 생성

디버깅 하는 동안 소스 코드를 사용할 수 없는 경우 Visual Studio는 **소스를 찾을** 수 없음 문서를 표시 하거나, 어셈블리에 대 한 기호가 없는 경우 **로드 된 기호 없음** 문서를 표시 합니다. 두 문서에는 현재 위치에 대 한 코드 C# 를 생성 하는 **디컴파일 소스 코드** 옵션이 있습니다. 그러면 생성 C# 된 코드를 다른 소스 코드와 마찬가지로 사용할 수 있습니다. 코드를 확인 하 고, 변수를 검사 하 고, 중단점을 설정 하는 등의 방법을 사용할 수 있습니다.

### <a name="no-symbols-loaded"></a>기호가 로드 되지 않았습니다.

다음 그림에서는 로드 된 **기호 없음** 메시지를 보여 줍니다.

![로드 된 기호 없는 문서 스크린샷](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>소스를 찾을 수 없음

다음 그림에서는 **원본 찾을 수 없음** 메시지를 보여 줍니다.

![소스를 찾을 수 없음 문서의 스크린샷](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>어셈블리에 대 한 소스 생성 및 포함

특정 위치에 대 한 소스 코드를 생성 하는 것 외에도 지정 된 .NET 어셈블리에 대 한 소스 코드를 모두 생성할 수 있습니다. 이렇게 하려면 **모듈** 창과 .net 어셈블리의 상황에 맞는 메뉴에서 **디컴파일 소스 코드** 명령을 선택 합니다. Visual Studio에서는 어셈블리에 대 한 기호 파일을 생성 한 다음 소스를 기호 파일에 포함 합니다. 이후 단계에서 포함 된 소스 코드를 [추출할](#extract-and-view-the-embedded-source-code) 수 있습니다.

![디컴파일 원본 명령이 있는 모듈 창에서 어셈블리 상황에 맞는 메뉴의 스크린샷](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>포함 된 소스 코드 추출 및 보기

**모듈** 창의 상황에 맞는 메뉴에서 **소스 코드 추출** 명령을 사용 하 여 기호 파일에 포함 된 소스 파일을 추출할 수 있습니다.

![소스 추출 명령이 있는 모듈 창에서 어셈블리 상황에 맞는 메뉴의 스크린샷](media/decompilation-extract-source-code.png)

추출 된 소스 파일이 [기타 파일로](../ide/reference/miscellaneous-files.md)솔루션에 추가 됩니다. Visual Studio에서는 기타 파일 기능이 기본적으로 해제 되어 있습니다. **도구** > **옵션** > **환경** > **문서** 에서이 기능을 사용 하도록 설정 하 > **솔루션 탐색기에 기타 파일 표시** 확인란을 선택할 수 있습니다. 이 기능을 사용 하지 않으면 추출 된 소스 코드를 열 수 없습니다.

![기타 파일 옵션이 설정 된 도구 옵션 페이지의 스크린샷](media/decompilation-tools-options-misc-files.png)

추출 된 소스 파일은 **솔루션 탐색기**의 기타 파일에 표시 됩니다.

![기타 파일이 포함 된 솔루션 탐색기의 스크린샷](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>알려진 제한 사항

### <a name="requires-break-mode"></a>중단 모드 필요

디버거가 중단 모드에 있고 응용 프로그램이 일시 중지 된 경우에만 디컴파일을를 사용 하 여 소스 코드를 생성할 수 있습니다. 예를 들어 Visual Studio는 중단점 또는 예외에 도달할 때 중단 모드로 전환 됩니다. **모두 중단** 명령 (![모두 중단 아이콘](media/decompilation-break-all.png))을 사용 하 여 Visual Studio에서 다음에 코드를 실행할 때 중단을 쉽게 트리거할 수 있습니다.

### <a name="decompilation-limitations"></a>디컴파일을 제한 사항

.NET 어셈블리에서 사용 되는 중간 형식 (IL)에서 소스 코드를 생성 하면 몇 가지 내재 된 제한 사항이 있습니다. 따라서 생성 된 소스 코드는 원래 소스 코드와 같지 않습니다. 대부분의 차이점은 런타임에 원래 소스 코드의 정보가 필요 하지 않은 위치에 있습니다. 예를 들어 공백, 주석 및 지역 변수의 이름과 같은 정보는 런타임에 필요 하지 않습니다. 원래 소스 코드를 대체 하는 것이 아니라 생성 된 소스를 사용 하 여 프로그램이 실행 되는 방식을 이해 하는 것이 좋습니다.

### <a name="debug-optimized-or-release-assemblies"></a>최적화 된 어셈블리 또는 릴리스 어셈블리 디버그

컴파일러 최적화를 사용 하 여 컴파일된 어셈블리에서 디컴파일된 코드를 디버깅할 때 다음과 같은 문제가 발생할 수 있습니다.
- 중단점은 일치 하는 소싱 위치에 항상 바인딩할 수 없습니다.
- 단계별 실행은 항상 올바른 위치로 이동 하지 않을 수 있습니다.
- 지역 변수의 이름이 정확 하지 않을 수 있습니다.
- 일부 변수는 평가할 수 없습니다.

자세한 내용은 GitHub 문제에서 확인할 수 있습니다. [ICSharpCode. 디컴파일러 integration IN VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901)을 참조 하세요.

### <a name="decompilation-reliability"></a>디컴파일을 안정성

상대적으로 적은 수의 디컴파일을 시도로 인해 오류가 발생할 수 있습니다. 이는 ILSpy에서 시퀀스 지점 null 참조 오류가 발생 한 것입니다.  이러한 문제를 포착 하 고 디컴파일을 시도를 정상적으로 실패 하 여 오류를 완화 했습니다.

자세한 내용은 GitHub 문제에서 확인할 수 있습니다. [ICSharpCode. 디컴파일러 integration IN VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901)을 참조 하세요.

### <a name="limitations-with-async-code"></a>비동기 코드의 제한 사항

Async/wait 코드 패턴이 있는 디컴파일 모듈의 결과는 완전 하지 않거나 실패할 수 있습니다. Async/wait 및 yield 상태 컴퓨터의 ILSpy 구현은 부분적 으로만 구현 됩니다. 

자세한 내용은 GitHub 문제: [PDB 생성기 상태](https://github.com/icsharpcode/ILSpy/issues/1422)에서 찾을 수 있습니다.

### <a name="just-my-code"></a>내 코드만

[JMC (내 코드만)](https://docs.microsoft.com/visualstudio/debugger/just-my-code) 설정을 사용 하면 Visual Studio에서 시스템, 프레임 워크, 라이브러리 및 기타 사용자가 아닌 호출을 한 단계씩 실행 합니다. 디버깅 세션 중에 **모듈** 창에는 디버거가 내 코드로 처리 하는 코드 모듈 (사용자 코드)이 표시 됩니다.

최적화 또는 릴리스 모듈 디컴파일을 사용자가 작성 하지 않은 코드를 생성 합니다. 디컴파일된 사용자가 아닌 코드에서 디버거가 중단 되는 경우 (예: **소스 없음** 창이 표시 됩니다. 내 코드만를 사용 하지 않도록 설정 하려면 **도구** > **옵션** (또는 **디버그** > **옵션**>)으로 이동한 후 **디버깅** > **일반**으로 이동한 후 **내 코드만 사용**을 선택 취소 합니다.

### <a name="extracted-sources"></a>추출 된 소스

어셈블리에서 추출 된 소스 코드에는 다음과 같은 제한 사항이 있습니다.
- 생성 된 파일의 이름과 위치는 구성할 수 없습니다.
- 파일은 일시적 이며 Visual Studio에서 삭제 됩니다.
- 파일은 단일 폴더에 배치 되 고 원래 원본이 사용 되지 않은 모든 폴더 계층에 배치 됩니다.
- 각 파일의 파일 이름에는 파일의 체크섬 해시가 포함 되어 있습니다.

### <a name="generated-code-is-c-only"></a>생성 된 코드 C# 는
디컴파일을는에서 C#소스 코드 파일만 생성 합니다. 다른 언어로 파일을 생성 하는 옵션은 없습니다.
