---
title: 아이디버그엔트리포인트이벤트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 531ff846f2488193ed7f3d9f200a1a4ea04df6f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730322"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
디버그 엔진(DE)은 프로그램이 사용자 코드의 첫 번째 명령을 실행하려고 할 때 이 인터페이스를 세션 디버그 관리자(SDM)로 보냅니다.

## <a name="syntax"></a>구문

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 이 인터페이스를 정상 작업의 일부로 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다. SDM은 [쿼리인터페이스를](/cpp/atl/queryinterface) 사용하여 `IDebugEvent2` 인터페이스에 액세스합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 디버깅 중인 프로그램이 로드되고 사용자 코드의 첫 번째 명령을 실행할 준비가 되면 이 이벤트 개체를 만들고 보냅니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="remarks"></a>설명
- [IDebugLoadCompleteEvent2는](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 프로그램이 첫 번째 명령을 실행하려고 할 때 전송됩니다. 예를 들어 `IDebugEntryPoint2` 프로그램이 사용자의 `main` 기능을 실행하려고 할 때 전송됩니다.

 DE가 보낼 `IDebugEntryPointEvent2`때 현재 코드 위치는 다음과 같은 `main`사용자 코드의 첫 번째 명령에 있어야 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
