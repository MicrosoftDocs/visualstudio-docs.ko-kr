---
title: '연습: 디자인 타임에 디버깅 | Microsoft Docs'
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
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54466cc3561c194199bbad2b35cd00433da2b0f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149423"
---
# <a name="walkthrough-debugging-at-design-time"></a>연습: 디자인 타임에 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

응용 프로그램이 실행 되 고 있지 않을 때 Visual Studio **직접** 실행 창을 사용 하 여 함수나 서브루틴을 실행할 수 있습니다. 함수나 서브루틴이 중단점을 포함 하는 경우 Visual Studio는 적절 한 지점에서 실행을 중단 합니다. 그런 다음 디버거 창을 사용하여 프로그램 상태를 조사할 수 있습니다. 이 기능을 ‘디자인 타임에 디버깅’이라고 합니다.  
  
 다음 절차에서는이 기능을 사용 하는 방법을 보여 줍니다.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>직접 실행 창에서 중단점을 적중 하려면  
  
1. Visual Basic 콘솔 응용 프로그램에 다음 코드를 붙여 넣습니다.  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2. 를 읽는 줄에 중단점을 설정 `s="Add BreakPoint Here"` 합니다.  
  
3. **직접 실행** 창에 다음을 입력 합니다.`?MyFunction<enter>`  
  
4. 중단점이 적중 되었으며 호출 스택이 정확한 지 확인 합니다.  
  
5. **디버그** 메뉴에서 **계속**을 클릭 하 고 여전히 디자인 모드에 있는지 확인 합니다.  
  
6. **직접 실행** 창에 다음을 입력 합니다.`?MyFunction<enter>`  
  
7. **직접 실행** 창에 다음을 입력 합니다.`?MySub<enter>`  
  
8. 중단점에 도달 했는지 확인 하 고 `i` **지역** 창에서 정적 변수의 값을 검사 합니다. 값은 3 이어야 합니다.  
  
9. 호출 스택이 정확한 지 확인 합니다.  
  
10. **디버그** 메뉴에서 **계속**을 클릭 하 고 여전히 디자인 모드에 있는지 확인 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 보안](../debugger/debugger-security.md)   
 [디버거 기본 사항](../debugger/debugger-basics.md)
