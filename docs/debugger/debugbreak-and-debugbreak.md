---
title: DebugBreak 및 __debugbreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 097405f98d1a80b8605b6773bdc675ff2c4ab773
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404651"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak 및 __debugbreak
코드의 어떤 위치에서든 [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) Win32 함수 또는 [__debugbreak](/cpp/intrinsics/debugbreak) 내장 함수를 호출할 수 있습니다. `DebugBreak` 및 `__debugbreak`는 해당 위치에 중단점을 설정하는 것과 같은 효과가 있습니다.

 `DebugBreak`는 시스템 함수에 대한 호출이므로 중단 후 올바른 호출 스택 정보가 표시되도록 하려면 시스템 디버그 기호를 설치해야 합니다. 이렇게 하지 않으면 디버거에서 표시하는 호출 스택 정보가 한 프레임씩 차이가 날 수 있습니다. `__debugbreak`를 사용하는 경우에는 기호가 필요하지 않습니다.

## <a name="see-also"></a>참조
- [컴파일러 내장 함수](/cpp/intrinsics/compiler-intrinsics)
- [디버거 보안](../debugger/debugger-security.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)
- [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
