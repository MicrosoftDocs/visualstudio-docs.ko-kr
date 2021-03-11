---
description: 64비트 프로세스의 혼합 네이티브 및 관리 코드를 디버그하려면 .NET Framework 버전 4가 있어야 합니다.
title: x64 프로세스의 혼합 모드 디버깅은 Microsoft .NET Framework 4 이상을 사용할 때만 지원됨 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 31ae6b1c4a80f7d28cdbbdd2c4d944cddf15227d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146953"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>오류: x64 프로세스용 혼합 모드 디버깅은 Microsoft .NET Framework 4 이상을 사용할 때만 지원됩니다.
64비트 프로세스의 혼합 네이티브 및 관리 코드를 디버그하려면 .NET Framework 버전 4가 있어야 합니다. 4 이전 버전의 .NET Framework에서는 64비트 프로세스의 혼합 모드 디버깅이 지원되지 않습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 다음 단계 중 하나를 수행합니다.

  - .NET Framework를 버전 4로 업그레이드합니다.

  - 디버깅을 위해 32비트 버전의 애플리케이션을 빌드합니다.

## <a name="see-also"></a>참조
- [Remote Debugging](../debugger/remote-debugging.md)
