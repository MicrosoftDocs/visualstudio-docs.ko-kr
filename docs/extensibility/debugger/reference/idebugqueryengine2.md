---
title: 아이디버그쿼리엔진2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b1784055c54c9243237c81edb708e13de9bc5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720659"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
이 인터페이스를 사용하면 세션 디버그 관리자(SDM)가 DE버그 엔진(DE)을 나타내는 인터페이스를 검색할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 DE 자체의 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 인터페이스에 대한 액세스를 허용하기 위해 가장 일반적인 DE 인터페이스(예: [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)및 [IDebugStackFrame2)를](../../../extensibility/debugger/reference/idebugstackframe2.md)구현하는 개체에 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스를 얻으려면 일반적인 DE 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugQueryEngine2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|사용자 지정 디버그 엔진(DE) 인터페이스를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 일반적으로 함수를 통해 인과 관계 정렬 스테핑을 지원 하기 위해 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스를 구현 하는 개체에서 구현 됩니다. 즉, 디버거가 함수에서 벗어나면 실행할 다음 함수가 스택의 이전 함수가 아니라 다른 스레드의 함수일 수 있습니다. "인과 관계"에 대한 정의는 [Visual Studio 디버거 용어집을](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)참조하십시오.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
