---
description: 이 인터페이스는 모듈 목록을 열거 합니다.
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96a35f11346b769a4329b1212a8202e5e5ded006
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058172"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
이 인터페이스는 모듈 목록을 열거 합니다.

## <a name="syntax"></a>구문

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는이 인터페이스를 구현 하 여 프로그램에 대해 로드 된 모듈 목록을 나타냅니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 Visual Studio는이 인터페이스를 얻기 위해 [Enummodules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) 을 호출 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugModules2` .

|메서드|Description|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|열거형 시퀀스에서 지정 된 수의 모듈을 검색 합니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|열거형 시퀀스에서 지정 된 수의 모듈을 건너뜁니다.|
|[재설정](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[원본과](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|모듈 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio는 주로 **모듈** 창을 업데이트 하는 데이 인터페이스를 사용 합니다.

 Visual Studio에서 디버깅 하기 위해 프로그램은 모듈 경계를 넘을 수 있는 코드 명령의 논리적 시퀀스 이므로 단일 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스에 대 한 모듈 목록이 필요 합니다. 목록의 첫 번째 모듈은 일반적으로 연결 된 프로그램의 초기 진입점을 포함 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
