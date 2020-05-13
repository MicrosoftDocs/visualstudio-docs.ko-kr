---
title: 아이버그필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728758"
---
# <a name="idebugfield"></a>IDebugField
이 인터페이스는 필드, 즉 기호 또는 형식에 대한 설명을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 기호 공급자는 이 인터페이스를 모든 필드의 기본 클래스로 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 모든 필드의 기본 클래스입니다. [GetKind의](../../../extensibility/debugger/reference/idebugfield-getkind.md)반환 값에 따라 이 인터페이스는 [QueryInterface](/cpp/atl/queryinterface)를 사용하여 보다 전문적인 인터페이스를 반환할 수 있습니다. 또한 많은 인터페이스는 `IDebugField` 다양한 메서드의 개체를 반환합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugField`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|기호 또는 유형에 대한 표시 가능한 정보를 가져옵니다.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|필드의 종류를 가져옵니다.|
|[Gettype](../../../extensibility/debugger/reference/idebugfield-gettype.md)|필드 유형을 가져옵니다.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|필드의 컨테이너를 가져옵니다.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|필드의 주소를 가져옵니다.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|필드의 크기를 바이트로 가져옵니다.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|필드에 대한 확장 정보를 가져옵니다.|
|[같음](../../../extensibility/debugger/reference/idebugfield-equal.md)|두 필드를 비교합니다.|
|[겟타입정보](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|기호 또는 형식에 대한 형식 독립적 정보를 가져옵니다.|

## <a name="remarks"></a>설명
 형식은 C 언어와 `typedef`동일합니다.

 다음 C++ 언어 예제에서는 `weather` 클래스 유형이며 `sunny` `stormy` 기호입니다.

```cpp
class weather;
weather sunny;
weather stormy;
```

 필드가 기호 또는 형식을 나타내는지 여부는 [GetKind를](../../../extensibility/debugger/reference/idebugfield-getkind.md) 호출하고 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 결과를 검사하여 결정할 수 있습니다. 비트가 `FIELD_KIND_TYPE` 설정된 경우 필드는 형식이고 `FIELD_KIND_SYMBOL` 비트가 설정된 경우 기호입니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
