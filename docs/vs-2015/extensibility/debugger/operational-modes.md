---
title: 운영 모드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4009ab6268140117c8fd1294adcc52ac347b799
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153716"
---
# <a name="operational-modes"></a>작업 모드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음과 같이 IDE에서 작동할 수 있는 세 가지 모드가 있습니다.  
  
- [디자인 모드](#vsconoperationalmodesanchor1)  
  
- [실행 모드](#vsconoperationalmodesanchor2)  
  
- [중단 모드](#vsconoperationalmodesanchor3)  
  
  이러한 모드 간의 사용자 지정 디버그 엔진 (DE) 전환 방식은 전환 메커니즘을 잘 알고 있어야 하는 구현 결정입니다. DE는 이러한 모드를 직접 구현할 수도 있고 그렇지 않을 수도 있습니다. 이러한 모드는 사용자 작업 또는 DE의 이벤트를 기반으로 전환 하는 디버그 패키지 모드입니다. 예를 들어 실행 모드에서 중단 모드로 전환 하는 것은 DE의 중지 이벤트에 의해 간섭 됩니다. 단계 또는 실행과 같은 작업을 수행 하는 사용자는 중단에서 실행 모드 또는 단계 모드로의 전환이 간섭 됩니다. 전환에 대 한 자세한 내용은 [실행 제어](../../extensibility/debugger/control-of-execution.md)를 참조 하세요.  
  
## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> 디자인 모드  
 디자인 모드는 Visual Studio 디버깅의 실행 중이 아닌 상태 이며,이 기간 동안에는 응용 프로그램에서 디버깅 기능을 설정할 수 있습니다.  
  
 디자인 모드에서는 몇 가지 디버깅 기능만 사용 됩니다. 개발자는 중단점을 설정 하거나 조사식 식을 만들도록 선택할 수 있습니다. IDE가 디자인 모드에 있는 동안에는 DE-DE가 로드 되거나 호출 되지 않습니다. DE와의 상호 작용은 실행 및 중단 모드 에서만 발생 합니다.  
  
## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> 실행 모드  
 실행 모드는 IDE의 디버깅 세션에서 프로그램이 실행 될 때 발생 합니다. 응용 프로그램은 중단점이 적중 되거나 예외가 throw 될 때까지 종료 될 때까지 실행 됩니다. 응용 프로그램을 종료 하기 위해 실행 하면 DE-DE가 디자인 모드로 전환 됩니다. 중단점이 적중 되거나 예외가 throw 되 면 DE는 중단 모드로 전환 됩니다.  
  
## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> 중단 모드  
 중단 모드는 디버깅 프로그램의 실행이 일시 중단 될 때 발생 합니다. 중단 모드는 개발자가 중단 시 응용 프로그램의 스냅숏을 제공 하 고 개발자가 응용 프로그램의 상태를 분석 하 고 응용 프로그램의 실행 방법을 변경할 수 있도록 합니다. 개발자는 코드를 보고 편집 하 고, 데이터를 검사 하거나 수정 하 고, 응용 프로그램을 다시 시작 하거나, 실행을 종료 하거나, 동일한 지점에서 계속 실행할 수 있습니다.  
  
 해제 모드는 DE-DE가 동기 중지 이벤트를 보낼 때 입력 됩니다. 이벤트 중지 라고도 하는 동기 중지 이벤트는 디버깅 중인 응용 프로그램에서 코드 실행이 중지 되었음을 세션 디버그 관리자 (SDM) 및 IDE에 알립니다. [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 및 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 인터페이스는 이벤트 중지의 예입니다.  
  
 중단 모드에서 실행 또는 단계 모드로 디버거를 전환 하는 다음 메서드 중 하나를 호출 하 여 이벤트 중지를 계속 합니다.  
  
- [실행](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
- [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
- [계속](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> 단계 모드  
 단계 모드는 프로그램에서 다음 코드 줄을 단계별로 실행 하거나 함수에서 다음 줄로 이동 하거나 함수를 건너뛸 때 발생 합니다. 메서드 [단계](../../extensibility/debugger/reference/idebugprocess3-step.md)를 호출 하 여 단계를 실행 합니다. 이 메서드에 `DWORD` 는 [stunit](../../extensibility/debugger/reference/stepunit.md) 및 [stkind](../../extensibility/debugger/reference/stepkind.md) 열거형을 입력 매개 변수로 지정 하는가 필요 합니다.  
  
 프로그램에서 코드의 다음 줄 또는 함수에 대 한 단계를 성공적으로 실행 하거나 커서 또는 설정 된 중단점까지 실행 하면 DE가 자동으로 중단 모드로 전환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [실행 제어](../../extensibility/debugger/control-of-execution.md)
