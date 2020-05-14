---
title: 아이데버그주소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f281ceb1f305c5774fedbf725f2e6a9481d073d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736597"
---
# <a name="idebugaddress"></a>IDebugAddress
이 인터페이스는 항목의 주소를 나타냅니다. 기호 처리기에 의해 반환됩니다.

## <a name="syntax"></a>구문

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 기호 공급자는 개체의 주소를 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 많은 인터페이스의 많은 메서드가 이 인터페이스를 반환합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 방법을 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|개체와 해당 위치를 설명하는 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조를 검색합니다.|

## <a name="remarks"></a>설명
 기호 공급자는 이 인터페이스를 반환하여 특정 범위(예: 함수, 메서드 또는 클래스) 내에서 개체및 해당 위치를 나타냅니다. 이 인터페이스는 심볼 공급자 및 식 평가기의 다양한 메서드에서 반환되고 전달됩니다. 일반적으로 기호 공급자는 이 인터페이스의 내용을 해석해야 하는 유일한 엔터티입니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
