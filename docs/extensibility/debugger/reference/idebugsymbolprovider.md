---
title: Idebug기호 공급자 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11e180288a9312d9af5a3d3b1bd63d8f2266f581
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719178"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
이 인터페이스는 기호 및 형식을 제공 하 여 필드로 반환 하는 기호 공급자를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
기호 공급자는 식 계산기에 기호 및 형식 정보를 제공 하기 위해이 인터페이스를 구현 해야 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
이 인터페이스는 COM의 `CoCreateInstance` 함수 (관리 되지 않는 기호 공급자의 경우)를 사용 하거나 적절 한 관리 코드 어셈블리를 로드 하 고 해당 어셈블리에 있는 정보를 기반으로 기호 공급자를 인스턴스화하여 가져옵니다. 디버그 엔진은 기호 공급자를 인스턴스화하여 식 계산기를 사용 하 여 조정 합니다. 이 인터페이스를 인스턴스화하는 한 가지 방법에 대해서는 예제를 참조 하세요.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는의 메서드를 보여 줍니다 `IDebugSymbolProvider` .

|메서드|설명|
|------------|-----------------|
|`Initialize`|더 이상 사용되지 않습니다. 사용하지 마십시오.|
|`Uninitialize`|더 이상 사용되지 않습니다. 사용하지 마십시오.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|디버그 주소를 포함 하는 필드를 가져옵니다.|
|`GetField`|더 이상 사용되지 않습니다. 사용하지 마십시오.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|문서 위치를 디버그 주소 배열에 매핑합니다.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|문서 컨텍스트를 디버그 주소 배열에 매핑합니다.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|디버그 주소를 문서 컨텍스트에 매핑합니다.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|디버그 주소에서 코드를 컴파일하는 데 사용 되는 언어를 가져옵니다.|
|`GetGlobalContainer`|더 이상 사용되지 않습니다. 사용하지 마십시오.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|정규화 된 메서드 이름을 나타내는 필드를 가져옵니다.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|정규화 된 클래스 이름을 나타내는 클래스 필드 형식을 가져옵니다.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|디버그 주소와 연결 된 네임 스페이스에 대 한 열거자를 만듭니다.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|기호 이름을 기호 형식에 매핑합니다.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|메서드에서 지정 된 디버그 주소 다음에 오는 디버그 주소를 가져옵니다.|

## <a name="remarks"></a>설명
이 인터페이스는 문서 위치를 디버그 주소에 매핑하고 그 반대의 경우도 마찬가지입니다.

## <a name="requirements"></a>요구 사항
헤더: sh

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>예
이 예제에서는 GUID가 지정 된 경우 기호 공급자를 인스턴스화하는 방법을 보여 줍니다 (디버그 엔진은이 값을 알고 있어야 함).

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>추가 정보
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
