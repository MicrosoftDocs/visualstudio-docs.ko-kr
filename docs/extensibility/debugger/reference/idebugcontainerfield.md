---
title: 아이디버그컨테이너필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72296517a64c6dcfcb8e347fb00588504aa75a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733213"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
이 인터페이스는 다른 기호 또는 형식에 대한 컨테이너인 기호 또는 형식을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 기호 공급자는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스를 구현하는 동일한 개체에 이 인터페이스를 구현합니다. 이 인터페이스는 컨테이너를 나타내는 모든 인터페이스의 기본 클래스이기도 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 많은 인터페이스의 많은 메서드가 이 인터페이스를 반환합니다. 이 클래스는 모든 컨테이너에 대한 기본 클래스이므로 [QueryInterface](/cpp/atl/queryinterface)를 사용하여 이 인터페이스에서 보다 특수화된 인터페이스를 가져올 수 있습니다. 이러한 인터페이스에는 [IDebugArrayField,](../../../extensibility/debugger/reference/idebugarrayfield.md) [IDebugClassField,](../../../extensibility/debugger/reference/idebugclassfield.md) [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)및 [IDebugPropertyField가](../../../extensibility/debugger/reference/idebugpropertyfield.md)포함됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|컨테이너 필드에 대한 열거수를 만듭니다.|

## <a name="remarks"></a>설명
 배열(변수에 대한 컨테이너), 클래스(메서드 및 변수에 대한 컨테이너) 및 메서드(매개 변수 및 로컬 변수에 대한 컨테이너)는 모두 컨테이너의 예입니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
