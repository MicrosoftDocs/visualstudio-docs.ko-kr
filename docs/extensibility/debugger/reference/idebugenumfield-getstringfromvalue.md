---
description: 이 메서드는 해당 값이 지정 된 열거형 상수의 이름을 가져옵니다.
title: 'IDebugEnumField:: GetStringFromValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 41d004a9b226646dd1196f1debc244cdf11efe32
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092581"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
이 메서드는 해당 값이 지정 된 열거형 상수의 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>매개 변수
`value`\
진행 열거 상수의 이름을 가져올 값입니다.

`pbstrValue`\
제한이 열거 상수의 이름을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 값에 연결 된 이름이 없으면가 반환 되 고, 그렇지 않으면 `S_FALSE` 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 동일한 값에 연결 된 이름이 둘 이상 있는 경우 열거형에 정의 된 첫 번째 이름이 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
