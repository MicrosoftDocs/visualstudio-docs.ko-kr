---
title: '방법: 프로그램에서 충돌이 발생하는 DLL 찾기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 44ebe042ff6e2507530e4be410e768550e922b44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703623"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>방법: 프로그램에서 충돌이 발생하는 DLL 찾기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 도구 메뉴에서 설정 가져오기 및 내보내기를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.  
  
 시스템 DLL 또는 다른 사람의 코드를 호출하는 동안 애플리케이션에 충돌이 발생하면 충돌 발생 시 활성 상태였던 DLL을 찾아야 합니다. 사용자 프로그램 외부에서 DLL에 충돌이 발생하는 경우 **모듈** 창을 사용하여 위치를 확인할 수 있습니다.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>모듈 창을 사용하여 충돌이 발생한 위치를 찾으려면  
  
1. 충돌이 발생한 주소를 기록합니다.  
  
2. **디버그** 메뉴에서 **창**을 선택한 다음, **모듈**을 클릭합니다.  
  
3. **모듈** 창에서 **주소** 열을 찾습니다. 이 열을 표시하려면 스크롤 막대를 사용해야 할 수도 있습니다.  
  
4. 주소별로 DLL을 정렬하려면 열 맨 위에 있는 **주소** 단추를 클릭합니다.  
  
5. 정렬된 목록을 조사하여 충돌 위치가 속하는 주소 범위를 가진 DLL을 찾습니다.  
  
6. **이름** 및 **경로** 열에서 DLL 이름과 경로를 확인합니다.  
  
## <a name="see-also"></a>관련 항목  
 [방법: 네이티브 Dll 디버깅](../debugger/how-to-debug-native-dlls.md)   
 [방법: 모듈 창 사용](../debugger/how-to-use-the-modules-window.md)
