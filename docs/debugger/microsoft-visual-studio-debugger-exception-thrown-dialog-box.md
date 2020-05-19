---
title: Microsoft Visual Studio Debugger(예외 throw) 대화 상자 | Microsoft Docs
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8376d0cd82e309c2c8db94e38b8c6a2083bd429a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731204"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Debugger(예외 throw) 대화 상자
프로그램에 예외가 발생하면 나타나는 대화 상자입니다. 이 대화 상자는 throw된 예외의 종류를 보고합니다. 코드를 통해 이 예외를 처리해야 합니다. 선택할 수 있는 예외 처리 옵션은 다음과 같습니다.

 **중단** - 프로그램의 실행을 중단하고 디버거를 시작합니다. 실행을 중단하기 전에는 예외 처리기가 호출되지 않습니다. 중단 위치에서 실행을 계속하면 예외 처리기가 호출됩니다.

 **계속** - 실행을 계속하여 예외 처리기에 예외를 처리할 기회를 줍니다. 특정 유형의 예외에는 이 옵션을 사용할 수 없습니다. **계속**을 선택하면 애플리케이션 실행이 계속됩니다. 네이티브 애플리케이션에서는 예외가 다시 throw됩니다. 관리되는 애플리케이션에서는 프로그램이 종료되거나 호스팅 애플리케이션에서 예외를 처리합니다.

> [!NOTE]
> 관리 코드에서는 처리되지 않은 예외가 발생한 후 실행을 계속할 수 없습니다. 관리 코드에서 처리되지 않은 예외가 발생한 후 **계속**을 선택하면 디버깅이 중지됩니다.

 **무시** - 예외 처리기를 호출하지 않고 실행을 계속합니다. 예외 처리기가 호출되지 않으므로 추가적인 예외 및 오류를 비롯한 후속 결과가 발생할 수 있습니다. 특정 유형의 예외에는 이 옵션을 사용할 수 없습니다.

## <a name="see-also"></a>참조
- [디버거를 사용한 예외 관리](../debugger/managing-exceptions-with-the-debugger.md)
- [예외에 대한 모범 사례](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [예외 처리](/cpp/extensions/exception-handling-cpp-component-extensions)