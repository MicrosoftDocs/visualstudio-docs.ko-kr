---
title: IDebugProgramHost2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722217"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
이 인터페이스는 프로그램에 대 한 호스트 (프로세스) 정보를 제공 합니다.

## <a name="syntax"></a>Syntax

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진은 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스와 동일한 개체에서이 인터페이스를 구현 하 여 호스팅 프로세스에 대 한 정보를 제공 합니다. 이는 선택적 인터페이스입니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) `IDebugProgram2` 를 호출 하 여이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProgramHost2` .

|메서드|설명|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|이 프로그램의 호스팅 프로세스에 대 한 제목, 이름 또는 파일 이름을 가져옵니다.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|이 프로그램의 호스팅 프로세스에 대 한 프로세스 식별자를 가져옵니다.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|이 프로그램의 호스팅 프로세스가 실행 되 고 있는 컴퓨터의 이름을 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
