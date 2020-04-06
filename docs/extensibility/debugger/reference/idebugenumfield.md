---
title: 이데버그에넘필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7885f36a113809e81279498a769e257af4f1cde2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730176"
---
# <a name="idebugenumfield"></a>IDebugEnumField
이 인터페이스는 열거형을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 기호 공급자는 열거형을 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetKind가](../../../extensibility/debugger/reference/idebugfield-getkind.md) 반환하는 `FIELD_TYPE_ENUM`경우 [쿼리 인터페이스를](/cpp/atl/queryinterface) 사용하여 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스에서 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>VTable 순서의 메서드
 `IDebugField` 이 인터페이스는 및 `IDebugContainerField` 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|이 열거형 형식의 이름을 설명하는 [IDebugField를](../../../extensibility/debugger/reference/idebugfield.md) 반환합니다.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|지정된 값과 연결된 열거형 상수의 이름을 반환합니다.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|지정된 열거형 상수 이름과 연결된 값을 반환합니다.|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|지정된 열거 상수 이름과 연관된 값을 반환하지만 대/소문자를 무시합니다.|

## <a name="remarks"></a>설명
 실제로 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [바인딩](../../../extensibility/debugger/reference/idebugbinder-bind.md)
