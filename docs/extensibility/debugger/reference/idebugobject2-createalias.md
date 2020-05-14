---
title: 아이디버그오브젝트2::창조알리아스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::CreateAlias
helpviewer_keywords:
- IDebugObject2::CreateAlias method
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03564e8b81eb4e11a2cd4f25e1047d326d62b21b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726300"
---
# <a name="idebugobject2createalias"></a>IDebugObject2::CreateAlias
이 개체에 대한 고유 ID 또는 별칭을 만들거나 기존 별칭을 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int CreateAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>매개 변수
`ppAlias`\
【아웃】 새(또는 기존) 별칭입니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 별칭은 개체가 메모리에 있는 동안 특정 개체를 나타내는 레이블입니다.

## <a name="see-also"></a>참조
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
