---
title: 아이데버그 심볼공급자 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719178"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
이 인터페이스는 기호 및 형식을 제공하여 필드로 반환하는 기호 공급자를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
기호 공급자는 식 계산기에 기호 및 형식 정보를 제공 하려면이 인터페이스를 구현 해야 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
이 인터페이스는 COM의 `CoCreateInstance` 함수(관리되지 않는 기호 공급자)를 사용하거나 적절한 관리 코드 어셈블리를 로드하고 해당 어셈블리에 있는 정보를 기반으로 기호 공급자를 인스턴스화하여 가져옵니다. 디버그 엔진은 식 계산기와 협력하여 작업하도록 기호 공급자를 인스턴스화합니다. 이 인터페이스를 인스턴스화하는 한 가지 방법은 예제를 참조하십시오.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는 의 `IDebugSymbolProvider`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|`Initialize`|사용되지 않습니다. 사용하지 마십시오.|
|`Uninitialize`|사용되지 않습니다. 사용하지 마십시오.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|디버그 주소가 포함된 필드를 가져옵니다.|
|`GetField`|사용되지 않습니다. 사용하지 마십시오.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|문서 위치를 디버그 주소 배열에 매핑합니다.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|문서 컨텍스트를 디버그 주소 배열에 매핑합니다.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|디버그 주소를 문서 컨텍스트에 매핑합니다.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|디버그 주소에서 코드를 컴파일하는 데 사용되는 언어를 가져옵니다.|
|`GetGlobalContainer`|사용되지 않습니다. 사용하지 마십시오.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|정규화된 메서드 이름을 나타내는 필드를 가져옵니다.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|정규화된 클래스 이름을 나타내는 클래스 필드 형식을 가져옵니다.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|디버그 주소와 연결된 네임스페이스에 대한 열거형기를 만듭니다.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|기호 이름을 기호 유형에 매핑합니다.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|메서드에서 지정된 디버그 주소를 따르는 디버그 주소를 가져옵니다.|

## <a name="remarks"></a>설명
이 인터페이스는 문서 위치를 디버그 주소로 매핑하고 그 반대의 경우도 마찬가지입니다.

## <a name="requirements"></a>요구 사항
헤더: sh.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="example"></a>예제
이 예제에서는 GUID(디버그 엔진이 이 값을 알고 있어야 함)가 주어지면 기호 공급자를 인스턴스화하는 방법을 보여 주었습니다.

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

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
