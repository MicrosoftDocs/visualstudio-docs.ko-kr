---
description: 이 인터페이스는 컴퓨터 또는 포트 공급자의 포트를 열거 합니다.
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 66598460a48c960b78cb89315fff6bd7ac9a845e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064594"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
이 인터페이스는 컴퓨터 또는 포트 공급자의 포트를 열거 합니다.

## <a name="syntax"></a>구문

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 사용자 지정 포트 공급자는이 인터페이스를 구현 하 여 공급자가 만든 포트 목록을 나타냅니다. Visual Studio는 자체 포트 공급자를 지원 하기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Enumports](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) 를 호출 하 여 포트 공급자가 만든 포트 목록을 나타내는이 인터페이스를 가져옵니다. [Enumpersistedports](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) 를 호출 하 여 디스크에 저장 된 포트 목록을 나타내는이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugPorts2` .

|메서드|Description|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|열거형 시퀀스에서 지정 된 수의 포트를 검색 합니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|열거형 시퀀스에서 지정 된 수의 포트를 건너뜁니다.|
|[재설정](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[원본과](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|열거자의 포트 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio에서는이 인터페이스를 사용 하 여 프로세스에 연결 하는 데 사용 되는 포트 목록을 채울 수 있습니다.

 디버그 엔진은 일반적으로이 인터페이스를 사용 하지 않습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
