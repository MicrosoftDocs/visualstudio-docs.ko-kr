---
title: 'IDebugProgram2:: Get프로그래밍 Id | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7723333547e0aeac7fe7a73c0dc40b36f4b6e071
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890034"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
이 프로그램에 대 한 GUID를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetProgramId( 
   GUID* pguidProgramId
);
```

```csharp
int GetProgramId( 
   out Guid pguidProgramId
);
```

## <a name="parameters"></a>매개 변수
`pguidProgramId`\
제한이 `GUID` 이 프로그램에 대 한를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 디버그 엔진 (DE)은 원래 [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 또는 [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드에 전달 된 프로그램 식별자를 반환 해야 합니다. 이를 통해 디버거 구성 요소에서 프로그램을 식별할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
