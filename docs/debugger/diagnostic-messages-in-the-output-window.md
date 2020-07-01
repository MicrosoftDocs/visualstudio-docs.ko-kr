---
title: 출력 창으로 메시지 보내기 | Microsoft Docs
ms.date: 11/08/2018
ms.topic: how-to
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d3c146775ac06b3118186738ee74932a4c452a
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350474"
---
# <a name="send-messages-to-the-output-window"></a>출력 창으로 메시지 보내기

<xref:System.Diagnostics> 클래스 라이브러리에 포함된 <xref:System.Diagnostics.Debug> 클래스나 <xref:System.Diagnostics.Trace> 클래스를 사용하여 **출력** 창에 런타임 메시지를 쓸 수 있습니다. ‘디버그’ 버전의 프로그램에서만 출력하려는 경우에는 <xref:System.Diagnostics.Debug> 클래스를 사용하세요. ‘디버그’ 및 ‘릴리스’ 버전에서 모두 출력하려면 <xref:System.Diagnostics.Trace> 클래스를 사용하세요. 

## <a name="output-methods"></a>출력 메서드
 <xref:System.Diagnostics.Trace> 클래스와 <xref:System.Diagnostics.Debug> 클래스에는 다음과 같은 출력 메서드가 있습니다.

- 실행을 중단하지 않고 정보를 출력하는 여러 가지 `Write` 메서드. 이 메서드는 이전 Visual Basic 버전의 `Debug.Print` 메서드 대신 사용됩니다.

- 지정된 조건이 실패할 경우 실행을 중단하고 정보를 출력하는 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 및 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 메서드. 기본적으로 `Assert` 메서드는 해당 정보를 대화 상자에 표시합니다. 자세한 내용은 [관리 코드의 어설션](../debugger/assertions-in-managed-code.md)을 참조하세요.

- 항상 실행을 중단하고 정보를 출력하는 <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> 및 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> 메서드. 기본적으로 `Fail` 메서드는 정보를 대화 상자에 표시합니다.

**출력** 창에는 다음에 대한 정보가 표시될 수도 있습니다.

- 디버거에서 로드하거나 언로드한 모듈 정보

- throw된 예외 정보

- 종료되는 프로세스 정보

- 종료되는 스레드 정보

## <a name="see-also"></a>참조
- [디버거 보안](../debugger/debugger-security.md)
- [출력 창](../ide/reference/output-window.md)
- [애플리케이션 추적 및 계측](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [C#, F# 및 Visual Basic 프로젝트 형식](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [관리 코드 디버깅](../debugger/debugging-managed-code.md)
