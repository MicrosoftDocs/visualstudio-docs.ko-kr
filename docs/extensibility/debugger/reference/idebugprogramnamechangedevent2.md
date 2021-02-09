---
title: IDebugProgramNameChangedEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0640fa06b821c6679bc52c9f92a757cee6f0a580
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898744"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
프로그램 이름이 변경 될 때 디버그 엔진 (DE)에서 세션 디버그 관리자 (SDM)로 전송 됩니다.

## <a name="syntax"></a>구문

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE는 프로그램 이름이 변경 되었음을 보고 하기 위해이 인터페이스를 구현 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 **IDebugEvent2** 인터페이스에 액세스 하는 데 [QueryInterface](/cpp/atl/queryinterface) 를 사용 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 DE는 프로그램 이름 변경을 보고 하기 위해이 이벤트 개체를 만들어 보냅니다. DE는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여이 이벤트를 보냅니다. 사용자 지정 포트 공급자는 I 인터페이스를 사용 하 여이 이벤트를 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
