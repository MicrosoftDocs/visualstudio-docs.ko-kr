---
description: 이 메서드는 필드에 대 한 정보를 표시할 정보를 가져옵니다.
title: 'IDebugField:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: deebf0c8dafe64c8eb78ba5a1af0b8f96c70a18a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077059"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
이 메서드는 필드에 대 한 정보를 표시할 정보를 가져옵니다.

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
진행 표시할 정보를 선택 하는 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) 상수의 조합입니다. 필드가 기호를 나타내는 경우 일반적으로 기호 이름 및 형식입니다.

`pFieldInfo`\
제한이 제공 된 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 구조의 정보를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
