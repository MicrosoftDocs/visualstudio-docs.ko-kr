---
title: 이데버그주소2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 402d8c8bcb50c570ff680b8fe1cf8d26f037ba17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736562"
---
# <a name="idebugaddress2"></a>IDebugAddress2
이 인터페이스는 이 인터페이스로 주소가 표시되는 개체를 소유하는 프로세스의 ID에 대한 액세스를 제공합니다.

## <a name="syntax"></a>구문

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 기호 공급자는 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스를 구현하는 동일한 개체에 이 인터페이스를 구현합니다. 이 인터페이스는 이 주소와 관련된 개체를 소유하는 프로세스의 ID에 대한 액세스를 제공합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [쿼리인터페이스를](/cpp/atl/queryinterface) 사용하여 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스에서 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>vtable 순서의 메서드
 이 인터페이스는 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스에서 상속된 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|이 인터페이스로 표시되는 개체를 소유하는 프로세스의 ID를 검색합니다.|

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
