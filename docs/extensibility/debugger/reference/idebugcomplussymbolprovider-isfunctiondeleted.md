---
description: 지정 된 디버그 주소의 함수가 삭제 되었는지 확인 합니다.
title: 'IDebugComPlusSymbolProvider:: IsFunctionDeleted | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsFunctionDeleted
ms.assetid: b276bd25-6658-4898-bc36-04ecdf92aa2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcaf296381e6035613ebc496e440f10d1ec65baa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163709"
---
# <a name="idebugcomplussymbolproviderisfunctiondeleted"></a>IDebugComPlusSymbolProvider::IsFunctionDeleted
지정 된 디버그 주소의 함수가 삭제 되었는지 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsFunctionDeleted(
    IDebugAddress* pAddress
);
```

```csharp
int IsFunctionDeleted(
    IDebugAddress pAddress
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
진행 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스가 나타내는 디버그 주소입니다. 이 주소는 METHOD_ADDRESS 이어야 합니다.

## <a name="return-value"></a>반환 값
함수를 삭제 하면이 반환 `S_OK` 됩니다. 함수가 있으면를 반환 `S_FALSE` 합니다.

## <a name="example"></a>예
다음 예제에서는 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) 인터페이스를 노출 하는 **Cdebug기호 공급자** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CDebugSymbolProvider::IsFunctionDeleted(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));

    METHOD_ENTRY( CDebugSymbolProvider::IsFunctionDeleted );

    IfFalseGo( pAddress, S_FALSE );
    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->IsFunctionDeleted( address.addr.addr.addrMethod.tokMethod,
                                     address.addr.addr.addrMethod.dwVersion,
                                     address.addr.addr.addrMethod.dwOffset ))
    {

        // S_FALSE indicates the function is not deleted

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::IsFunctionDeleted, hr );

    if (!SUCCEEDED(hr))
    {
        hr = S_FALSE;
    }

    return hr;
}
```

## <a name="see-also"></a>참고 항목
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
