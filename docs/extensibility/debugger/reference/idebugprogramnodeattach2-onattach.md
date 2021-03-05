---
description: 연결 된 프로그램에 연결 하거나 연결 방법에 대 한 연결 프로세스를 지연 합니다.
title: 'IDebugProgramNodeAttach2:: OnAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d1fdb6f0e2fe41555dbbc3b1bcfd16a1a2b4240
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167050"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
연결 된 프로그램에 연결 하거나 [연결 방법에](../../../extensibility/debugger/reference/idebugengine2-attach.md) 대 한 연결 프로세스를 지연 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>매개 변수
`guidProgramId`\
[in] `GUID` 연결 된 프로그램에 할당 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. `S_FALSE` [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드를 호출 하지 않아야 하는 경우를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 이 [메서드는 attach 메서드를](../../../extensibility/debugger/reference/idebugengine2-attach.md) 호출 하기 전에 연결 프로세스 중에 호출 됩니다. `OnAttach`메서드는 연결 프로세스를 수행할 수 있습니다 .이 경우이 메서드는를 반환 `S_FALSE` 하거나 연결 프로세스를 메서드에 대해 지연 시킵니다 `IDebugEngine2::Attach` (메서드는를 `OnAttach` 반환 `S_OK` ). 두 이벤트에서 메서드는 `OnAttach` `GUID` 디버깅 되는 프로그램의를 지정 된로 설정할 수 있습니다 `GUID` .

## <a name="see-also"></a>참고 항목
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
