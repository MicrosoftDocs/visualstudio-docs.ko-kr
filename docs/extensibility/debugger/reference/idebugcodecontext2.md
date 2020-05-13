---
title: 아이디버그코드컨텍스트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 778602cc29049d855c418fd8fa416feb1ad8e9fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734216"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
이 인터페이스는 코드 명령의 시작 위치를 나타냅니다. 오늘날 대부분의 런타임 아키텍처의 경우 코드 컨텍스트는 프로그램의 실행 스트림에서 주소로 간주될 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진은 코드 명령의 위치를 문서 위치와 연관시키기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 많은 인터페이스의 메서드는 이 인터페이스를 반환합니다( 가장 일반적으로 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). 또한 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 인터페이스뿐만 아니라 중단점 해결 정보와 함께 광범위하게 사용됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|활성 코드 컨텍스트에 해당하는 문서 컨텍스트를 가져옵니다.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|이 코드 컨텍스트에 대한 언어 정보를 가져옵니다.|

## <a name="remarks"></a>설명
 인터페이스와 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 인터페이스의 주요 차이점은 항상 `IDebugCodeContext2` 명령이 정렬되어 있다는 것입니다. `IDebugCodeContext2` 즉, 명령은 `IDebugCodeContext2` 항상 명령의 시작을 가리키는 반면 `IDebugMemoryContext2` 런타임 아키텍처에서 메모리 바이트를 가리킬 수 있습니다. `IDebugCodeContext2`기본 저장소 크기(일반적으로 바이트)가 아니라 지침에 의해 증가됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
