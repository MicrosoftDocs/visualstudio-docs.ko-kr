---
title: 아이데버그제네릭파라필드::겟플래그 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFlags
- IDebugGenericParamField::GetFlags
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d131a5dc4a1fd64f2a82bff4f51f7cbc4a905a8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728002"
---
# <a name="idebuggenericparamfieldgetflags"></a>IDebugGenericParamField::GetFlags
이 제네릭 매개 변수에 대한 플래그를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetFlags(
    DWORD* pdwFlags
);
```

```csharp
int GetFlags(
    ref uint pdwFlags
);
```

## <a name="parameters"></a>매개 변수
`pdwFlags`\
【아웃】 이 제네릭 매개 변수에 대한 플래그를 반환합니다.

## <a name="return-value"></a>Return Value
성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
이러한 플래그에는 다양한 특수 제약 조건에 대한 정보가 포함되어 있습니다.

## <a name="example"></a>예제
다음 예제에서는 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) 인터페이스를 노출 하는 **CDebugGenericParamField 개체에** 대 한이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );

    IfFalseGo( pdwFlags, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    *pdwFlags = m_dwFlags;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );
    return hr;
}
```

## <a name="see-also"></a>참조
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
