---
title: 이데부알리아스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2ceb87277460f65e52c35f02e7fbbd01da1101a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736521"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 변수에 대한 숫자 별칭을 나타냅니다. 별칭은 단순히 변수에 대 한 다른 이름입니다.

## <a name="syntax"></a>구문

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 계산기(EE)는 변수에 대한 숫자 별칭을 지원하기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
- [CreateAlias는](../../../extensibility/debugger/reference/idebugobject2-createalias.md) 특정 개체에 대한 별칭을 만듭니다. 별칭을 검색하려면 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) 또는 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)를 사용합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 메서드는 인터페이스에 `IDebugAlias` 정의되어 있습니다.

|방법|설명|
|------------|-----------------|
|[Getobject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|이 별칭이 참조하는 개체를 가져옵니다.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|별칭 이름을 가져옵니다.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|이 개체에 `ICorDebugValue` 대한 관리 코드 정보에 대한 액세스를 제공하는 인터페이스를 검색합니다(관리코드만 해당).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|이 별칭을 더 이상 사용되지 않는 것으로 표시합니다.|

## <a name="remarks"></a>설명
 별칭은 문자열 형식의 소수 자릿수이며 # 문자(예: 1001#)가 뒤따릅니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
