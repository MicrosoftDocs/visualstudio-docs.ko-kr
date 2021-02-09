---
title: IDebugManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b90540aaf5f7e409c8fc7fa44126f195230317f8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929812"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 이 인터페이스를 사용 하면 식 계산기 (EE)에서 값 클래스 인스턴스 (예:)에 대 한 속성 또는 메서드를 호출 하 `System.Decimal` 고 디버깅 중인 프로그램에서 [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 를 호출 하지 않고 해당 값을 설정할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기는 변수와 같은 관리 되는 코드 개체를 나타내기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스를 가져오려면 값 클래스의 인스턴스를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 에서 [getmanageddebugobject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) 를 호출 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md)에서 상속 된 메서드 외에도 인터페이스는 `IDebugManagedObject` 다음 메서드를 노출 합니다.

|메서드|Description|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|관리 코드 개체를 나타내고 적절 한 관리 코드 인터페이스를 가져올 수 있는 인터페이스를 반환 합니다.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|이 개체의 값을 지정 된 관리 되는 코드 개체의 값으로 설정 합니다.|

## <a name="remarks"></a>설명
 식 계산기는이 인터페이스를 사용 하 여 관리 코드 개체를 구문 분석 트리에 저장 합니다.

## <a name="requirements"></a>요구 사항
 헤더: ee. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [평가](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
