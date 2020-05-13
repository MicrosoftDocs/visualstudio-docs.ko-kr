---
title: '방법: 삽입 된 코드 디버깅 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35d2343343bf554df7592c8616e7697d88665baf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62847787"
---
# <a name="how-to-debug-injected-code"></a>방법: 삽입한 코드 디버그

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 도구 메뉴에서 설정 가져오기 및 내보내기를 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

특성을 사용하면 C++ 프로그래밍을 매우 단순화할 수 있습니다. 자세한 내용은 [개념](/cpp/windows/attributed-programming-concepts)을 참조합니다. 일부 특성은 컴파일러가 직접 해석합니다. 프로그램 소스에 코드를 삽입하여 컴파일러가 컴파일할 수 있게 하는 특성도 있습니다. 이렇게 코드를 삽입하면 프로그래머가 써야 하는 코드의 양이 줄어들어 보다 쉽게 프로그래밍할 수 있습니다. 그러나 삽입된 코드를 실행하는 동안 때때로 버그가 발생하여 애플리케이션에 문제가 생기기도 합니다. 이런 경우에는 삽입된 코드를 살펴보아야 할 수 있습니다. Visual Studio에서는 두 가지 방법으로 삽입된 코드를 볼 수 있습니다.

- **디스어셈블리** 창에서 삽입된 코드를 볼 수 있습니다.

- [/Fx](/cpp/build/reference/fx-merge-injected-code)를 사용하여 원래 코드와 삽입된 코드가 병합된 원본 파일을 만들 수 있습니다.

**디스어셈블리** 창에는 소스 코드와 특성에 의해 삽입된 코드에 대한 어셈블리 언어 명령이 표시됩니다. 또한 **디스어셈블리** 창에 소스 코드 주석이 표시될 수도 있습니다.

## <a name="to-turn-on-source-annotation"></a>소스 주석을 설정하려면

- **디스어셈블리** 창에서 마우스 오른쪽 단추를 클릭하고 바로 가기 메뉴에서 **소스 코드 표시**를 선택합니다.

     소스 창에 있는 특성의 위치를 알면 바로 가기 메뉴를 사용하여 **디스어셈블리** 창에서 삽입된 코드를 찾을 수 있습니다.

## <a name="to-view-injected-code"></a>삽입된 코드를 보려면

1. 디버거는 중단 모드에 있어야 합니다.

2. 소스 코드 창에서 보려는 삽입된 코드의 특성 앞에 커서를 놓습니다.

3. 마우스 오른쪽 단추를 클릭하여 바로 가기 메뉴에서 **디스어셈블리로 이동**을 선택합니다.

     특성이 현재 실행 위치와 가까이 있으면 **디버그** 메뉴에서 **디스어셈블리** 창을 선택할 수 있습니다.

## <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>현재 실행 위치에서 디스어셈블리 코드를 보려면

1. 디버거는 중단 모드에 있어야 합니다.

2. **디버그** 메뉴에서 **창**을 선택하고 **디스어셈블리**를 클릭합니다.

## <a name="see-also"></a>참고자료

- [디버거 보안](../debugger/debugger-security.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)
