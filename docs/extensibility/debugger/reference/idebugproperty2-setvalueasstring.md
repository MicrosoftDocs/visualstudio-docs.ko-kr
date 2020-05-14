---
title: 아이디버그프로퍼피2::세트밸류아스스트링 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 112ded163f38b93e9918387d8ca6beafb8282647
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721246"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
지정된 문자열에서 속성값을 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>매개 변수
`pszValue`\
【인】 설정할 값을 포함하는 문자열입니다.

`nRadix`\
【인】 모든 수치 정보를 해석하는 데 사용되는 방사형입니다. 이 경우 Radix를 자동으로 확인하려면 0이 될 수 있습니다.

`dwTimeout`\
【인】 이 메서드에서 반환하기 전에 기다릴 최대 시간(밀리초)을 지정합니다. 무기한 `INFINITE` 대기하는 데 사용합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 다음 표에서는 다른 가능한 값을 보여 주며 있습니다.

|값|Description|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|문자열을 속성 값으로 변환할 수 없거나 속성 값을 설정할 수 없습니다.|
|`E_SETVALUE_VALUE_IS_READONLY`|속성이 읽기 전용입니다.|

## <a name="see-also"></a>참조
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
