---
title: 이넘디버그프로퍼프로퍼정보2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfa0f8feff6a53b84a6337e5bea8bdc622e19a20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715349"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
이 인터페이스는 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조를 개명합니다.

## <a name="syntax"></a>구문

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DEBug 엔진(DE)은 특정 속성에 대한 정보를 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 특정 속성의 자식을 나타내는 이 인터페이스를 얻으려면 [EnumChildren를](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 호출합니다. 특정 스택 프레임의 속성을 나타내는 이 인터페이스를 얻으려면 [EnumProperties를](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugPropertyInfo2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|열거 순서에서 지정된 수의 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조를 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|열거 순서에서 지정된 수의 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조를 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|열거형에서 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조의 수를 가져옵니다.|

## <a name="remarks"></a>설명
 일반적으로 속성은 이름, 값, 주소 및 형식뿐만 아니라 연결된 속성 개체 또는 스택 프레임에 적합한 기타 정보를 포함할 수 있는 정보의 계층 구조입니다. 자세한 내용은 [IDebugProperty2를](../../../extensibility/debugger/reference/idebugproperty2.md) 참조하십시오.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
