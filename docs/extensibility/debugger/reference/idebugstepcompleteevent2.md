---
description: 이 인터페이스는 디버깅 중인 프로그램에서 한 단계씩 코드 실행, 프로시저 단위 실행 또는 소스 코드 또는 문 또는 명령의 한 단계씩 코드 실행이 완료 되 면 디버그 엔진 (DE)에서 세션 디버그 관리자 (SDM)로 보냅니다.
title: IDebugStepCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStepCompleteEvent2
helpviewer_keywords:
- IDebugStepCompleteEvent2 interface
ms.assetid: eba2b76e-f90d-486b-ae5c-c47f1b8ba2e5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38791456500fc5996345314a0a779f5ccd03d940
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053193"
---
# <a name="idebugstepcompleteevent2"></a>IDebugStepCompleteEvent2
이 인터페이스는 디버깅 중인 프로그램에서 한 단계씩 코드 실행, 프로시저 단위 실행 또는 소스 코드 또는 문 또는 명령의 한 단계씩 코드 실행이 완료 되 면 디버그 엔진 (DE)에서 세션 디버그 관리자 (SDM)로 보냅니다.

## <a name="syntax"></a>구문

```
IDebugStepCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE는이 인터페이스를 구현 하 여 단계 작업의 완료를 보고 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 `IDebugEvent2` 인터페이스에 액세스 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 DE는이 이벤트 개체를 만들어 단계 작업 완료를 보고 합니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여 보냅니다.

## <a name="remarks"></a>설명
 단계가 완료 되 면 디버깅 중인 프로그램이 더 이상 일시 중지 되 고 IDE에서 모든 창을 업데이트 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
