---
title: 이넘디버그커스터텀속성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f8b521432124267d3f0e179d3a889fb599fa99d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717135"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
사용자 지정 특성을 개명합니다.

## <a name="syntax"></a>구문

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 기호 공급자는 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) 인터페이스를 통해 사용자 지정 특성을 지원 하기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
- [열거형 사용자 지정 특성이 이 인터페이스를 반환합니다.](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugCustomAttributes`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|열거 순서에서 지정된 수의 사용자 지정 특성을 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|열거 순서에서 지정된 수의 사용자 지정 특성을 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|열거형에서 사용자 지정 특성 수를 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
