---
title: IDebugExpressionContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 344ae287b3784ceca87fbbab09ad2b2e0a304205
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729632"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
이 인터페이스는 식 계산에 대 한 컨텍스트를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는이 인터페이스를 구현 하 여 식을 계산할 수 있는 컨텍스트를 나타냅니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Getexpressioncontext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 를 호출 하면이 인터페이스가 반환 됩니다. 이 인터페이스는 디버그 중인 프로그램이 일시 중지 되어 스택 프레임을 사용할 수 있는 경우에만 액세스할 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugExpressionContext2` .

|메서드|설명|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|평가 컨텍스트의 이름을 검색 합니다.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|계산을 위해 텍스트 기반 식을 구문 분석 합니다.|

## <a name="remarks"></a>설명
 평가 컨텍스트는 식 계산을 수행 하기 위한 범위로 간주할 수 있습니다.

 프로그램이 중지 되 면 세션 디버그 관리자 (SDM)는 [Enum프레임 정보](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)에 대 한 호출을 사용 하 여 DE에서 스택 프레임을 가져옵니다. 그런 다음, SDM은 [Getexpressioncontext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 를 호출 하 여 인터페이스를 가져옵니다 `IDebugExpressionContext2` . 그런 다음 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 를 호출 하 여 평가할 준비 된 식을 나타내는 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스를 만듭니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
