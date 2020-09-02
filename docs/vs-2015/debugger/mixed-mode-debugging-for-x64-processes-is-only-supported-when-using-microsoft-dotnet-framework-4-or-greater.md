---
title: x64 프로세스의 혼합 모드 디버깅은 Microsoft .NET Framework 4 이상을 사용할 때만 지원됨 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e974269cccb65db66ee59735f7acc5de494e2106
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697828"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>x64 프로세스의 혼합 모드 디버깅은 Microsoft .NET Framework 4 이상을 사용할 때만 지원됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET Framework 버전 4 이전 버전에서는 x64 프로세스의 혼합 모드 디버깅을 지원 하지 않습니다. 따라서 디버깅하는 동안 네이티브 코드에서 관리 코드로 또는 그 반대로 실행할 수 없습니다.  
  
### <a name="workarounds"></a>해결 방법  
  
- Microsoft .NET Framework 4 이상을 사용하도록 프로젝트를 업데이트합니다.  
  
     -또는-  
  
     관리 코드와 네이티브 코드를 별도의 디버깅 세션에서 디버깅합니다.  
  
     -또는-  
  
     다음 절차에 설명된 대로 혼합 코드를 32비트 프로세스로 디버깅합니다.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>플랫폼을 32비트로 변경하려면(Visual Basic 또는 C#)  
  
1. **솔루션 탐색기**에서 프로젝트를 오른쪽 마우스 단추로 클릭하고 **속성**을 클릭합니다.  
  
2. 속성 페이지에서 **컴파일** 또는 **디버그** 탭을 클릭합니다.  
  
3. **플랫폼**을 클릭하고 플랫폼 목록에서 x86을 선택합니다.  
  
     기본적으로 Visual Basic 및 C# 컴파일러에서는 모든 CPU에서 실행할 수 있는 코드를 생성합니다. 이러한 이진 코드는 64비트 컴퓨터에서 64비트 프로세스로 실행됩니다. 32비트 프로세스에서 실행하려면 **AnyCPU** 대신 **Win32**를 선택해야 합니다.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>플랫폼을 32비트로 변경하려면(C/C++)  
  
1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  
  
2. 속성 페이지에서 **플랫폼**을 클릭하고 플랫폼 목록에서 Win32를 선택합니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- [SQL 디버깅 설정](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [64비트 애플리케이션 디버그](../debugger/debug-64-bit-applications.md)
