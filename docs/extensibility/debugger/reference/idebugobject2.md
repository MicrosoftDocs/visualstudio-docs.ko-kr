---
title: 아이디버그오브젝트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e468b5a282ffb5466d57a3c9b1a37aa3ae8643ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726080"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스는 개체에 대한 추가 정보를 제공합니다.

## <a name="syntax"></a>구문

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 계산기는 별칭에 대한 지원과 개체에 대한 정보에 대한 액세스를 제공하기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스는 [QueryInterface](/cpp/atl/queryinterface). 또한 [GetObject는](../../../extensibility/debugger/reference/idebugalias-getobject.md) 이 인터페이스를 반환합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 `IDebugObject2` [인터페이스는 IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스의 메서드 외에도 다음을 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|이 개체로 표시되는 속성을 백업할 수 있는 필드 또는 변수(있는 경우)를 가져옵니다.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|이 개체의 값을 나타내는 관리 되는 코드 개체를 가져옵니다.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|이 개체에 대한 고유 ID를 만들거나 기존 별칭을 반환합니다.|
|[게탈리아스](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|이 개체와 연결된 별칭(있는 경우)을 가져옵니다.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|이 개체의 형식을 가져옵니다.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|이 개체가 사용자 데이터를 나타내는지 여부를 결정합니다.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|편집 및 계속 상태가 더 이상 유효하지 않은지 여부를 결정합니다.<br /><br /> 사용자 지정 식 계산기는 이 메서드를 `E_NOTIMPL`구현하지 않습니다(항상 반환해야 합니다).|

## <a name="remarks"></a>설명
 별칭에 대한 설명은 [IDebugAlias를](../../../extensibility/debugger/reference/idebugalias.md) 참조하십시오.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [Getobject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
