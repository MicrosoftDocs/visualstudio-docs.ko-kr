---
title: 아이디버그 이전 기호검색이벤트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d6f3f78e165ba2f4453131b7b459e3061243ff6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736117"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
디버그 엔진(DE)은 이 인터페이스를 세션 디버그 관리자(SDM)로 전송하여 심볼 로드 중에 상태 표시줄 메시지를 설정합니다.

## <a name="syntax"></a>구문

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 기호 로드 중에 상태 표시줄 메시지를 설정해야 하는 경우 이 인터페이스를 구현합니다. 이 인터페이스는 스크립트 인터프리터와 함께 작동하거나 스크립트 인터프리터의 일부인 디버그 엔진에 의해서만 구현됩니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다(SDM은 **QueryInterface를** 사용하여 **IDebugEvent2** 인터페이스에 액세스합니다).

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 기호 로드 중에 상태 표시줄 메시지를 설정해야 할 때 이 이벤트 개체를 만들고 보냅니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="methods"></a>메서드
 다음 표에서는 의 `IDebugBeforeSymbolSearchEvent2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|현재 디버깅 중인 모듈의 이름을 검색합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
