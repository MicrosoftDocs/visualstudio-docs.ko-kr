---
title: IDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6801176964a47646f03091131e1be89cf63c97f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726306"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 이 인터페이스는 바인더에서 기호와 식의 값을 캡슐화 하기 위해 만드는 개체를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기는이 인터페이스를 구현 하 여 개체를 나타냅니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는 식 계산기가 구문 분석 된 식에 사용 하는 모든 개체에 대 한 기본 클래스입니다. [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) 메서드를 호출 하 여 반환 됩니다. [QueryInterface](/cpp/atl/queryinterface) 는이 인터페이스에서 더 특수화 된 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugObject` .

|메서드|설명|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|개체의 크기를 가져옵니다.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|개체의 값을 연속 된 일련의 바이트로 가져옵니다.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|연속 된 일련의 바이트에서 개체의 값을 설정 합니다.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|이 개체의 참조 값을 설정 합니다.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|개체의 값 주소를 나타내는 메모리 컨텍스트를 가져옵니다.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|디버그 엔진의 주소 공간에서 관리 되는 개체의 복사본을 만듭니다.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|이 개체가 null 참조 인지 여부를 테스트 합니다.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|개체를이 개체와 비교 합니다.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|이 개체가 읽기 전용인 지 여부를 확인 합니다.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|개체가 투명 프록시 인지 여부를 확인 합니다.|

## <a name="remarks"></a>설명
 식 계산기는이 인터페이스를 기본 클래스로 사용 하 여 구문 분석 트리의 개체를 나타냅니다.

## <a name="requirements"></a>요구 사항
 헤더: ee. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [바인딩하며](../../../extensibility/debugger/reference/idebugbinder-bind.md)
