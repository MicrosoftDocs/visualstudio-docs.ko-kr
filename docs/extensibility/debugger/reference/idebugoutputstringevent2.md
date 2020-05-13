---
title: 아이데버그출력스트링이벤트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c47a920e99ece3fb0853e4e6a26dba3c8d0c45c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726026"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
이 인터페이스는 디버그 엔진(DE)에 의해 세션 디버그 관리자(SDM)로 전송되어 문자열을 출력합니다.

## <a name="syntax"></a>구문

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 이 인터페이스를 구현하여 IDE의 **출력** 창에 문자열을 보냅니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다. SDM은 [쿼리인터페이스를](/cpp/atl/queryinterface) 사용하여 `IDebugEvent2` 인터페이스에 액세스합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 **이** 이벤트 개체를 만들고 출력 창에 문자열을 보냅니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugOutputStringEvent2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|표시 가능한 메시지를 가져옵니다.|

## <a name="remarks"></a>설명
 예를 들어 관리되지 않는 코드에서 출력할 문자열은 디버깅 중인 프로그램이 Win32 `OutputDebugString` 함수에 문자열을 보낼 때 시작될 수 있습니다. 이 문자열은 DE에 의해 가로채고 `IDebugOutputStringEvent2` 이벤트로 SDM에 전송됩니다.

 [IDebugMessageEvent2를](../../../extensibility/debugger/reference/idebugmessageevent2.md) 사용하여 사용자 응답이 필요한 메시지를 보냅니다.

 [IDebugErrorEvent2를](../../../extensibility/debugger/reference/idebugerrorevent2.md) 사용하여 응답이 필요하지 않은 오류 메시지를 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
