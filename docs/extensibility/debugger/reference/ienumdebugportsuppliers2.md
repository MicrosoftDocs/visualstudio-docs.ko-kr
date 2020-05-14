---
title: 이넘디버그포트공급업체2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de0bfc5b387df9b347e4a58d97601a5e1e70f1a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715941"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
이 인터페이스는 포트 공급자를 개명합니다.

## <a name="syntax"></a>구문

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 Visual Studio는 포트 공급자 목록을 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [EnumPortSupplier에](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) 전화하여 포트 공급업체 목록을 구하십시오.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugPortSuppliers2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|열거 순서에서 지정된 수의 포트 공급자를 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|열거 순서에서 지정된 수의 포트 공급자를 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|열거형에서 포트 공급업체 수를 가져옵니다.|

## <a name="remarks"></a>설명
 디버그 엔진은 일반적으로 이 인터페이스를 가져올 필요가 없습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
