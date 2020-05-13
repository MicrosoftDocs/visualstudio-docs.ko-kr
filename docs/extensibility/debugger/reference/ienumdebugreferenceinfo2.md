---
title: 이넘디버그레퍼런스정보2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6132235a7e4789c7d9efe5bae9d7fd531112dab4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715274"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
이 인터페이스는 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조를 개명합니다.

## <a name="syntax"></a>구문

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE버그 엔진(DE)은 메모리의 개체에 대한 참조에 대한 지원의 일부로 이 인터페이스를 구현합니다. 이 인터페이스는 참조가 지원되는 경우에만 구현되어야 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 비주얼 스튜디오는 이 인터페이스를 얻기 위해 [EnumChildren를](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugReferenceInfo2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|열거 순서에서 지정된 수의 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조를 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|열거 순서에서 지정된 수의 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조를 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|열거형에서 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조의 수를 가져옵니다.|

## <a name="remarks"></a>설명
 참조는 기본적으로 형식과 주소이지만 속성은 이름, 형식 및 주소입니다. 참조는 참조된 개체가 메모리에 있는 한 유지됩니다. 자세한 내용은 [IDebugReference2를](../../../extensibility/debugger/reference/idebugreference2.md) 참조하십시오.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
