---
title: 이데버그에넘필드::겟스트링From밸류 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de59c573f7e233ea2aacb0dfa38826051c59373
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730293"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
이 메서드는 해당 값이 주어진 열거형 상수의 이름을 가져옵니다.

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
【인】 열거형 상수의 이름을 얻을 수 있는 값입니다.

`pbstrValue`\
【아웃】 열거형 상수의 이름을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 `S_FALSE` 값에 연결된 이름이 없는 경우 반환하거나 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 동일한 값과 연결된 이름이 두 개 이상 인 경우 열거형에 정의된 첫 번째 이름이 반환됩니다.

## <a name="see-also"></a>참조
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
