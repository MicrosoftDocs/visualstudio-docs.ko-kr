---
title: 웹 서비스를 디버그하는 동안 시간 초과 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f3522b61c8d7d78a182036d3a1f66c0495f5081
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852448"
---
# <a name="error-timeout-while-debugging-web-services"></a>오류: 웹 서비스를 디버깅하는 동안 시간 초과
코드를 호출하여 XML Web services를 한 단계씩 실행할 때 호출 시간이 초과되어 디버깅을 계속할 수 없는 경우가 있습니다. 이때 다음과 같은 오류 메시지가 나타날 수 있습니다.

```cmd
An unhandled exception of type 'System.Net.WebException' occurred in
system.Web.services.dll
Additional information: The operation has timed-out.
```

## <a name="solution"></a>솔루션
 이 문제를 방지하려면 다음 예제와 같이 XML Web services 호출에 대한 시간 제한 값을 무한대로 설정합니다.

```csharp
Service1 obj = new Service1();
obj.TimeOut = -1; // infinite time out.
```

## <a name="see-also"></a>참조
- [웹 애플리케이션 디버그: 오류 및 문제 해결](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
