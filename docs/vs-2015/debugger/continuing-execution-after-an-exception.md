---
title: 예외 후 실행 계속 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
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
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ae74c51f0f738bc596fbe5c789011630927707c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702263"
---
# <a name="continuing-execution-after-an-exception"></a>예외 후 실행 계속
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

예외로 인해 디버거에서 실행이 중단되면 대화 상자가 나타납니다. Visual Basic 또는 c #의 경우 기본적으로 [예외 도우미](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) 대화 상자가 표시 됩니다. C + +의 경우 이전 **예외** 대화 상자가 표시 됩니다. Visual Basic 또는 c #을 사용 하지만 **옵션** 대화 상자에서 **예외 도우미** 를 사용 하지 않도록 설정한 경우에는 **예외** 대화 상자가 표시 됩니다.  
  
 예외 **도우미** 또는 **예외** 대화 상자가 나타나면 예외를 발생 시킨 문제를 해결할 수 있습니다.  
  
## <a name="managed-code"></a>관리 코드  
 관리 코드에서는 처리되지 않은 예외가 발생한 후 같은 스레드에서 실행을 계속할 수 있습니다. **예외 도우미** 는 예외가 throw 된 지점까지 호출 스택을 해제 합니다.  
  
## <a name="native-code"></a>네이티브 코드  
 네이티브 C/C++에서는 두 가지 옵션이 있습니다.  
  
- **중단** 을 클릭 하 고 문제 해결을 시도할 수 있습니다. 중단 모드에 있는 동안 **호출 스택** 창에서 프레임을 마우스 오른쪽 단추로 클릭 하 고 바로 가기 메뉴에서 **이 프레임으로 해제를** 선택 하 여 호출 스택을 해제할 수 있습니다. 디버깅을 계속 하면 문제를 해결 하지 않은 경우 **예외** 대화 상자가 다시 나타납니다. 그렇지 않으면 **예외** 대화 상자가 다시 나타나지 않습니다.  
  
- 문제 해결을 시도 하지 않고 **계속** 을 클릭 하 여 계속 실행할 수 있습니다. **예외** 대화 상자가 다시 나타납니다.  
  
## <a name="mixed-code"></a>혼합 코드  
 네이티브 및 관리 코드가 혼합된 코드를 디버깅하는 동안 처리되지 않은 예외가 발생하면 운영 체제 제한에 따라 호출 스택을 해제할 수 없습니다. 바로 가기 메뉴를 사용하여 호출 스택을 해제하려고 하면 혼합 코드 디버깅 중에 처리되지 않은 예외가 발생하면 디버거가 호출 스택을 해제할 수 없다는 내용의 오류 메시지가 나타납니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거를 사용한 예외 관리](../debugger/managing-exceptions-with-the-debugger.md)
