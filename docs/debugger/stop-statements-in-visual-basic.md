---
title: Visual Basic의 Stop 문 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f9ab4ef453a921371ab7ef4f272cd0e38f4108a
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322529"
---
# <a name="stop-statements-in-visual-basic"></a>Visual Basic의 Stop 문

중단점을 설정하는 대신 Visual Basic의 Stop 문을 사용하는 프로그래밍 방식을 제공합니다. 디버거에서는 Stop 문이 나올 경우 프로그램 실행을 중단하여 중단 모드를 시작합니다. C# 프로그래머는 <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>에 대한 호출을 사용하여 동일한 결과를 얻을 수 있습니다.

Stop 문을 설정하거나 제거하려면 소스 코드를 편집해야 합니다. 중단점을 설정하거나 제거하는 것처럼 디버거 명령을 사용하여 Stop 문을 설정하거나 제거할 수는 없습니다.

End 문과 달리, Stop 문은 변수를 다시 설정하거나 사용자를 디자인 모드로 되돌리지 않습니다. 디버그 메뉴에서 계속을 선택하면 계속 애플리케이션을 실행할 수 있습니다.

디버거 외부에서 Visual Basic 애플리케이션을 실행할 경우, Just-in-Time 디버깅이 활성화되면 Stop 문이 디버거를 실행합니다. Just-in-Time 디버깅이 활성화되지 않으면, Stop 문이 End 문처럼 동작하여 실행을 종료합니다. QueryUnload 이벤트나 Unload 이벤트가 발생하지 않으므로, Visual Basic 애플리케이션의 릴리스 버전에서 모든 Stop 문을 제거해야 합니다. 자세한 내용은 [Just-In-Time 디버깅](just-in-time-debugging-in-visual-studio.md)을 참조하세요.

 다음과 같은 조건부 컴파일을 사용하면 이 경우에 Stop 문을 제거하지 않아도 됩니다.

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

또 다른 방법은 Stop 문 대신 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 문을 사용하는 것입니다. <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 문은 지정된 조건이 충족되지 않는 경우에만 실행을 중단합니다. 릴리스 버전을 빌드하면 <xref:System.Diagnostics.Debug.Assert%2A> 문은 자동으로 제거됩니다. 자세한 내용은 [관리 코드의 어설션](assertions-in-managed-code.md)을 참조하세요. 디버그 버전에서 <xref:System.Diagnostics.Debug.Assert%2A> 문이 항상 실행을 중단하도록 하려면 다음과 같이 지정하세요.

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

다음과 같이 <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> 메서드를 사용할 수도 있습니다.

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>참조

- [디버거 보안](debugger-security.md)
- [C#, F#, and Visual Basic Project Types](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)(C#, F# 및 Visual Basic 프로젝트 형식)
- [관리 코드 디버그](debugging-managed-code.md)
