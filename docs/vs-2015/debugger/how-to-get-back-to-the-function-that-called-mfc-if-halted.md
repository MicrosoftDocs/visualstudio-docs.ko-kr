---
title: '방법: 중단 된 경우 MFC를 호출한 함수로 돌아가기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c19cbf6e892ba8b35f2b92ad9b86aa0b74a64810
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685879"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>방법: 중지된 경우 MFC를 호출한 함수로 돌아가기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 도구 메뉴에서 설정 가져오기 및 내보내기를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.  
  
 **디버그** 메뉴의 **중단** 명령을 사용하여 프로그램을 중단했을 때 MFC에서 중지되었고 코드에 문제가 있다고 판단되면 호출 스택 창을 사용하여 함수로 되돌아갈 수 있습니다. 자세한 내용은 [방법: 호출 스택 창 사용](../debugger/how-to-use-the-call-stack-window.md)을 참조하세요.  
  
 때로는 코드가 메시지 펌프에서 손상될 수도 있습니다. 그럴 경우 호출 스택에는 사용자 코드가 들어 있지 않습니다. 이 문제가 발생하지 않도록 하려면 **중단** 명령 대신 중단점을 사용합니다. 이 경우 조건 및 적중 횟수도 함께 사용할 수 있습니다. 자세한 내용은 [중단점 및 추적점](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)(영문)을 참조 하세요.  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>MFC를 호출한 함수를 탐색하려면  
  
- **호출 스택** 창을 사용합니다.  
  
## <a name="see-also"></a>관련 항목  
 [네이티브 코드 디버그 Faq](../debugger/debugging-native-code-faqs.md)   
 [네이티브 코드 디버그](../debugger/debugging-native-code.md)
