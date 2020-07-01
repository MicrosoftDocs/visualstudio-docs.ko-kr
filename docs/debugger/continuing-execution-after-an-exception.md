---
title: 예외 후 실행 계속 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e94867d845988b787247c32d32afd35af946972
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350682"
---
# <a name="continuing-execution-after-an-exception"></a>예외 후 실행 계속
예외로 인해 디버거가 실행을 중단하면 기본적으로 **예외 도우미**가 표시됩니다. **옵션** 대화 상자에서 **예외 도우미**를 사용하지 않도록 설정한 경우 **예외 도우미**(C# 또는 Visual Basic) 또는 **예외** 대화 상자(C+++)가 표시됩니다.

 **예외 도우미**가 표시되면 예외를 발생시킨 문제를 해결할 수 있습니다.

## <a name="managed-and-native-code"></a>관리 및 네이티브 코드
 관리 및 네이티브 코드에서는 처리되지 않은 예외가 발생한 후 같은 스레드에서 실행을 계속할 수 있습니다. **예외 도우미**는 호출 스택을 해제하여 예외가 throw된 지점으로 되돌립니다.

## <a name="mixed-code"></a>혼합 코드
 네이티브 및 관리 코드가 혼합된 코드를 디버깅하는 동안 처리되지 않은 예외가 발생하면 운영 체제 제한에 따라 호출 스택을 해제할 수 없습니다. 바로 가기 메뉴를 사용하여 호출 스택을 해제하려고 하면 혼합 코드 디버깅 중에 처리되지 않은 예외가 발생하면 디버거가 호출 스택을 해제할 수 없다는 내용의 오류 메시지가 나타납니다.

## <a name="see-also"></a>참조

- [디버거를 사용한 예외 관리](../debugger/managing-exceptions-with-the-debugger.md)