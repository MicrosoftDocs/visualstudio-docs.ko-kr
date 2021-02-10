---
title: 'IDebugObject2:: CreateAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::CreateAlias
helpviewer_keywords:
- IDebugObject2::CreateAlias method
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 48badc2f418dec9fd34906b6925db1c2a9dfd490
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953515"
---
# <a name="idebugobject2createalias"></a>IDebugObject2::CreateAlias
이 개체의 고유 ID 또는 별칭을 만들거나 기존 별칭을 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int CreateAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>매개 변수
`ppAlias`\
제한이 새 또는 기존 별칭입니다.

## <a name="return-value"></a>Return Value
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 별칭은 개체가 메모리에 있는 동안 특정 개체를 나타내는 레이블입니다.

## <a name="see-also"></a>참고 항목
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
