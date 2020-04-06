---
title: 아이데버그디디에이치오브젝트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fbd270aa1b65f05f308d41d22f154fb53b8833d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727682"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 이 인터페이스를 사용하면 식 평가기(EE)가 값 클래스 인스턴스에서 `System.Decimal`속성 또는 메서드를 호출하고 디버깅 중인 프로그램에서 [Evaluate를](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 호출하지 않고 값을 설정할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 평가기는 변수와 같은 관리되는 코드 개체를 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스를 가져오려면 값 클래스의 인스턴스를 나타내는 [IDebugObject에서](../../../extensibility/debugger/reference/idebugobject.md) [GetManagedDebugObject를](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugObject에서](../../../extensibility/debugger/reference/idebugobject.md)상속된 메서드 외에도 인터페이스는 `IDebugManagedObject` 다음 메서드를 노출합니다.

|방법|설명|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|관리되는 코드 개체를 나타내는 인터페이스를 반환하고 적절한 관리 코드 인터페이스를 가져올 수 있습니다.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|이 개체의 값을 지정된 관리 코드 개체의 값으로 설정합니다.|

## <a name="remarks"></a>설명
 식 계산기는 이 인터페이스를 사용하여 관리되는 코드 개체를 구문 분석 트리에 저장합니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
