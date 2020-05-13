---
title: IDebug방화벽구성콜백2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 635771fc87326b28566058a43d4922b131ae1975
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728718"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
DCOM을 사용하는 디버그 엔진이 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 방화벽이 원격 디버깅을 차단하지 않도록 UI에 요청하도록 합니다.

## <a name="syntax"></a>구문

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 세션 디버그 관리자의 포트 개체에 의해 구현됩니다.

## <a name="methods"></a>메서드
 다음 표에서는 의 `IDebugFirewallConfigurationCallback2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|방화벽이 원격 디버깅을 차단하지 않도록 요청합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
