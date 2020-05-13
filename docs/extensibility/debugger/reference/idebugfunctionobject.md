---
title: 아이디버그기능 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728495"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스는 함수를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 계산기는 함수를 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스의 전문화이며 `IDebugObject` 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 사용하여 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugObject에서](../../../extensibility/debugger/reference/idebugobject.md)상속된 메서드 외에도 인터페이스는 `IDebugFunctionObject` 다음 메서드를 노출합니다.

|방법|설명|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|기본 데이터 개체를 만듭니다.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|생성자 사용 하 여 개체를 만듭니다.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|생성자가 없는 개체를 만듭니다.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|배열 개체를 만듭니다.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|문자열 개체를 만듭니다.|
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|함수를 호출하고 결과 값을 개체로 반환합니다.|

## <a name="remarks"></a>설명
 이 인터페이스를 사용하면 식 계산기에서 구문 분석 트리의 함수를 나타낼 수 있습니다. 이 `Create` 인터페이스의 메서드는 메서드에 입력 매개 변수를 나타내는 개체를 생성하는 데 사용됩니다. 그런 다음 함수의 반환 값을 나타내는 개체를 반환 하는 [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 메서드를 호출 하 여 함수를 실행할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
