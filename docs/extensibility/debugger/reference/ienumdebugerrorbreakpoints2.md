---
description: 이 인터페이스는 보류 중인 중단점과 연결 된 오류 중단점을 열거 합니다.
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 71667ef0de4d72d2d6db2619c41c68b7949803e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086588"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
이 인터페이스는 보류 중인 중단점과 연결 된 오류 중단점을 열거 합니다.

## <a name="syntax"></a>구문

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는 중단점에 대 한 지원의 일부로이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 Visual Studio에서는 [Canbind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) 를 호출 하 여 바인딩할 수 없는 중단점 목록을 나타내는이 인터페이스를 가져오거나, 바인딩되지 않은 중단점 목록을 나타내는이 인터페이스를 가져오는 [enumerrorbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) 발생 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugErrorBreakpoints2` .

|메서드|Description|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|열거형 시퀀스에서 지정 된 수의 오류 중단점을 검색 합니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|열거형 시퀀스에서 지정 된 수의 오류 중단점을 건너뜁니다.|
|[재설정](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[원본과](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|열거자의 오류 중단점 수를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스에는 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 인터페이스 목록이 포함 되어 있으며, 각 인터페이스는 바인딩할 수 없는 중단점을 설명 하 고 바인딩할 수 없는 이유를 설명 합니다. Visual Studio는 인터페이스를 사용 하 여 `IEnumDebugErrorBreakpoint2` IDE에 표시 된 중단점을 업데이트 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
