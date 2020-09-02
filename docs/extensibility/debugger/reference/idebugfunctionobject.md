---
title: IDebugFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6433c1f2c540b040a3b3beccc264377e69592387
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728495"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 이 인터페이스는 함수를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기는 함수를 나타내기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스의 특수화 이며 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 가져옵니다 `IDebugObject` .

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md)에서 상속 된 메서드 외에도 인터페이스는 `IDebugFunctionObject` 다음 메서드를 노출 합니다.

|메서드|설명|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|기본 데이터 개체를 만듭니다.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|생성자를 사용 하 여 개체를 만듭니다.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|생성자 없이 개체를 만듭니다.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|배열 개체를 만듭니다.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|문자열 개체를 만듭니다.|
|[평가](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|함수를 호출 하 고 결과 값을 개체로 반환 합니다.|

## <a name="remarks"></a>설명
 이 인터페이스를 사용 하면 식 계산기가 구문 분석 트리에서 함수를 나타낼 수 있습니다. `Create`이 인터페이스의 메서드는 메서드에 대 한 입력 매개 변수를 나타내는 개체를 생성 하는 데 사용 됩니다. 그러면 함수의 반환 값을 나타내는 개체를 반환 하는 [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 메서드를 호출 하 여 함수를 실행할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: ee. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
