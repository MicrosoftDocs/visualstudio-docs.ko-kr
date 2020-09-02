---
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b423ee2cb95ad55296c452cfdc4b891ee4cd26a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723537"
---
# <a name="idebugprocess3"></a>IDebugProcess3
이 인터페이스는 실행 중인 프로세스와 해당 프로그램을 나타냅니다. 이 인터페이스는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스의 여러 메서드를 대체 하는 것으로 존재 합니다. 프로세스의 모든 프로그램에 대 한 제어를 제공 합니다.

> [!NOTE]
> [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)및 [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) 메서드는 더 이상 사용 되지 않으며 더 이상 사용 되지 않습니다. 대신 인터페이스에 해당 하는 메서드를 사용 `IDebugProcess3` 합니다.

## <a name="syntax"></a>Syntax

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스는 프로그램을 그룹으로 관리 하기 위해 사용자 지정 포트 공급자에 의해 구현 됩니다. 프로그램을 그룹으로 관리 하는 경우 실행을 제어 하 고 식 계산기에 대 한 언어를 설정할 수 있습니다. 이 인터페이스는 포트 공급자에 의해 구현 되어야 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는이 프로세스에서 식별 된 프로그램 그룹과 상호 작용 하기 위해 주로 세션 디버그 관리자 (SDM)에서 호출 됩니다.

 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) 를 호출 하 여이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)에서 상속 된 메서드 외에도 `IDebugProcess3` 는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|프로세스를 계속 실행 하거나 단계별로 실행 합니다.|
|[실행](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|프로세스의 실행을 시작 합니다.|
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|프로세스에서 하나의 명령 또는 문을 앞으로 이동 하는 단계입니다.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|디버깅을 위해 프로세스가 시작 된 이유를 가져옵니다.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|디버그 엔진이 적절 한 식 계산기를 로드할 수 있도록 호스팅 언어를 설정 합니다.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|이 프로세스에 대해 현재 설정 된 언어를 검색 합니다.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|이 프로세스에 대 한 편집 하며 계속 하기 (ENC)를 사용 하지 않도록 설정 합니다.<br /><br /> 사용자 지정 포트 공급자는이 메서드를 구현 하지 않습니다 .이 메서드는 항상를 반환 해야 `E_NOTIMPL` 합니다.|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|이 프로세스에 대 한 ENC 상태를 가져옵니다.<br /><br /> 사용자 지정 포트 공급자는이 메서드를 구현 하지 않습니다 .이 메서드는 항상를 반환 해야 `E_NOTIMPL` 합니다.|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|사용 가능한 디버그 엔진에 대 한 고유 식별자 배열을 검색 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
