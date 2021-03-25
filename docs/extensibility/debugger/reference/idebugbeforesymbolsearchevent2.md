---
description: 디버그 엔진 (DE)은 기호를 로드 하는 동안 상태 표시줄 메시지를 설정 하기 위해이 인터페이스를 세션 디버그 관리자 (SDM)로 보냅니다.
title: IDebugBeforeSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e3e7c0428a96b8841a598e7b91986aa1555ea5c2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067480"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
디버그 엔진 (DE)은 기호를 로드 하는 동안 상태 표시줄 메시지를 설정 하기 위해이 인터페이스를 세션 디버그 관리자 (SDM)로 보냅니다.

## <a name="syntax"></a>구문

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE는 기호를 로드 하는 동안 상태 표시줄 메시지를 설정 해야 하는 경우이 인터페이스를 구현 합니다. 이 인터페이스는에서 작동 하거나 스크립트 인터프리터의 일부인 디버그 엔진 에서만 구현 됩니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 해야 합니다. SDM은 **IDebugEvent2** 인터페이스에 액세스 하는 데 **QueryInterface** 를 사용 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 DE는 기호를 로드 하는 동안 상태 표시줄 메시지를 설정 해야 하는 경우이 이벤트 개체를 만들고 보냅니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback 함수를 사용 하 여 보냅니다.

## <a name="methods"></a>메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugBeforeSymbolSearchEvent2` .

|메서드|Description|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|현재 디버깅 중인 모듈의 이름을 검색 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
