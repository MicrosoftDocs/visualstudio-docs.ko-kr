---
title: 'IDebugGenericParamField:: GetFlags | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728002"
---
# <a name="idebuggenericparamfieldgetflags"></a>IDebugGenericParamField::GetFlags
이 제네릭 매개 변수에 대 한 플래그를 검색 합니다.

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
제한이 이 제네릭 매개 변수에 대 한 플래그를 반환 합니다.

## <a name="return-value"></a>반환 값
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
이러한 플래그는 다양 한 특수 제약 조건에 대 한 정보를 포함 합니다.

## <a name="example"></a>예
다음 예제에서는 [Idebuggenericparamfield](../../../extensibility/debugger/reference/idebuggenericparamfield.md) 인터페이스를 노출 하는 **CDebugGenericParamFieldType** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

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

## <a name="see-also"></a>추가 정보
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
