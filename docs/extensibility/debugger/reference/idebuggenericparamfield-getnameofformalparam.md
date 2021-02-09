---
title: 'IDebugGenericParamField:: GetNameOfFormalParam | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetNameOfFormalParam
- GetNameOfFormalParam
ms.assetid: 05032a83-49ce-4007-b5d6-7b56945b956c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94976f45ebb8d6d757507c2cf3b02dc909aa2729
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838979"
---
# <a name="idebuggenericparamfieldgetnameofformalparam"></a>IDebugGenericParamField::GetNameOfFormalParam
이 제네릭 매개 변수의 이름을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetNameOfFormalParam (
    BSTR* pbstrName
);
```

```csharp
int GetNameOfFormalParam (
    string pbstrName
);
```

## <a name="parameters"></a>매개 변수
`pbstrName`\
제한이 이 제네릭 매개 변수의 이름입니다.

## <a name="return-value"></a>Return Value
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="example"></a>예제
다음 예제에서는 [Idebuggenericparamfield](../../../extensibility/debugger/reference/idebuggenericparamfield.md) 인터페이스를 노출 하는 **CDebugGenericParamFieldType** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CDebugGenericParamFieldType::GetNameOfFormalParam(BSTR *pbstrName)
{
    HRESULT hr = S_OK;
    CComBSTR bstrName;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetNameOfFormalParam );

    IfFalseGo( pbstrName, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    IfNullGo( *pbstrName = SysAllocString(m_bstrName), E_OUTOFMEMORY );

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetNameOfFormalParam, hr );
    return hr;
}
```

## <a name="see-also"></a>참고 항목
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
