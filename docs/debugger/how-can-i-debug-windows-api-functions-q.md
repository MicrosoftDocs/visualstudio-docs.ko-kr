---
title: Windows API 함수 디버그 | Microsoft Docs
description: NT 기호가 로드된 Windows API 함수를 디버그하는 방법을 알아봅니다. 32비트 코드에서 데코레이트된 형식의 함수 이름을 사용하여 중단점을 설정합니다.
ms.custom: SEO-VS-2020
ms.date: 06/03/2020
ms.topic: how-to
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89fdbcf9d18a7794e1fb2520384db0f9bcec3147
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386945"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Windows API 함수를 어떻게 디버깅할 수 있습니까?
NT 기호가 로드된 Windows API 함수를 디버깅하려면 다음 작업을 수행해야 합니다.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>NT 기호가 있는 Windows API 함수에 중단점을 설정하려면

- [함수 중단점](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)에서 함수가 있는 DLL의 이름과 함께 함수 이름을 입력합니다([컨텍스트 연산자](../debugger/context-operator-cpp.md) 참조). 32비트 코드에서는 함수 이름의 데코레이팅된 형식을 사용합니다. 예를 들어 **MessageBeep** 에 중단점을 설정하려면 다음을 입력해야 합니다.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     데코레이트된 이름을 가져오려면 [데코레이트된 이름 보기](/previous-versions/5x49w699(v=vs.140))를 참조하세요.

     데코레이트된 이름을 테스트하고 디스어셈블리 코드에서 볼 수 있습니다. Visual Studio 디버거의 함수에서 일시 중지된 동안 코드 편집기 또는 호출 스택 창에서 함수를 마우스 오른쪽 단추로 클릭하고 **디스어셈블리로 이동** 을 선택합니다.

- 64비트 코드에서 데코레이트되지 않은 이름을 사용할 수 있습니다.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>참조
- [네이티브 코드 디버그 FAQ](../debugger/debugging-native-code-faqs.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)
