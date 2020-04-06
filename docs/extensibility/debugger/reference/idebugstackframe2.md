---
title: 아이디버그스택프레임2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37acb9f2984c36130de494108ef4b76a59cc74e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719508"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
이 인터페이스는 특정 스레드의 호출 스택에서 단일 스택 프레임을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 스택 프레임을 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 인터페이스를 검색하려면 [EnumFrameInfo를](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 호출합니다. [다음을](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) 호출하여 인터페이스가 포함된 `IDebugStackFrame2` [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조를 검색합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugStackFrame2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|이 스택 프레임에 대한 코드 컨텍스트를 가져옵니다.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|이 스택 프레임에 대한 문서 컨텍스트를 가져옵니다.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|스택 프레임의 이름을 가져옵니다.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|스택 프레임에 대한 설명을 가져옵니다.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|스택 프레임과 연결된 물리적 주소 범위의 컴퓨터 종속 표현을 가져옵니다.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|스택 프레임 및 스레드의 현재 컨텍스트 내에서 식 평가를 수행하기 위한 평가 컨텍스트를 가져옵니다.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|스택 프레임과 연결된 언어를 가져옵니다.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|스택 프레임과 연결된 속성에 대한 설명을 가져옵니다.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|스택 프레임 속성에 대한 열거형기를 만듭니다.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|스택 프레임과 연결된 스레드를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 디버깅 중인 프로그램이 중단점(사용자 설정 중단점 또는 예외로 인해 발생)에서 중지된 경우에만 가져옵니다. 이 인터페이스에서 식 컨텍스트를 가져와 식을 평가하거나 레지스터 목록을 반환하거나 호출 스택을 가져오고 검사할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
