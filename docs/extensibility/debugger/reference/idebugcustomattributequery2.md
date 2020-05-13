---
title: IDebug사용자 정의 속성 쿼리2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fe3969002c64ab361de76012c432e2bb5c61b5c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732481"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
이 필드에 대한 사용자 지정 특성의 존재를 확인하고 이 필드에 있는 경우 특성 정보를 반환합니다.

## <a name="syntax"></a>구문

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 기호 공급자는 사용자 지정 특성을 지원 하기 위해 [IDebugField를](../../../extensibility/debugger/reference/idebugfield.md) 구현 하는 동일한 개체에이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [쿼리인터페이스를](/cpp/atl/queryinterface) 사용하여 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스에서 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 **IDebugCustomAttributeQuery** 인터페이스의 메서드를 보여 줍니다.

|방법|설명|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|사용자 지정 특성이 이름으로 존재하는지 여부를 결정합니다.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|지정된 사용자 지정 특성에 대한 특성 정보를 가져옵니다.|

 **IDebugCustomAttributeQuery** 메서드 외에도 다음 `IDebugCustomAttributeQuery2` 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|이 필드에 연결된 모든 사용자 지정 특성에 대한 열거형기를 가져옵니다.|

## <a name="remarks"></a>설명
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) 메서드는 이 필드에 대해 정의된 모든 사용자 지정 특성에 대해 열거기를 반환할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
