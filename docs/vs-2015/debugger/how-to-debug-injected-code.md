---
title: '방법: 삽입한 코드 디버그 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df35a25534961c6ab94891d2da6fe54f05c37a3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681083"
---
# <a name="how-to-debug-injected-code"></a>방법: 삽입한 코드 디버그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 도구 메뉴에서 설정 가져오기 및 내보내기를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.  
  
 특성을 사용하면 C++ 프로그래밍을 매우 단순화할 수 있습니다. 자세한 내용은 [개념](https://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e)을 참조하세요. 일부 특성은 컴파일러가 직접 해석합니다. 프로그램 소스에 코드를 삽입하여 컴파일러가 컴파일할 수 있게 하는 특성도 있습니다. 이렇게 코드를 삽입하면 프로그래머가 써야 하는 코드의 양이 줄어들어 보다 쉽게 프로그래밍할 수 있습니다. 그러나 때때로 버그가 발생하여 삽입된 코드를 실행하는 동안 애플리케이션에 문제가 생기기도 합니다. 이런 경우에는 삽입된 코드를 볼 수 있습니다. Visual Studio에서는 두 가지 방법으로 삽입된 코드를 볼 수 있습니다.  
  
- **디스어셈블리** 창에서 삽입된 코드를 볼 수 있습니다.  
  
- [/Fx](https://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560)를 사용하여 원래 코드와 삽입된 코드가 병합된 원본 파일을 만들 수 있습니다.  
  
  **디스어셈블리** 창에는 소스 코드와 특성에 의해 삽입된 코드에 대한 어셈블리 언어 명령이 표시됩니다. 또한 **디스어셈블리** 창에 소스 코드 주석이 표시될 수도 있습니다.  
  
### <a name="to-turn-on-source-annotation"></a>소스 주석을 설정하려면  
  
- **디스어셈블리** 창에서 마우스 오른쪽 단추를 클릭하고 바로 가기 메뉴에서 **소스 코드 표시**를 선택합니다.  
  
     소스 창에 있는 특성의 위치를 알면 바로 가기 메뉴를 사용하여 **디스어셈블리** 창에서 삽입된 코드를 찾을 수 있습니다.  
  
### <a name="to-view-injected-code"></a>삽입된 코드를 보려면  
  
1. 디버거는 중단 모드에 있어야 합니다.  
  
2. 소스 코드 창에서 보려는 삽입된 코드의 특성 앞에 커서를 놓습니다.  
  
3. 마우스 오른쪽 단추를 클릭하여 바로 가기 메뉴에서 **디스어셈블리로 이동**을 선택합니다.  
  
     특성이 현재 실행 위치와 가까이 있으면 **디버그** 메뉴에서 **디스어셈블리** 창을 선택할 수 있습니다.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>현재 실행 위치에서 디스어셈블리 코드를 보려면  
  
1. 디버거는 중단 모드에 있어야 합니다.  
  
2. **디버그** 메뉴에서 **창**을 선택하고 **디스어셈블리**를 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 보안](../debugger/debugger-security.md)   
 [네이티브 코드 디버그](../debugger/debugging-native-code.md)
