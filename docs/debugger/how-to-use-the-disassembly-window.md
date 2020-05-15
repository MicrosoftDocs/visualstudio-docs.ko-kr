---
title: 디버거에서 디스어셈블리 코드 보기 | Microsoft Docs
ms.custom: seodec18
ms.date: 10/30/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43214ee122b3aa5c3907b9176631f2dc22c9178e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846392"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio 디버거에서 디스어셈블리 코드 보기(C#, C++, Visual Basic, F#)

**디스어셈블리** 창에는 컴파일러에서 만든 명령에 따라 어셈블리 코드가 표시됩니다. 관리 코드를 디버그하는 경우 이러한 어셈블리 명령은 Visual Studio 컴파일러에서 생성한 MSIL(Microsoft Intermediate Language)이 아닌 JIT(Just-in-Time) 컴파일러에서 만든 네이티브 코드에 대응합니다.

> [!NOTE]
> **디스어셈블리** 창을 최대한 활용하려면 [어셈블리 언어 프로그래밍](https://wikipedia.org/wiki/Assembly_language)의 기본 사항을 이해하거나 알아보세요.

이 기능은 주소 수준 디버깅을 사용하도록 설정해야만 사용할 수 있습니다. 스크립트 또는 SQL 디버깅에는 사용할 수 없습니다.

**디스어셈블리** 창에는 어셈블리 지침뿐 아니라 다음과 같은 선택적 정보도 표시할 수 있습니다.

- 각 명령이 있는 메모리 주소, 네이티브 애플리케이션의 경우 실제 메모리 주소, Visual Basic 또는 C#의 경우 함수의 시작 부분으로부터의 오프셋입니다.

- 어셈블리 코드가 파생된 소스 코드

- 코드 바이트(실제 컴퓨터 또는 MSIL 명령의 바이트 표시)

- 메모리 주소의 기호 이름

- 소스 코드에 해당하는 줄 번호

어셈블리 언어 명령은 명령 이름의 약어인 ‘니모닉’과 변수, 레지스터 및 상수를 나타내는 ‘기호’로 이루어집니다.   각 컴퓨터 언어 명령은 하나의 어셈블리 언어 니모닉으로 표시되며 필요에 따라 그 뒤에 하나 이상의 기호가 옵니다.

어셈블리 코드는 프로세서 레지스터 또는 공용 언어 런타임 레지스터(관리 코드의 경우)에 크게 의존합니다. **디스어셈블리** 창과 **레지스터** 창을 함께 사용하면 레지스터 콘텐츠를 검사할 수 있습니다.

어셈블리 언어가 아닌 원시 숫자 형식으로 컴퓨터 코드 명령을 보려면 **메모리** 창을 사용하거나 **디스어셈블리** 창의 바로 가기 메뉴에서 **코드 바이트**를 선택합니다.

## <a name="use-the-disassembly-window"></a>디스어셈블리 창 사용

**디스어셈블리** 창을 사용하도록 설정하려면 **도구** > **옵션**(또는 **도구** > **옵션**) > **디버깅**에서 **주소 수준 디버깅 사용**을 선택합니다.

디버그하는 동안 **디스어셈블리** 창을 열려면 **창** > **디스어셈블리**를 선택하거나 **Alt**+**8**을 누릅니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

선택적 정보 표시 여부를 선택하려면 **디스어셈블리** 창을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 원하는 옵션을 선택하거나 선택 취소합니다.

왼쪽 여백의 노란색 화살표는 현재 실행 지점을 나타냅니다. 네이티브 코드의 경우 실행 지점은 CPU의 프로그램 카운터에 해당합니다. 이 위치는 프로그램에서 다음에 실행될 명령을 나타냅니다.

## <a name="see-also"></a>참조

* [메모리에서 페이지 위나 아래로 이동](../debugger/how-to-page-up-or-down-in-memory.md)
* [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
* [방법: 레지스터 창 사용](../debugger/how-to-use-the-registers-window.md)