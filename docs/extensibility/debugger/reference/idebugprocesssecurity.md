---
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c81cda3a27cfe1ef0fecfefc9bbb790d4d5217
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723186"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` 는 프로세스에 연결 하는 것이 안전 하지 않은 사용자에 게 경고 하기 위해 포트 공급자에 의해 구현 됩니다.

## <a name="syntax"></a>Syntax

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProcessSecurity` .

|메서드|설명|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|포트 공급자에서 사용자 이름을 가져옵니다.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|디버깅 프로세스에 연결 하는 것은 안전 하지 않은 사용자에 게 경고 합니다.|

## <a name="remarks"></a>설명
 경고를 표시 하 고 연결 하려는 프로세스를 안전 하지 않은 것으로 간주할 수 있는 경우 사용자가 취소할 수 있도록이 인터페이스를 구현 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [Ports](../../../extensibility/debugger/ports.md)
- [포트 공급자](../../../extensibility/debugger/port-suppliers.md)
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
