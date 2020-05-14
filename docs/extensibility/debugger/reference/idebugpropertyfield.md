---
title: 아이디버그프로퍼티필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96a3f3c2dca16cd2c28c9d1727e4ac145c91c482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720688"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
이 인터페이스는 속성을 받고 설정할 수 있는 함수를 제공합니다.

## <a name="syntax"></a>구문

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 기호 공급자는 [IDebugContainerField를](../../../extensibility/debugger/reference/idebugcontainerfield.md)구현하는 동일한 개체에 이 인터페이스를 구현합니다. 이 인터페이스는 클래스의 속성 개념을 지원하는 특수화입니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 쿼리 [인터페이스를](/cpp/atl/queryinterface) 사용 하 여 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스에서이 `FIELD_KIND_PROP`인터페이스를 가져옵니다 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드가 반환 하는 경우 .

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 및 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|속성을 가져옵니다.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|속성을 설정하는 메서드를 가져옵니다.|

## <a name="remarks"></a>설명
 속성은 관리 되는 코드 개념이며 변수로 처리 되는 메서드를 나타냅니다. 속성이 관리되지 않는 C++에 없습니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
