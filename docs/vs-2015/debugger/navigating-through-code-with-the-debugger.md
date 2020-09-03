---
title: 디버거를 사용 하 여 코드 탐색 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f79ece781db19f2483ef1dd6cb0a81ff7cf78e06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88608941"
---
# <a name="navigating-through-code-with-the-debugger"></a>디버거로 코드 탐색
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

디버거를 사용 하 여 코드를 탐색 하 고 응용 프로그램에서 문제를 더 빠르고 쉽게 해결할 수 있도록 하는 명령 및 바로 가기에 대해 알아봅니다. 디버거에서 코드를 탐색 하는 동안 [앱의 상태를 검사](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) 하거나 실행 흐름에 대해 자세히 알아볼 수 있습니다.  
  
## <a name="start-debugging"></a>디버그 시작  
 **F5 키** 를 사용 하 여 디버깅 세션을 시작 하는 경우가 종종 있습니다 (**디버그**  /  **디버깅 시작**). 이 명령은 디버거가 연결 된 상태에서 앱을 시작 합니다.  
  
 녹색 화살표는 디버거도 시작 합니다 ( **F5**와 동일).  
  
 ![DBG&#95;기본 사항&#95;디버깅 시작&#95;](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 디버거를 연결 하 여 응용 프로그램을 시작할 수 있는 몇 가지 다른 방법으로는 **F11** ([코드 한 단계씩 코드](#BKMK_Step_into__over__or_out_of_the_code)실행),  **F10** ([프로시저 단위](#BKMK_Step_over_Step_out)실행) 또는 **커서까지 실행**을 사용 하는 등이 있습니다.  이러한 옵션의 용도에 대 한 정보는이 항목의 다른 섹션을 참조 하세요.  
  
 디버그할 때 노란색 선은 다음에 실행 될 코드를 보여 줍니다.  
  
 ![DBG&#95;기본&#95;중단&#95;모드](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 디버깅 하는 동안 **F5**, **F11** 등의 명령을 전환 하 고이 항목에 설명 된 다른 기능 (예: 중단점)을 사용 하 여 확인 하려는 코드를 신속 하 게 가져올 수 있습니다.  
  
 지역 창에서 변수 값 보기 또는 조사식 창 식 평가와 같은 대부분의 디버거 기능은 디버거가 일시 중지 된 동안에만 사용할 수 있습니다 ( *중단 모드*라고도 함). 디버거가 일시 중지 되 면 함수, 변수 및 개체가 메모리에 유지 되는 동안 앱 상태가 일시 중단 됩니다. 중단 모드에서 요소 위치 및 상태를 검사 하 여 위반 또는 버그를 찾을 수 있습니다. 일부 프로젝트 형식의 경우 중단 모드에 있는 동안 애플리케이션을 조정할 수도 있습니다.  
  
## <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> 한 줄씩 코드 한 단계씩 코드 실행  
 디버깅 하는 동안 각 코드 줄 (각 문)에서 중지 하려면 **F11** 키보드 바로 가기 (또는 메뉴의 **디버그**  /  **단계** )를 사용 합니다.  
  
> [!TIP]
> 각 코드 줄을 실행 하면 변수 위로 마우스를 이동 하 여 값을 확인 하거나 [지역](../debugger/autos-and-locals-windows.md) 및 [조사식](../debugger/autos-and-locals-windows.md) 창을 사용 하 여 해당 값이 변경 되는 것을 볼 수 있습니다.  
  
 한 **단계씩 코드 실행**의 동작에 대 한 자세한 내용은 다음과 같습니다.  
  
- 중첩된 함수 호출인 경우 **한 단계씩 코드 실행** 명령은 가장 안쪽에 중첩된 함수를 한 단계씩 실행합니다. **와 같은 호출에** 한 단계씩 코드 실행 `Func1(Func2())`을 사용하면 디버거에서 함수 `Func2`를 한 단계씩 실행합니다.  
  
- 실제로 디버거는 실제 줄이 아닌 코드 문을 단계별로 실행합니다. 예를 들어 한 줄에 `if` 절을 작성할 수 있습니다.  
  
  ```csharp  
  int x = 42;  
  string s = "Not answered";  
  if( int x == 42) s = "Answered!";  
  ```  
  
  ```vb  
  Dim x As Integer = 42  
  Dim s As String = "Not answered"  
  If x = 42 Then s = "Answered!"  
  ```  
  
   이 줄을 한 단계씩 실행하면 디버거는 조건을 한 단계로 처리하고 결과를 다른 단계로 처리합니다(이 예에서는 조건이 참임).  
  
  함수를 한 단계씩 실행 하는 동안 호출 스택을 시각적으로 추적 하려면 [디버그 하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)를 참조 하세요.  
  
## <a name="step-through-code-skipping-functions"></a><a name="BKMK_Step_over_Step_out"></a> 코드를 단계별로 실행 하 고 함수를 건너뜁니다.  
 디버거에서 코드를 실행 하는 경우 특정 함수에서 무슨 일이 발생 하는지 확인할 필요가 없는 경우가 종종 있습니다 (잘 테스트 된 라이브러리 코드와 같이 중요 하지 않거나 작동 한다는 것을 알 수 없음). 이러한 명령을 사용 하 여 코드를 건너뛸 수 있습니다 (물론 함수는 계속 실행 되지만 디버거는 해당 함수를 건너뜁니다).  
  
|키보드 명령|메뉴 명령|설명|  
|----------------------|------------------|-----------------|  
|**F10**|**프로시저 단위 실행**|현재 줄에 함수 호출이 포함 된 경우 **프로시저 단위** 실행은 코드를 실행 한 다음 호출 된 함수가 반환 된 후 코드의 첫 번째 줄에서 실행을 일시 중단 합니다.|  
|**Shift+F11**|**프로시저 나가기**|**프로시저** 실행 코드를 계속 실행 하 고 현재 함수가 반환 될 때 실행을 일시 중단 합니다. 디버거는 현재 함수를 건너뜁니다.|  
  
> [!TIP]
> 앱에서 진입점을 찾아야 하는 경우 **F10** 또는 **F11**키를 사용 하 여 시작 합니다. 이러한 명령은 종종 앱 상태를 검사 하거나 실행 흐름에 대 한 자세한 정보를 확인 하려는 경우에 유용 합니다.  
  
## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> 특정 위치 또는 함수까지 실행  
 종종 코드를 디버깅 하는 기본 방법입니다. 이러한 메서드는 검사할 코드를 정확 하 게 알고 있거나 최소한 디버깅을 시작할 위치를 알고 있는 경우에 유용 합니다.  
  
- **코드에 중단점 설정**  
  
     코드에 간단한 중단점을 설정하려면 Visual Studio 편집기에서 소스 파일을 엽니다. 실행을 일시 중단 하려는 코드 줄에 커서를 설정 하 고 코드 창을 마우스 오른쪽 단추로 클릭 하 여 상황에 맞는 메뉴를 표시 하 고 **중단점/중단점 삽입** 을 선택 하거나 **F9**키를 누릅니다. 디버거는 줄이 실행 되기 바로 전에 실행을 일시 중단 합니다.  
  
     ![중단점 설정](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Visual Studio에서 중단점은 조건부 중단점 및 추적점과 같은 다양한 추가 기능을 제공합니다. [중단점 사용](../debugger/using-breakpoints.md)을 참조 하세요.  
  
- **커서 위치까지 실행**  
  
     커서 위치까지 실행하려면 소스 창에서 실행 가능한 코드 줄에 커서를 놓습니다. 편집기의 상황에 맞는 메뉴 (편집기에서 마우스 오른쪽 단추 클릭)에서 **커서까지 실행**을 선택 합니다. 이는 임시 중단점을 설정 하는 것과 같습니다.  
  
- **수동으로 코드 중단**  
  
     실행 중인 응용 프로그램의 사용 가능한 다음 코드 줄에서 중단하려면 **디버그**, **모두 중단** 을 선택합니다(키보드: **Ctrl+Alt+Break**).  
  
     해당 소스 또는 기호(.pdb) 파일 없이 코드를 실행하는 동안 중단하는 경우 디버거에서 적절한 파일을 찾는 데 도움이 될 수 있는 **소스 파일을 찾을 수 없음** 또는 **기호를 찾을 수 없음** 페이지가 표시됩니다. [기호 (.pdb) 및 소스 파일 지정을](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)참조 하세요. 지원 파일에 액세스할 수 없는 경우에도 디스어셈블리 창에서 어셈블리 명령을 디버깅할 수 있습니다.  
  
- **호출 스택에 있는 함수까지 실행**  
  
     디버깅 하는 동안 사용할 수 있는 **호출 스택** 창에서 함수를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **커서까지 실행**을 선택 합니다. 호출 스택을 시각적으로 추적하려면 [디버깅하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)를 참조하세요.  
  
- **이름으로 지정된 함수까지 실행**  
  
     지정 된 함수에 도달할 때까지 응용 프로그램을 실행 하도록 디버거에 지시할 수 있습니다. 함수 이름을 지정하거나 호출 스택에서 함수를 선택할 수 있습니다.  
  
     함수 이름을 지정하려면 **디버그**, **새 중단점**, **함수에서 중단**을 선택한 다음 함수의 이름과 기타 식별 정보를 입력합니다.  
  
     ![새 중단점 대화 상자](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     함수가 오버로드되거나 여러 네임스페이스에 있는 경우 **중단점 선택** 대화 상자에서 원하는 함수를 선택할 수 있습니다.  
  
     ![중단점 선택 대화 상자](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> 포인터를 이동하여 실행 흐름 변경  
 디버거가 일시 중지 된 동안 명령 포인터를 이동 하 여 실행할 코드의 다음 문을 설정할 수 있습니다. 소스 또는 디스어셈블리 창의 여백에 있는 노란색 화살표는 다음에 실행할 문의 위치를 나타냅니다. 코드의 일부를 건너뛰거나 이전에 실행한 줄로 돌아가려면 이 화살표를 이동합니다. 알려진 버그를 포함하는 코드 섹션을 건너뛰려는 경우 등에 이 방법을 사용할 수 있습니다.  
  
 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 다음에 실행할 문을 설정하려면 다음 절차 중 하나를 사용합니다.  
  
- 소스 창에서 노랑 화살표를 같은 소스 파일에서 다음 문을 설정할 위치로 끌어 놓습니다.  
  
- 소스 창에서 실행 하려는 줄에 커서를 설정 하 고 마우스 오른쪽 단추를 클릭 한 다음 **다음 문 설정**을 선택 합니다.  
  
- 디스어셈블리 창에서 다음에 실행할 어셈블리 명령에 커서를 설정 하 고를 마우스 오른쪽 단추로 클릭 한 **다음 다음 문 설정**을 선택 합니다.  
  
> [!CAUTION]
> 다음 문을 설정하면 프로그램 카운터가 새 위치로 바로 이동하게 됩니다. 이 명령은 주의해서 사용해야 합니다.  
> 
> - 기존 실행 위치와 새 실행 위치 사이에서는 명령이 실행되지 않습니다.  
>   - 실행 위치를 뒤로 이동하면 그 사이에서 실행된 명령이 실행 취소되지 않습니다.  
>   - 다음 문을 다른 함수나 범위로 이동하면 호출 스택이 손상되어 런타임 오류나 예외가 발생할 수 있습니다. 다음 문을 다른 범위로 이동하려고 하면 디버거에서 대화 상자가 열리고 여기서 작업을 취소할 수 있습니다. Visual Basic의 경우 다음 문을 다른 범위나 함수로 이동할 수 없습니다.  
>   - 네이티브 C++에서 런타임 검사를 활성화한 경우 다음 문을 설정하면 실행이 메서드의 끝에 도달할 때 예외가 throw될 수 있습니다.  
>   - 편집하며 계속하기를 활성화한 경우 편집하며 계속하기에서 즉시 다시 매핑할 수 없는 종류의 편집을 수행하면 **다음 문 설정** 이 실패합니다. 예를 들어 catch 블록 내의 코드를 편집하면 이 문제가 발생합니다. 이 경우 작업이 지원되지 않음을 알리는 오류 메시지가 나타납니다.  
> 
> [!NOTE]
> 관리 코드의 경우 다음과 같은 조건에서는 다음 문을 이동할 수 없습니다.  
> 
> - 다음 문이 현재 문과 다른 메서드에 있는 경우  
>   - Just-In-Time 디버깅을 사용하여 디버깅을 시작한 경우  
>   - 호출 스택 해제를 진행 중인 경우  
>   - System.StackOverflowException 또는 System.Threading.ThreadAbortException 예외가 throw된 경우  
  
 애플리케이션을 실행하는 동안에는 다음 문을 설정할 수 없습니다. 다음에 실행할 문을 설정하려면 디버거가 중단 모드에 있어야 합니다.  
  
## <a name="step-into-non-user-code"></a>사용자가 아닌 코드를 한 단계씩 코드 실행  
 기본적으로 디버거는 디버깅 하는 동안 앱 코드만 표시 하 고 *내 코드만*이라는 디버거 설정에 의해 결정 됩니다. 다양 한 프로젝트 형식 및 언어에 대해 작동 하는 방법 및 동작을 사용자 지정 하는 방법을 보려면 [내 코드만](../debugger/just-my-code.md) 를 참조 하세요. 그러나 디버그 하는 동안에는 프레임 워크 코드, 타사 라이브러리 코드 또는 운영 체제 (시스템 호출)에 대 한 호출을 확인 하는 것이 좋습니다.  
  
 **도구**  /  **옵션**  /  **디버깅** 으로 이동 하 고 **내 코드만 사용** 확인란의 선택을 취소 하 여 내 코드만를 해제할 수 있습니다.  
  
 내 코드만 사용 하지 않도록 설정 된 경우 디버거는 사용자 코드가 아닌 코드를 한 단계씩 실행 하 고 디버거 창에 사용자 코드가 아닌 코드를 표시할 수 있습니다.  
  
> [!NOTE]
> 디바이스 프로젝트에 대해서는 내 코드만 옵션이 지원되지 않습니다.  
  
 **한 단계씩 시스템 호출 실행**  
  
 시스템 코드에 대 한 디버깅 기호를 로드 하 고 내 코드만을 사용할 수 없는 경우 다른 모든 호출과 마찬가지로 시스템 호출을 한 단계씩 실행 할 수 있습니다.  
  
 Microsoft 기호 파일에 액세스 하려면 기호 서버를 사용 하 여 기호 파일 [(.pdb) 및 소스 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) 항목에서 [로컬 컴퓨터에 없는 기호 파일 찾기](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) 를 참조 하세요.  
  
 디버깅하는 동안 특정 시스템 구성 요소에 대한 기호를 로드하려면  
  
1. 모듈 창을 엽니다(키보드: **Ctrl+Alt+U**).  
  
2. 기호를 로드하려는 모듈을 선택합니다.  
  
     **기호 상태** 열을 보면 기호가 로드된 모듈을 확인할 수 있습니다.  
  
3. 상황에 맞는 메뉴에서 **기호 로드** 를 선택합니다.  
  
## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 한 단계씩 관리 코드의 속성 및 연산자 실행  
 기본적으로 디버거는 관리 코드의 속성과 연산자를 건너뜁니다. 대부분의 경우 이렇게 하면 더 나은 디버깅 환경이 제공됩니다. 속성이나 연산자를 한 단계씩 실행하려면 **디버그** / **옵션**을 선택합니다. **디버깅**  /  **일반** 페이지에서 **속성 및 연산자 건너뛰기 (관리 전용)** 확인란의 선택을 취소 합니다.
