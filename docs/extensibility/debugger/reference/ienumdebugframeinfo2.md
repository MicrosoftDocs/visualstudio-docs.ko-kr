---
title: 이넘디버그프레임정보2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0aa67792ced94afd9c4439cbc6ea577e6b85f28b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716616"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
이 인터페이스는 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조를 개명합니다.

## <a name="syntax"></a>구문

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DEBug 엔진(DE)은 이 인터페이스를 구현하여 현재 호출 스택을 설명하는 구조 목록을 제공합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 Visual Studio는 [EnumFrameInfo를](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 호출하여 디버깅 중인 프로그램에서 중단점, 예외 또는 중단이 발생할 때마다 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugFrameInfo2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|열거 순서에서 지정된 수의 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조를 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|열거 순서에서 지정된 수의 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조를 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|열거형에서 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조의 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio는 디버깅 중인 프로그램에서 중단점, 예외 또는 사용자가 생성한 일시 중지를 처리하는 첫 번째 단계로 이 인터페이스를 가져옵니다. [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조의 목록은 현재 호출 스택을 나타내며, 현재 함수는 목록의 시작 부분에, 목록 끝에 가장 오래된 함수 호출이 있습니다. 각각은 `FRAMEINFO` 식을 평가할 수 있는 컨텍스트인 스택 프레임과 로컬 변수를 나타냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
