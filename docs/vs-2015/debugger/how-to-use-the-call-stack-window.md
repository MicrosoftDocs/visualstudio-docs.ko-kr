---
title: '방법: 호출 스택 창 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 84c0bfead1633da13b4284cad04ace674045b057
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697481"
---
# <a name="how-to-use-the-call-stack-window"></a>방법: 호출 스택 창 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**호출 스택** 창에서 현재 스택에 있는 함수 또는 프로시저 호출을 볼 수 있습니다.  
  
 **호출 스택** 창에는 각 함수의 이름과 해당 함수가 작성 된 프로그래밍 언어가 표시 됩니다. 함수 또는 프로시저 이름 다음에는 모듈 이름, 줄 번호 및 매개 변수의 이름, 형식, 값 등의 선택적 정보가 표시될 수 있습니다. 이러한 선택적 정보의 표시 여부를 선택할 수 있습니다.  
  
 노란색 화살표는 현재 실행 포인터가 있는 스택 프레임을 나타냅니다. 기본적으로 소스, **디스어셈블리**, **지역**, **조사식**및 **자동** 창에 해당 정보가 표시 되는 프레임입니다. 컨텍스트를 스택의 다른 프레임으로 변경 하려면 **호출 스택** 창에서이 작업을 수행할 수 있습니다.  
  
 호출 스택의 일부에 대해 디버깅 기호를 사용할 수 없는 경우 호출 **스택** 창에서 호출 스택의 해당 부분에 대 한 올바른 정보를 표시 하지 못할 수 있습니다. 다음과 같이 출력됩니다.  
  
 [아래 프레임은 올바르지 않거나 누락되었거나 name.dll에 대해 로드된 기호가 없음]  
  
 관리 코드에서는 기본적으로입니다. **호출 스택** 창에서 사용자가 사용 하지 않는 코드에 대 한 정보를 숨깁니다. 숨겨진 정보 대신 다음과 같이 출력됩니다.  
  
 **[\<External Code>]**  
  
 사용자가 작성하지 않은 코드는 "내 코드"가 아닌 모든 코드를 의미합니다. 바로 가기 메뉴를 사용하여 사용자가 작성하지 않은 코드에 대한 호출 스택 정보를 표시하도록 선택할 수 있습니다.  
  
 바로 가기 메뉴를 사용하면 스레드 간의 호출 표시 여부를 선택할 수 있습니다.  
  
> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 실제 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기**를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>중단 모드 또는 실행 모드에서 호출 스택 창을 표시하려면  
  
- **디버그** 메뉴에서 **창** 을 선택한 다음 **호출 스택**을 클릭 합니다.  
  
### <a name="to-change-the-optional-information-displayed"></a>표시된 선택적 정보를 변경하려면  
  
- **호출 스택** 창을 마우스 오른쪽 단추로 클릭 하 고 **표시 \<**_the information that you want_**> **를 설정 하거나 선택 취소 합니다.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>사용자가 작성하지 않은 코드 프레임을 호출 스택 창에 표시하려면  
  
- **호출 스택** 창에서 마우스 오른쪽 단추를 클릭하고 **외부 코드 표시**를 선택합니다.  
  
### <a name="to-switch-to-another-stack-frame"></a>다른 스택 프레임으로 전환하려면  
  
1. **호출 스택** 창에서 보려는 코드와 데이터가 포함 된 프레임을 마우스 오른쪽 단추로 클릭 합니다.  
  
2. **프레임으로 전환**을 선택합니다.  
  
     선택한 프레임 옆에 끝이 굽은 녹색 화살표가 나타납니다. 실행 포인터는 여전히 노란색 화살표로 표시되어 있는 원래 프레임에 그대로 있습니다. **디버그** 메뉴에서 **한 단계 실행** 또는 **계속**을 선택하면 선택한 프레임이 아닌 원래 프레임에서 실행이 계속됩니다.  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>다른 스레드에서의 호출 또는 다른 스레드로의 호출을 표시하려면  
  
