---
title: 아이데버그필드::겟정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b3251db3426f87901ca0768800feaa36fef5373
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728851"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
이 메서드는 필드에 대 한 표시 가능한 정보를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

## <a name="parameters"></a>매개 변수
`dwFields`\
【인】 표시할 정보를 선택하는 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) 상수의 조합입니다. 필드가 기호를 나타내는 경우 일반적으로 기호 이름 및 유형입니다.

`pFieldInfo`\
【아웃】 제공된 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 구조의 정보를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
