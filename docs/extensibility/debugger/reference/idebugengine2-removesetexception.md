---
description: 지정 된 예외를 제거 하 여 디버그 엔진에서 더 이상 처리 하지 않도록 합니다.
title: 'IDebugEngine2:: RemoveSetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b763291fccd39d46b32347d89df1a11e1b3d09f2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095409"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
지정 된 예외를 제거 하 여 디버그 엔진에서 더 이상 처리 하지 않도록 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>매개 변수
`pException`\
진행 제거할 예외를 설명 하는 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 구조체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 제거 되는 예외는 이전에 [Setexception](../../../extensibility/debugger/reference/idebugengine2-setexception.md) 메서드에 대 한 호출로 설정 되어 있어야 합니다.

 모든 set 예외를 한 번에 제거 하려면 [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