- **호출 스택** 창을 마우스 오른쪽 단추로 클릭하고 **다른 스레드로 호출/다른 스레드에서 호출 포함**을 선택합니다.  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>호출 스택에 있는 함수의 소스 코드를 보려면  
  
- **호출 스택** 창에서 소스 코드를 보려는 함수를 마우스 오른쪽 단추로 클릭하고 **소스 코드로 이동**을 선택합니다.  
  
### <a name="to-visually-trace-the-call-stack"></a>호출 스택을 시각적으로 추적하려면  
  
1. **호출 스택** 창에서 바로 가기 메뉴를 엽니다. **코드 맵에 호출 스택 표시를**선택 합니다. (키보드: **CTRL**  +  **SHIFT**  +  **`** )  
  
     [디버깅 하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)를 참조 하세요.  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>호출 스택에 있는 함수의 디스어셈블리 코드를 보려면  
  
- **호출 스택** 창에서 디스어셈블리 코드를 보려는 함수를 마우스 오른쪽 단추로 클릭하고 **디스어셈블리로 이동**을 선택합니다.  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>호출 스택 창에서 특정 함수까지 실행하려면  
  
- **호출 스택** 창에서 함수를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **커서까지 실행**을 선택 합니다.  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>함수 호출의 종료 지점에 중단점을 설정하려면  
  
- [Set a breakpoint at a call stack function](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window)(호출 스택 함수에서 중단점 설정)을 참조하세요.  
  
### <a name="to-load-symbols-for-a-module"></a>모듈의 기호를 로드하려면  
  
- **호출 스택** 창에서 기호를 다시 로드 하려는 모듈이 표시 된 프레임을 마우스 오른쪽 단추로 클릭 하 고 **기호 로드**를 선택 합니다.  
  
## <a name="loading-symbols"></a>기호 로드  
 **호출 스택** 창에서 현재 기호가 로드되어 있지 않은 코드에 대한 디버깅 기호를 로드할 수 있습니다. 이러한 기호는 Microsoft 공용 기호 서버에서 다운로드한 .NET Framework 또는 시스템 기호일 수도 있고 디버깅 중인 컴퓨터의 기호 경로에 있는 기호일 수도 있습니다.  
  
 [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.  
  
#### <a name="to-load-symbols"></a>기호를 로드하려면  
  
1. **호출 스택** 창에서 기호가 로드 되지 않은 프레임을 마우스 오른쪽 단추로 클릭 합니다. 프레임이 흐리게 표시됩니다.  
  
2. 다음 **에서 기호 로드** 를 가리킨 다음 **Microsoft 기호 서버** 또는 **기호 경로**를 클릭 합니다.  
  
#### <a name="to-set-the-symbol-path"></a>기호 경로를 설정하려면  
  
1. **호출 스택** 창의 바로 가기 메뉴에서 **기호 설정**을 선택합니다.  
  
     **옵션** 대화 상자가 열리고 **기호** 페이지가 표시됩니다.  
  
2. **기호 설정**을 클릭 합니다.  
  
3. **옵션** 대화 상자에서 폴더 아이콘을 클릭합니다.  
  
     **기호 파일(.pdb) 위치** 상자에 커서가 표시됩니다.  
  
4. 디버깅 중인 컴퓨터의 기호 위치에 대한 디렉터리 경로 이름을 입력합니다. 로컬 디버깅인 경우 이 컴퓨터는 로컬 컴퓨터이고 원격 디버깅인 경우 이 컴퓨터는 원격 컴퓨터입니다.  
  
5. **확인**을 클릭하여 **옵션** 대화 상자를 닫습니다.  
  
## <a name="see-also"></a>관련 항목  
 [호출 스택 창의 혼합 코드 및 누락 된 정보](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [방법: 디버거 창의 숫자 형식 변경](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)   
 [기호 (.pdb) 및 소스 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [중단점 사용](../debugger/using-breakpoints.md)
