---
description: 이 인터페이스는 특정 스레드의 호출 스택에 있는 단일 스택 프레임을 나타냅니다.
title: IDebugStackFrame2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5ec53e89afb43187c641058620df53c4a61d6cc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145913"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
이 인터페이스는 특정 스레드의 호출 스택에 있는 단일 스택 프레임을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE)은이 인터페이스를 구현 하 여 스택 프레임을 나타냅니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Enum프레임 정보](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 를 호출 하 여 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 인터페이스를 검색 합니다. 인터페이스를 포함 하는 [프레임 정보](../../../extensibility/debugger/reference/frameinfo.md) 구조를 검색 하려면 [다음](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) 을 호출 `IDebugStackFrame2` 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugStackFrame2` .

|메서드|설명|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|이 스택 프레임에 대 한 코드 컨텍스트를 가져옵니다.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|이 스택 프레임의 문서 컨텍스트를 가져옵니다.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|스택 프레임의 이름을 가져옵니다.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|스택 프레임에 대 한 설명을 가져옵니다.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|스택 프레임과 연결 된 실제 주소 범위의 컴퓨터 종속 표현을 가져옵니다.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|스택 프레임 및 스레드의 현재 컨텍스트 내에서 식 계산을 수행 하기 위한 평가 컨텍스트를 가져옵니다.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|스택 프레임과 연결 된 언어를 가져옵니다.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|스택 프레임과 연결 된 속성에 대 한 설명을 가져옵니다.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|스택 프레임 속성의 열거자를 만듭니다.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|스택 프레임과 연결 된 스레드를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 디버그 중인 프로그램이 중단점에서 중지 된 경우에만 가져옵니다 (사용자 설정 중단점 또는 예외로 인해 발생). 이 인터페이스에서 식을 계산 하기 위해 식 컨텍스트를 얻거나 레지스터 목록을 반환 하거나 호출 스택을 얻고 검사할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
