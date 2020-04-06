---
title: 이데버그메소드필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061035933e57ea4ca8e7857f68ac3d6311bae32c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727066"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
이 인터페이스는 메서드를 설명합니다.

## <a name="syntax"></a>구문

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 기호 공급자는 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스를 구현하는 동일한 개체에 이 인터페이스를 구현합니다. 이 인터페이스는 메서드를 제공하는 전문화 입니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetKind가](../../../extensibility/debugger/reference/idebugfield-getkind.md) 반환하는 `FIELD_TYPE_METHOD`경우 [쿼리 인터페이스를](/cpp/atl/queryinterface) 사용하여 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스에서 이 인터페이스를 가져옵니다. 또한 메서드, [GetPropertyGetter,](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)및 [Enum생성자](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)모두 인터페이스를 반환합니다. `IDebugMethodField`

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 및 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|메서드의 매개 변수에 대한 열거수를 만듭니다.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|메서드를 포함하는 개체의 "this" 포인터를 가져옵니다.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|메서드의 모든 로컬 변수에 대한 열거수를 만듭니다.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|메서드의 선택한 로컬 변수에 대한 열거수를 만듭니다.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|특정 사용자 지정 특성이 정의되었는지 여부를 결정합니다.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|메서드의 정적 로컬 변수에 대한 열거수를 만듭니다.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|메서드의 전역 컨테이너를 가져옵니다.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|메서드를 호출하는 데 필요한 각 인수의 형식에 대한 열거수를 만듭니다.|

## <a name="remarks"></a>설명
 메서드에는 매개 변수와 로컬 변수가 포함될 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
