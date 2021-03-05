---
description: 디버그 주소가 지정 된 경우 기호 형식을 검색 합니다.
title: 'IDebugComPlusSymbolProvider:: GetTypeFromAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetTypeFromAddress
- GetTypeFromAddress
ms.assetid: 01f21ff9-e8a5-4e5f-9f7b-1b6de8b1432f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1dfcc7987c672ebf9647f33281b64d6d446a383e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163721"
---
# <a name="idebugcomplussymbolprovidergettypefromaddress"></a>IDebugComPlusSymbolProvider::GetTypeFromAddress
디버그 주소가 지정 된 경우 기호 형식을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetTypeFromAddress(
    IDebugAddress* pAddress,
    IDebugField**  ppField
);
```

```csharp
int GetTypeFromAddress(
    IDebugAddress   pAddress,
    out IDebugField ppField
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
진행 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스로 표시 되는 디버그 주소입니다.

`ppField`\
제한이 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) 인터페이스로 표시 되는 배열 형식을 반환 합니다.

## <a name="return-value"></a>반환 값
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="example"></a>예
다음 예제에서는 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) 인터페이스를 노출 하는 **Cdebug기호 공급자** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CDebugSymbolProvider::GetTypeFromAddress(
    IDebugAddress *pAddress,
    IDebugField **ppField)
{
    HRESULT hr = E_FAIL;
    CDEBUG_ADDRESS da;
    CDebugGenericParamScope* pGenScope = NULL;

    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromPrimitive );

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidWritePtr(ppField, IDebugField*));

    IfFailGo( pAddress->GetAddress(&da) );

    switch ( da.addr.dwKind )
    {
        case ADDRESS_KIND_METADATA_LOCAL:
        case ADDRESS_KIND_METADATA_PARAM:
        case ADDRESS_KIND_METADATA_FIELD:
        case ADDRESS_KIND_METADATA_ARRAYELEM:
        case ADDRESS_KIND_METADATA_METHOD:
            {
                IfFailGo( this->CreateClassType(da.GetModule(), da.tokClass, ppField) );
                break;
            }

        case ADDRESS_KIND_METADATA_RETVAL:
            {
                if ( da.addr.addr.addrRetVal.dwCorType )
                {

                    IfNullGo( pGenScope = new CDebugGenericParamScope(da.GetModule(), da.tokClass, da.GetMethod()), E_OUTOFMEMORY );
                    IfFailGo( this->CreateType((const COR_SIGNATURE*)(&da.addr.addr.addrRetVal.rgSig),
                                               da.addr.addr.addrRetVal.dwSigSize,
                                               da.GetModule(),
                                               mdMethodDefNil,
                                               pGenScope,
                                               ppField) );
                }
                else
                {
                    IfFailGo( this->CreateClassType(da.GetModule(), da.tokClass, ppField) );
                }

                break;
            }

        default:
            {
                ASSERT(!"Address type not supported.");
            }
    }

Error:

    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromPrimitive, hr );

    RELEASE( pGenScope );

    return hr;
}
```

## <a name="see-also"></a>참고 항목
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
