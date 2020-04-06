---
title: 이넘디버그프로그램2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1717397d9ff073642c7b6bc25ad85babe76d684c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715578"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
이 인터페이스는 현재 디버그 세션에서 실행 중인 프로그램을 개명합니다.

## <a name="syntax"></a>구문

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE(디버그 엔진)는 DE에서 디버깅하는 프로그램 목록을 제공하기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 비주얼 스튜디오는 이 인터페이스를 얻기 위해 [EnumPrograms를](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 호출합니다. [Enum프로그램은](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) 비주얼 스튜디오에서 사용되지 않습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugPrograms2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|열거 순서에서 지정된 수의 프로그램을 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|열거 순서에서 지정된 수의 프로그램을 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|열거형의 프로그램 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio는 이 인터페이스를 사용하여 다음을 수행합니다.

- **모듈** 창을 채웁니다(EnumPrograms를 호출한 다음 각 프로그램에서 [EnumModules를](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) 호출). [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

- **프로세스에 연결 목록을** 채우기(각 `IDebugProcess2::EnumPrograms` [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출하여 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) 인터페이스를 가져오도록 요청).

- 프로세스의 각 프로그램을 디버깅할 수 있는 DS 목록을 [생성합니다(GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)사용).

- 각 프로그램에 ENC(편집 및 계속) 업데이트를 적용합니다(IDebugProcess2::EnumPrograms를 호출한 다음 [GetENCUpdate를](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)호출).

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
