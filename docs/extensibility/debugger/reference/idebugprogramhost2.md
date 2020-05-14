---
title: 아이디버그프로그램호스트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64db456e0c438f8665f122c3cd1b079c2ad1cea1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722217"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
이 인터페이스는 프로그램에 대한 호스트(프로세스) 정보를 제공합니다.

## <a name="syntax"></a>구문

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진은 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스와 동일한 개체에 이 인터페이스를 구현하여 호스팅 프로세스에 대한 정보를 제공합니다. 이 인터페이스는 선택적 인터페이스입니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스를 `IDebugProgram2` 얻으려면 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugProgramHost2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|이 프로그램의 호스팅 프로세스의 제목, 친숙한 이름 또는 파일 이름을 가져옵니다.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|이 프로그램의 호스팅 프로세스의 프로세스 식별자를 가져옵니다.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|이 프로그램의 호스팅 프로세스가 실행 중인 컴퓨터의 이름을 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
