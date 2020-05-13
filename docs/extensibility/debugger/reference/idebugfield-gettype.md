---
title: 아이디버그필드::겟타입 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetType
helpviewer_keywords:
- IDebugField::GetType method
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e052155524c962894af021bf5afdec50d182d68
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728796"
---
# <a name="idebugfieldgettype"></a>IDebugField::GetType
이 메서드는 필드의 형식을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetType( 
   IDebugField** ppType
);
```

```csharp
int GetType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>매개 변수
`ppType`\
【아웃】 필드 형식을 다른 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체로 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
