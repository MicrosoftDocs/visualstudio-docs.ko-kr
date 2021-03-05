---
description: 하나 이상의 모듈의 디버깅을 제어 하는 단일 디버그 엔진 (DE)을 나타냅니다.
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2d91098a1f0a7f2df579a347fccb01239fdfeebe
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153674"
---
# <a name="idebugengine3"></a>IDebugEngine3
하나 이상의 모듈의 디버깅을 제어 하는 단일 디버그 엔진 (DE)을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스는 사용자 지정 DE (기호를 지 원하는 경우)에서 구현 되어 JustMyCode 상태를 사용 하도록 설정 합니다. 이 인터페이스는 기호 및 JustMyCode를 지 원하는 경우 DE에 의해 구현 되어야 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는 기호를 로드 하는 위치에 대 한 사용자 옵션을 전달 하기 위해 SDM (세션 디버그 관리자)에 의해 호출 됩니다. 이는 인스턴스화될 때 엔진의 GUID를 설정 하기 위해 호출 됩니다 (이 GUID는 엔진 등록 시점의 메트릭을 기반으로 함). 또한 SDM은이 인터페이스를 호출 하 여 JustMyCode 상태를 설정 하 고 디버거에서 알려진 모든 예외를 지정 된 상태로 설정 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)에서 상속 된 메서드 외에도 인터페이스는 `IDebugEngine3` 다음 메서드를 노출 합니다.

|메서드|설명|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|DE가 디버깅 기호를 검색 하는 데 사용할 경로를 설정 합니다.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|아직 기호가 로드 되지 않은 모든 모듈에 대 한 기호를 로드 합니다.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|JustMyCode 정보에 대해 DE를 알려 줍니다.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|메트릭에 대해 DE GUID를 설정 합니다.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|현재 처리 중인 모든 예외를 지정 된 상태로 설정 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
