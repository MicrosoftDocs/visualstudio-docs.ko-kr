---
description: 포트 공급자가 새 포트를 추가할 수 있는지 확인 합니다.
title: 'IDebugPortSupplier2:: CanAddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad704eda53807d344b23736d2d9b55e172c36468
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072210"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
포트 공급자가 새 포트를 추가할 수 있는지 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Return Value
 포트를 추가할 수 있는 경우는를 반환 하 `S_OK` 고, 그렇지 않으면를 반환 `S_FALSE` 하 여이 포트 공급자에 추가할 수 있는 포트가 없음을 표시 합니다.

## <a name="remarks"></a>설명
 Addport 메서드를 호출 하기 전에이 메서드를 호출 합니다 .이 메서드는 포트를 추가 하 고 추가 하는 데 시간이 오래 걸릴 수 있으므로 [Addport](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
