---
title: 이넘디버그모듈2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 612285aa4d5a249c0f922ccae88d98a7df83187b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716439"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
이 인터페이스는 모듈 목록을 나열합니다.

## <a name="syntax"></a>구문

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 프로그램에 로드된 모듈 목록을 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 비주얼 스튜디오는 이 인터페이스를 얻기 위해 [EnumModules를 호출합니다.](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugModules2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|열거 순서에서 지정된 수의 모듈을 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|열거 순서에서 지정된 수의 모듈을 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|모듈 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio는 주로 이 인터페이스를 사용하여 모듈 창을 **업데이트합니다.**

 Visual Studio에서 디버깅을 위해 프로그램은 모듈 경계를 넘을 수 있는 코드 명령의 논리적 시퀀스이므로 단일 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스에 대한 모듈 목록이 필요합니다. 목록의 첫 번째 모듈에는 일반적으로 연결된 프로그램의 초기 진입점이 포함됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
