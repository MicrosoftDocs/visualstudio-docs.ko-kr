---
title: 아이디버그프로세스3 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723537"
---
# <a name="idebugprocess3"></a>IDebugProcess3
이 인터페이스는 실행 중인 프로세스와 해당 프로그램을 나타냅니다. 이 인터페이스는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스의 여러 메서드를 대체합니다. 프로세스의 모든 프로그램을 제어할 수 있습니다.

> [!NOTE]
> [계속](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [실행](../../../extensibility/debugger/reference/idebugprogram2-execute.md)및 [단계](../../../extensibility/debugger/reference/idebugprogram2-step.md) 메서드는 더 이상 사용되지 않으며 더 이상 사용되지 않아야 합니다. 대신 인터페이스에서 해당 `IDebugProcess3` 메서드를 사용합니다.

## <a name="syntax"></a>구문

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 사용자 지정 포트 공급자가 프로그램을 그룹으로 관리하기 위해 구현합니다. 프로그램이 그룹으로 관리되는 경우 해당 프로그램을 제어하고 식 평가기의 언어를 설정할 수 있습니다. 이 인터페이스는 포트 공급자가 구현해야 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 주로 이 프로세스에서 식별된 프로그램 그룹과 상호 작용하기 위해 세션 디버그 관리자(SDM)에 의해 호출됩니다.

 이 인터페이스를 가져오려면 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 인터페이스에서 [쿼리인터페이스를](/cpp/atl/queryinterface) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugProcess2에서](../../../extensibility/debugger/reference/idebugprocess2.md)상속된 메서드 외에도 `IDebugProcess3` 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[계속](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|프로세스의 실행 또는 단계적 실행을 계속합니다.|
|[실행](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|프로세스 실행을 시작합니다.|
|[단계](../../../extensibility/debugger/reference/idebugprocess3-step.md)|프로세스에서 하나의 명령또는 문을 전달합니다.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|디버깅을 위해 프로세스가 시작된 이유를 가져옵니다.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|디버그 엔진이 적절한 식 계산기에서 로드할 수 있도록 호스팅 언어를 설정합니다.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|이 프로세스에 대해 현재 설정된 언어를 검색합니다.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|이 프로세스에 대해 ENC(편집 및 계속)를 사용하지 않도록 설정합니다.<br /><br /> 사용자 지정 포트 공급자는 이 메서드를 `E_NOTIMPL`구현하지 않습니다(항상 반환해야 합니다).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|이 프로세스에 대한 ENC 상태를 가져옵니다.<br /><br /> 사용자 지정 포트 공급자는 이 메서드를 `E_NOTIMPL`구현하지 않습니다(항상 반환해야 합니다).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|사용 가능한 디버그 엔진에 대한 고유 식별자 배열을 검색합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
