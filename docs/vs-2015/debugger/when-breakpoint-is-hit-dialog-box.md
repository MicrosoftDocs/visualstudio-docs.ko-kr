---
title: 중단점이 적중될 때 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.whenbreakpointishit
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
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7cd140a22c435df0875c089a69476d3e1e61cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149418"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>중단점이 적중될 때 대화 상자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 대화 상자에서는 중단점이 적중될 때 발생하는 작업을 사용자 지정할 수 있습니다.  
  
## <a name="uielement-list"></a>UI 요소 목록  
 **메시지 인쇄**  
 DebuggerDisplay 구문을 사용 하 여 메시지를 출력 합니다. 자세한 내용은 [DebuggerDisplay 특성 사용](../debugger/using-the-debuggerdisplay-attribute.md)을 참조하세요.  
  
 이 텍스트 상자는 자체적으로 또는 DebuggerDisplay 식의 중괄호 안에 사용할 수 있는 특수 키워드(예: $ADDRESS)도 지원합니다. 사용 가능한 키워드는 대화 상자에 나열됩니다.  
  
 **실행 계속**  
 이 컨트롤은 **메시지 인쇄**를 선택한 경우에만 활성화됩니다. 이 컨트롤을 선택하면 위치 적중 시 중단하는 방법 대신 중단점을 추적점으로 사용하여 프로그램 실행을 추적할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [중단점 사용](../debugger/using-breakpoints.md)   
 [DebuggerDisplay 특성 사용](../debugger/using-the-debuggerdisplay-attribute.md)
