---
title: IEnumDebugPropertyInfo2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715349"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
이 인터페이스는 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조체를 열거 합니다.

## <a name="syntax"></a>Syntax

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는이 인터페이스를 구현 하 여 특정 속성에 대 한 정보를 나타냅니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 을 호출 하 여 특정 속성의 자식을 나타내는이 인터페이스를 가져옵니다. [Enumproperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) 를 호출 하 여 특정 스택 프레임의 속성을 나타내는이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugPropertyInfo2` .

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|열거형 시퀀스에서 지정 된 수의 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조체를 검색 합니다.|
|[skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|열거형 시퀀스에서 지정 된 수의 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조체를 건너뜁니다.|
|[재설정](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|열거자의 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조체 수를 가져옵니다.|

## <a name="remarks"></a>설명
 일반적으로 속성은 이름, 값, 주소 및 형식을 포함할 수 있는 정보 계층 구조와 연결 된 속성 개체 또는 스택 프레임에 적절 한 기타 정보를 제공 합니다. 자세한 내용은 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 를 참조 하세요.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
