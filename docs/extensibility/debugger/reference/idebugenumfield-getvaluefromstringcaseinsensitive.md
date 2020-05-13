---
title: 이데버그에넘필드::겟값스트링케이스인감이 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551945ded9d1ba3e973f18c21463a896cbd478c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730245"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
이 메서드는 대/소문자를 구분하지 않음 검색을 사용하여 열거형 상수의 이름과 연결된 값을 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>매개 변수
`pszValue`\
【인】 값을 얻을 이름을 지정하는 문자열입니다. C++의 경우 이 문자열은 넓은 문자 문자열입니다.

`pValue`\
【아웃】 연결된 숫자 값을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 `S_FALSE`이름이 열거형 또는 오류 코드의 일부가 아닌 경우 을 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 대/소문자를 구분하지 않습니다. 대/소문자 구분 검색이 필요한 경우(예: 이름이 대/소문자를 구분하는 C++ 와 같은 언어에서) [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)을 사용합니다.

## <a name="see-also"></a>참조
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
