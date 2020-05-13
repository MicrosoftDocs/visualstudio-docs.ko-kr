---
title: 아이디버그프로그램이름변경이벤트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae58728601c3adbe6e37a00fd0694a5d71eef0b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722152"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
프로그램 이름이 변경될 때 DE(디버그 엔진)에서 세션 디버그 관리자(SDM)로 전송됩니다.

## <a name="syntax"></a>구문

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 프로그램 이름이 변경되었음을 보고하기 위해 이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다. SDM은 [쿼리 인터페이스를](/cpp/atl/queryinterface) 사용하여 **IDebugEvent2** 인터페이스에 액세스합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 프로그램 이름 변경을 보고하기 위해 이 이벤트 개체를 만들고 보냅니다. DE는 디버깅 중인 프로그램에 연결할 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 이 이벤트를 보냅니다. 사용자 지정 포트 공급자는 I 인터페이스를 사용하여 이 이벤트를 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
