---
title: 아이데버그엔진3 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7026156eac7f60e7435e32244c3cc03ae5f08e1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730647"
---
# <a name="idebugengine3"></a>IDebugEngine3
하나 이상의 모듈의 디버깅을 제어하는 단일 디버그 엔진(DE)을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 JustMyCode 상태를 활성화하기 위해 사용자 지정 DE(기호를 지원하는 경우)에 의해 구현됩니다. 이 인터페이스는 기호 및 JustMyCode를 지원하는 경우 DE에서 구현해야 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 SDM(세션 디버그 관리자)에서 호출하여 기호를 로드할 위치에 대한 사용자 옵션을 전달합니다. 인스턴스화될 때 엔진의 GUID를 설정하기 위해 호출됩니다(이 GUID는 엔진 등록 시점의 메트릭을 기반으로 함). 또한 SDM은 이 인터페이스를 호출하여 JustMyCode 상태를 설정하고 디버거에 의해 알려진 모든 예외를 지정된 상태로 설정합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugEngine2에서](../../../extensibility/debugger/reference/idebugengine2.md)상속된 메서드 외에도 인터페이스는 `IDebugEngine3` 다음 메서드를 노출합니다.

|방법|설명|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|DE가 디버깅 기호를 검색하는 데 사용할 경로 또는 경로를 설정합니다.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|아직 기호가 로드되지 않은 모든 모듈의 기호를 로드합니다.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|JUSTMyCode 정보에 대해 DE에 알려줍니다.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|메트릭에서 DE GUID를 설정합니다.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|현재 미해결 된 모든 예외를 지정된 상태로 설정합니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
