---
title: '방법: 호출 스택 창에 네이티브 프레임이 없을 때 관리 코드에서 실행 | Microsoft Docs'
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
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63bd55fd254dd263540a9161e8579ea6600e97f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690097"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>방법: 호출 스택 창에 네이티브 프레임이 없을 때 관리 코드에서 나가기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**호출 스택** 창에 표시되지 않는 네이티브 프레임이 코드에 있는 경우 관리 코드에서 나가면 예기치 않은 결과가 발생할 수 있습니다. **프로시저 나가기** 대신 중단점을 사용하면 이 문제를 해결할 수 있습니다.  
  
> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>네이티브 프레임이 호출 스택 화면에서 없어질 때 관리 코드에 대해 프로시저 나가기를 수행하려면  
  
1. 네이티브 코드에서 호출 후의 위치 중단점을 관리 코드로 설정합니다.  
  
2. **디버그** 메뉴에서 **계속**을 선택합니다.  
  
     관리되는 호출이 완료되면 네이티브 코드의 중단점에서 실행이 중지됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [방법: 호출 스택 창 사용](../debugger/how-to-use-the-call-stack-window.md)
