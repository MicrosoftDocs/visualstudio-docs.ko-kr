---
title: 스토어 앱 디버그
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 48a85bcf-290b-4390-9993-f6f9dd73ad03
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bc2d05c6b6aae4b2f33d135c6859da7b17de963
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533161"
---
# <a name="debug-store-apps-in-visual-studio"></a>Visual Studio에서 스토어 앱 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 디버거를 사용하면 프로그램의 실행을 제어하고 프로그램의 상태를 검사할 수 있습니다. 디버거를 사용하여 Windows 스토어 앱에서 결함의 원인을 찾고 앱 작동 방법을 정확하게 파악할 수 있습니다. 디버거에서 실행을 일시 중단(중단)하면 Visual Studio에는 실행 코드가 포함된 소스 파일이 표시되고 실행 문이 강조 표시됩니다. 변수 값, 실행 함수의 호출 스택과 그 외 프로그램 상태에 관한 측면을 볼 수 있습니다. 한 번에 프로그램 문을 하나씩 계속 실행(단계별 실행)하면 문에서 프로그램 값을 변경하는 방법을 확인할 수 있습니다. JavaScript로 작성된 앱에서 페이지의 DOM을 검사 및 조작할 수 있습니다.

## <a name="in-this-section"></a>단원 내용

|제목|설명|
|-|-|
|[디버그 세션 시작(JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)|디버깅 세션을 시작하는 방법에서는 JavaScript 앱에 대한 디버깅 세션을 구성 및 시작할 수 있는 다양한 옵션을 설명합니다.|
|[디버그 세션에서 실행 제어(JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)|디버거 탐색에서는 디버깅을 시작 및 중지하는 방법과 코드를 탐색하는 방법, 프로그램 상태를 보는 방법을 알려 주는 간단한 앱을 소개합니다.|
|[빠른 시작: HTML 및 CSS 디버그](../debugger/quickstart-debug-html-and-css.md)|HTML 및 CSS 디버깅에서는 HTML과 CSS를 보고 수정할 수 있는 라이브 DOM 검사 도구를 사용하여 JavaScript 앱을 대화형으로 디버깅하는 방법을 설명합니다.|
|[빠른 시작: JavaScript 디버그](../debugger/quickstart-debug-javascript-using-the-console.md)|콘솔을 사용 하 여 JavaScript 디버그 javascript [콘솔 명령을](../debugger/javascript-console-commands.md)사용 하 여 javascript 앱을 대화형으로 디버깅 하는 방법을 보여 줍니다.|
|[디버그 세션 시작(VB, C#, C++ 및 XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)|디버깅 세션을 시작하는 방법(Visual C++, Visual C# 및 Visual Basic)에서는 Visual C++, Visual C# 또는 Visual Basic으로 작성된 앱의 디버깅 세션을 구성 및 시작할 수 있는 다양한 옵션을 설명합니다.|
|[디버그 세션 탐색(XAML 및 C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)|디버거 탐색에서는 디버깅을 시작 및 중지하는 방법과 코드를 탐색하는 방법, 프로그램 상태를 보고 변경하는 방법을 알려 주는 간단한 앱을 설명합니다.|
|[Windows 스토어에 대한 일시 중단, 다시 시작 및 백그라운드 이벤트 트리거](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)|디버거는 앱을 일시 중지, 다시 시작 및 종료하는 Windows PLM(프로세스 수명 관리) 이벤트를 사용하지 않도록 설정합니다. 디버거 도구 모음에서 이러한 이벤트를 트리거할 수 있습니다.<br /><br /> 백그라운드 작업을 통해 앱이 일시 중단된 경우에도 중요한 작업을 수행할 수 있습니다. 디버거를 사용하면 이러한 백그라운드 작업을 시작하고 디버깅할 수 있습니다.|

## <a name="see-also"></a>참고 항목
 [Visual Studio에서 디버깅(MSDN 라이브러리)](https://msdn.microsoft.com/library/sc65sadd(VS.110).aspx)
