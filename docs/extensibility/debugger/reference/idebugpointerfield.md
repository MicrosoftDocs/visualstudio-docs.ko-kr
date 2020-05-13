---
title: 이데버그포인터필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a69797cc513b96c364f0357f22788fc9bcd65657
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725599"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
이 인터페이스는 포인터 형식을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 기호 공급자는 포인터를 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetKind가](../../../extensibility/debugger/reference/idebugfield-getkind.md) 반환하는 `FIELD_TYPE_POINTER`경우 [쿼리 인터페이스를](/cpp/atl/queryinterface) 사용하여 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스에서 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 `IDebugField` 이 인터페이스는 및 `IDebugContainerField` 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|포인터의 대상을 설명하는 [IDebugField를](../../../extensibility/debugger/reference/idebugfield.md) 반환합니다.|

## <a name="remarks"></a>설명
 C/C++에서 포인터는 배열 표기와 함께 사용되는 경우 컨테이너가 될 수 있습니다. 예를 들어, `char *pString` `pString` Given 은 에 `char`대한 포인터 유형이 있습니다. `pString[3]`해당 컨테이너의 네 번째 요소를 `char` 참조하는 포인터인 컨테이너 의 형식이 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
