---
title: 아이디버그바인더3:GetException개체및타이 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e25a0f7b4e1713a072359f1efdd962f36c50b774
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735744"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
이 메서드는 개체와 연결된 예외(있는 경우)를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>매개 변수
`ppException`\
【아웃】 예외를 나타내는 개체를 반환합니다.

`ppField`\
【아웃】 예외를 일으킬 수 있는 특정 필드를 나타내는 개체를 반환합니다(이 값은 null 값일 수 있음).

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

> [!NOTE]
> 예외가 있는지 확인하려면 `ppException`:에서 반환되는 값을 확인하여 null 값인 경우 이 개체와 예외가 연결되지 않습니다.

## <a name="see-also"></a>참조
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
