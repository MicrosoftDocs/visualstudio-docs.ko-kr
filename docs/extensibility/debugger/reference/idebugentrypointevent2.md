---
description: 디버그 엔진 (DE)은 프로그램이 사용자 코드의 첫 번째 명령을 실행 하려고 할 때이 인터페이스를 세션 디버그 관리자 (SDM)로 보냅니다.
title: IDebugEntryPointEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da733292407c93327374a4c6fa54c558d3202caa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153393"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
디버그 엔진 (DE)은 프로그램이 사용자 코드의 첫 번째 명령을 실행 하려고 할 때이 인터페이스를 세션 디버그 관리자 (SDM)로 보냅니다.

## <a name="syntax"></a>Syntax

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE는 정상적인 작업의 일부로이 인터페이스를 구현 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 `IDebugEvent2` 인터페이스에 액세스 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 디버그 중인 프로그램이 로드 되 고 사용자 코드의 첫 번째 명령을 실행할 준비가 되 면 DE는이 이벤트 개체를 만들고 보냅니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여 보냅니다.

## <a name="remarks"></a>설명
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 는 프로그램이 가장 먼저 명령을 실행 하려고 할 때 전송 됩니다. 예를 들어 `IDebugEntryPoint2` 는 프로그램이 사용자의 함수를 실행 하려고 할 때 전송 됩니다 `main` .

 DE가 전송 되 면 `IDebugEntryPointEvent2` 현재 코드 위치가 사용자 코드의 첫 번째 명령 (예:)에 있어야 합니다 `main` .

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
