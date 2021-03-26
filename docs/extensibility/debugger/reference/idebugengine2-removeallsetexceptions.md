---
description: 특정 런타임 아키텍처 또는 언어에 대해 IDE에서 설정한 예외 목록을 제거 합니다.
title: 'IDebugEngine2:: RemoveAllSetExceptions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b40da7391fc360b68da70f02f4d32afb92e83a58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087940"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
특정 런타임 아키텍처 또는 언어에 대해 IDE에서 설정한 예외 목록을 제거 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT RemoveAllSetExceptions( 
   REFGUID guidType
);
```

```csharp
int RemoveAllSetExceptions( 
   ref Guid guidType
);
```

## <a name="parameters"></a>매개 변수
`guidType`\
진행 언어의 GUID 이거나 런타임 아키텍처와 관련 된 디버그 엔진의 GUID입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드에서 제거 된 예외는 [Setexception](../../../extensibility/debugger/reference/idebugengine2-setexception.md) 메서드에 대 한 이전 호출에 의해 설정 되었습니다.

 특정 예외를 제거 하려면 [Removesetexception](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
