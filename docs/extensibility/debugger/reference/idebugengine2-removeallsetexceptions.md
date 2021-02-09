---
title: 'IDebugEngine2:: RemoveAllSetExceptions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca4fbf706fb9172aea2ac7a1304f1643a0061dc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878957"
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

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드에서 제거 된 예외는 [Setexception](../../../extensibility/debugger/reference/idebugengine2-setexception.md) 메서드에 대 한 이전 호출에 의해 설정 되었습니다.

 특정 예외를 제거 하려면 [Removesetexception](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
