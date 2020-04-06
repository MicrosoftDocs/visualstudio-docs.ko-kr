---
title: 이넘디버그오류지점2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea841a095964b71e301e966bfd0a10c8f7c0c65d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716890"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
이 인터페이스는 보류 중인 중단점과 관련된 오류 중단점을 개명합니다.

## <a name="syntax"></a>구문

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 중단점에 대한 지원의 일부로 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 Visual Studio는 바인딩할 수 없는 중단점 목록을 나타내는 이 인터페이스를 가져오려면 [CanBind를](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) [호출하거나, EnumErrorBreakpoints는](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) 바인딩되지 않은 중단점 목록을 나타내는 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugErrorBreakpoints2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|열거 시퀀스에서 지정된 수의 오류 중단점을 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|열거 순서에서 지정된 수의 오류 중단점을 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|열거형의 오류 중단점 수를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스에는 바인딩할 수 없는 중단점과 바인딩할 수 없는 이유를 설명하는 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 인터페이스 목록이 있습니다. Visual Studio는 `IEnumDebugErrorBreakpoint2` 인터페이스를 사용하여 IDE에 표시된 중단점을 업데이트합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
