---
description: 이 프로그램에 대 한 GUID를 가져옵니다.
title: 'IDebugProgram2:: Get프로그래밍 Id | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad0b5c8af1723414e6805e362312f167f995fbe4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084508"
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

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 디버그 엔진 (DE)은 원래 [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 또는 [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드에 전달 된 프로그램 식별자를 반환 해야 합니다. 이를 통해 디버거 구성 요소에서 프로그램을 식별할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
