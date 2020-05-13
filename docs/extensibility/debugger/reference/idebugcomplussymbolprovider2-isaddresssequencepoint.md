---
title: IDebugComPlus 기호제공자2::이주소시퀀스포인트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::IsAddressSequencePoint
- IsAddressSequencePoint
ms.assetid: 89b27c57-5295-428b-8229-a402500d8cd3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b9f1f3df8b96e9f9b25bf630206ce37bcd27635
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733412"
---
# <a name="idebugcomplussymbolprovider2isaddresssequencepoint"></a>IDebugComPlusSymbolProvider2::IsAddressSequencePoint
지정된 디버그 주소가 시퀀스 지점인지 확인합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsAddressSequencePoint(
    IDebugAddress* pAddress
);
```

```csharp
int IsAddressSequencePoint(
    IDebugAddress pAddress
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
【인】 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스로 표시되는 디버그 주소입니다.

## <a name="return-value"></a>Return Value
디버그 주소가 시퀀스 지점인 경우 반환합니다. `S_OK` 그렇지 않으면 `S_FALSE`을 반환합니다.

## <a name="example"></a>예제
다음 예제에서는 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) 인터페이스를 노출하는 **CDebugSymbolProvider** 개체에 대해 이 메서드를 구현하는 방법을 보여 줍니다.

```cpp
HRESULT CDebugSymbolProvider::IsAddressSequencePoint(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );

    IfFalseGo( pAddress, E_INVALIDARG );

    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->IsSequencePoint( address.addr.addr.addrMethod.tokMethod,
                                   address.addr.addr.addrMethod.dwVersion,
                                   address.addr.addr.addrMethod.dwOffset ))
    {

        // S_FALSE indicates this is not a sequence point

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );

    return hr;
}
```

## <a name="see-also"></a>참조
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
