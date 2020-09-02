---
title: 편집 하며 계속 하기 오류 메시지 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5437ef982309ef8595f08283f2685e93d346e764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428299"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>편집하며 계속하기 오류 메시지 대화 상자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 대화 상자는 편집 하며 계속 하기를 지 원하는 언어로 디버그할 때 표시 되지만 **편집 하며 계속 하기** 는 코드 변경 형식에 사용할 수 없습니다. 대화 상자 안의 오류 메시지에서 보다 자세한 설명을 제공합니다. 이 대화 상자가 표시될 수 있는 원인은 다음과 같습니다.  
  
- 관리되지 않는 디버깅을 사용하도록 설정된 상태에서 관리 코드를 편집하려고 한 경우. 편집하며 계속하기는 혼합 모드 디버깅에서 작동하지 않습니다.  
  
- SQL Server 코드를 편집하려고 한 경우  
  
- Dr. Watson 덤프를 디버깅 하는 동안 코드를 편집 하려고 했습니다.  
  
- 처리 되지 않은 예외가 발생 한 후 코드를 편집 하려고 했지만 "**처리 되지 않은 예외에 대 한 호출 스택 해제**" 옵션이 선택 되지 않았습니다.  
  
- 포함된 런타임 애플리케이션을 디버깅하는 동안 코드를 편집하려고 한 경우  
  
- **디버그** 메뉴에서 시작 하는 대신 연결 된 프로그램의 코드를 편집 하려고 했습니다.  
  
- 최적화된 코드를 편집하려고 한 경우  
  
- 대상이 64비트 애플리케이션일 때 관리 코드를 편집하려고 한 경우. 편집하며 계속하기를 사용하려면 대상을 x86으로 설정해야 합니다. (*프로젝트* **속성**, **컴파일** 탭, **고급 컴파일러** 설정).  
  
- 디버깅하는 동안 수정하여 다시 로드한 어셈블리의 코드를 편집하려고 한 경우  
  
- 로드하지 않은 어셈블리의 코드를 편집하려고 한 경우  
  
- 새 버전에 빌드 오류가 있으므로 이전 버전의 애플리케이션을 디버깅하기 시작한 경우  
  
- 실행되고 있는 코드를 편집하려고 한 경우  
  
## <a name="uielement-list"></a>UI 요소 목록  
 **확인**  
 대화 상자를 종료하고 바로 전에 시도한 편집을 취소합니다.  
  
## <a name="see-also"></a>관련 항목  
 [지원되는 코드 변경(C++)](../debugger/supported-code-changes-cpp.md)
