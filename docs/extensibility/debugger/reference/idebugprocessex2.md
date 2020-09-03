---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 743dd1aa72d9b8db6b848618c8a2ad6c8c8ecaaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723333"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
이 인터페이스를 사용 하면 세션 디버그 관리자 (SDM)가 프로세스에 연결 하거나 프로세스에서 분리 하는 프로세스를 알릴 수 있습니다.

## <a name="syntax"></a>Syntax

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 사용자 지정 포트 공급자는 다음과 같은 작업을 위해 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 인터페이스와 동일한 개체에서이 인터페이스를 구현 합니다.

- 프로세스에 연결 된 세션 추적 지원

- 여러 디버그 엔진에서 자동 연결 지원

  사용자 지정 포트 공급자가를 선택 하는 경우이 인터페이스를 구현할 수 있습니다.

## <a name="notes-for-callers"></a>호출자 참고 사항

- SDM은 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) `IDebugProcess2` 를 호출 하 여이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProcessEx2` .

|메서드|설명|
|------------|-----------------|
|[연결](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|현재 세션에서 프로세스를 디버깅 하 고 있음을 프로세스에 알립니다.|
|[분리](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|세션에서 프로세스를 더 이상 디버깅 하지 않음을 프로세스에 알립니다.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|디버그 엔진의 목록에 대 한 프로그램 노드를 추가 합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 SDM과 프로세스 사이에서 전용입니다.

## <a name="requirements"></a>요구 사항
 헤더: Portpriv. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
