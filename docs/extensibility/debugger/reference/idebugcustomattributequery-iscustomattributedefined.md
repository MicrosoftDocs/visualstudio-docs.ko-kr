---
description: 지정 된 사용자 지정 특성이 정의 되어 있는지 여부를 확인 합니다.
title: 'IDebugCustomAttributeQuery:: IsCustomAttributeDefined | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery::IsCustomAttributeDefined
- IsCustomAttributeDefined
ms.assetid: c7425db6-4347-4f69-8f88-337ddaa34fa6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4ffd03313896db1a6bf5cb719adf2ecf5858243
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162968"
---
# <a name="idebugcustomattributequeryiscustomattributedefined"></a>IDebugCustomAttributeQuery::IsCustomAttributeDefined
지정 된 사용자 지정 특성이 정의 되어 있는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsCustomAttributeDefined(
    LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
    string pszCustomAttributeName
);
```

## <a name="parameters"></a>매개 변수
`pszCustomAttributeName`\
진행 사용자 지정 특성의 이름입니다.

## <a name="return-value"></a>반환 값
사용자 지정 특성이 정의 된 경우는를 반환 하 `S_OK` 고 그렇지 않으면를 반환 `S_FALSE` 합니다.

## <a name="example"></a>예
다음 예제에서는 [Idebugcustomattributequery](../../../extensibility/debugger/reference/idebugcustomattributequery.md) 인터페이스를 제공 하는 **Cdebugclassfieldsymbol** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CDebugClassFieldSymbol::IsCustomAttributeDefined(
    LPCOLESTR pszCustomAttribute
)
{
    HRESULT hr = S_FALSE;
    CComPtr<IMetaDataImport> pMetadata;
    mdToken token = mdTokenNil;
    CComPtr<IDebugField> pField;
    CComPtr<IDebugCustomAttributeQuery> pCA;

    ASSERT(IsValidWideStringPtr(pszCustomAttribute));

    METHOD_ENTRY( CDebugClassFieldSymbol::IsCustomAttributeDefined );

    IfFalseGo( pszCustomAttribute, E_INVALIDARG );

    IfFailGo( m_spSH->GetMetadata( m_spAddress->GetModule(), &pMetadata ) );

    IfFailGo( CDebugCustomAttribute::GetTokenFromAddress( m_spAddress, &token) );
    IfFailGo( pMetadata->GetCustomAttributeByName( token,
              pszCustomAttribute,
              NULL,
              NULL ) );
Error:

    METHOD_EXIT( CDebugClassFieldSymbol::IsCustomAttributeDefined, hr );

    if (hr != S_OK)
    {
        hr = S_FALSE;
    }

    return hr;
}
```

## <a name="see-also"></a>참고 항목
- [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)
