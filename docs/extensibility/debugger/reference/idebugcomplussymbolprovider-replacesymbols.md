---
title: IDebugComPlus 기호 제공자::대체 기호 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ReplaceSymbols
- IDebugComPlusSymbolProvider::ReplaceSymbols
ms.assetid: 82fbc8db-c4b1-432f-bec9-1a9dc09570be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90ef0ae096618b776182b397d196f2a4477abe5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733608"
---
# <a name="idebugcomplussymbolproviderreplacesymbols"></a>IDebugComPlusSymbolProvider::ReplaceSymbols
현재 디버그 기호를 지정된 데이터 스트림의 디버그 기호로 바꿉습니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ReplaceSymbols(
    ULONG32  ulAppDomainID,
    GUID     guidModule,
    IStream* pStream
);
```

```csharp
int ReplaceSymbols(
    uint    ulAppDomainID,
    Guid    guidModule,
    IStream pStream
);
```

## <a name="parameters"></a>매개 변수
`ulAppDomainID`\
【인】 응용 프로그램 도메인의 식별자입니다.

`guidModule`\
【인】 모듈의 고유 식별자입니다.

`pStream`\
【인】 새 기호가 포함된 데이터 스트림입니다.

## <a name="return-value"></a>Return Value
성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="example"></a>예제
다음 예제에서는 [IDebugComPlusSymbol공급자](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) 인터페이스를 노출 하는 **CDebugSymbolProvider** 개체에 대 한이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CDebugSymbolProvider::ReplaceSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IStream* pStream
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::ReplaceSymbols );

    IfFailGo( GetModule( idModule, &pModule ) );
    IfFailGo( pModule->ReplaceSymbols( pStream ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::ReplaceSymbols, hr );
    return hr;
}
```

## <a name="see-also"></a>참조
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
