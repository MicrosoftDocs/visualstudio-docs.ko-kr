---
title: 혼합 모드 디버깅은 Microsoft .NET Framework 2.0 또는 3.0을 사용할 때만 지원됨 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b20ef6b81e4d7162fd230d9d0c3437fe1b5232c1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730926"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>혼합 모드 디버깅은 Microsoft .NET Framework 2.0 또는 3.0을 사용할 때만 지원됩니다.
2\.0 이전 버전의 Microsoft .NET Framework에서는 64비트 프로세스의 혼합 모드 디버깅이 지원되지 않습니다. 즉, 디버깅하는 동안 네이티브 코드에서 관리 코드로 또는 그 반대로 이동할 수 없습니다.

 이 문제를 해결하기 위해 다음을 수행할 수 있습니다.

- Microsoft .NET Framework 2.0 또는 3.0을 사용하도록 프로젝트를 업데이트합니다.

- 관리 코드와 네이티브 코드를 별도의 디버깅 세션에서 디버깅합니다.

- 다음 절차에 설명된 대로 혼합 코드를 32비트 프로세스로 디버깅합니다.

### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>운영 체제를 32비트로 변경하려면(Visual Basic 또는 C#)

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음, 바로 가기 메뉴에서 **속성**을 클릭합니다.

2. 속성 페이지에서 **컴파일** 또는 **디버그** 탭을 클릭합니다.

3. **플랫폼**을 클릭한 다음, 플랫폼 목록에서 **x86**을 선택합니다.

     기본적으로 Visual Basic 및 C# 컴파일러에서는 모든 CPU에서 실행할 수 있는 코드가 생성됩니다. 이러한 이진 코드는 64비트 컴퓨터에서 64비트 프로세스로 실행됩니다. 32비트 프로세스에서 실행하려면 **AnyCPU** 대신 **Win32**를 선택해야 합니다.

### <a name="to-change-the-operating-system-to-32-bit-cc"></a>운영 체제를 32비트로 변경하려면(C/C++)

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음, 바로 가기 메뉴에서 **속성**을 클릭합니다.

     속성 페이지에서 **플랫폼**을 클릭하고 플랫폼 목록에서 **Win32**를 선택합니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- [SQL 디버깅 설정](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))을 참조하세요.

## <a name="see-also"></a>참조
- [64비트 애플리케이션 디버그](../debugger/debug-64-bit-applications.md)