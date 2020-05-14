---
title: CRT 디버그 라이브러리 사용 | Microsoft Docs
ms.date: 10/03/2019
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20aeee220bec600c2232286d18600b04201ad03b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745614"
---
# <a name="crt-debug-library-use"></a>CRT 디버그 라이브러리 사용
C 런타임 라이브러리는 디버깅을 폭넓게 지원합니다. CRT 디버그 라이브러리 중 하나를 사용 하려면 [/debug](/cpp/build/reference/debug-generate-debug-info) 와 연결하고 **/mdd**, **/MTd** 또는 **/ldd**로 컴파일해야 합니다.

## <a name="remarks"></a>주의
 CRT 디버깅의 주요 정의와 매크로는 CRTDBG.h 헤더 파일에 포함되어 있습니다.

 CRT 디버그 라이브러리의 함수는 최적화 없이 디버그 정보([/Z7, /Zd, /Zi, /ZI(디버깅 정보 형식)](/cpp/build/reference/z7-zi-zi-debug-information-format))를 사용하여 컴파일됩니다. 일부 함수는 함수에 전달된 매개 변수를 확인하기 위해 어설션을 사용하며 소스 코드를 제공합니다. 이 소스 코드를 사용하면 CRT 함수를 단계적으로 실행하여 원하는 대로 함수가 작동하고 있는지 확인하고 잘못된 매개 변수나 메모리 상태를 검사할 수 있습니다. 일부 CRT 기술은 독점되어 있어서 예외 처리, 부동 소수점 및 다른 몇 가지 루틴에 대한 소스 코드를 제공하지 않습니다.

 사용할 수 있는 런타임 라이브러리에 대한 자세한 내용은 [C 런타임 라이브러리](/cpp/c-runtime-library/crt-library-features)를 참조하세요.

## <a name="see-also"></a>참조

- [CRT 디버깅 기술](../debugger/crt-debugging-techniques.md)
- [/MD, /MT, /LD(런타임 라이브러리 사용)](/cpp/build/reference/md-mt-ld-use-run-time-library)
