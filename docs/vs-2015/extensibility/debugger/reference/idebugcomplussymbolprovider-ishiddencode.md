---
title: 'IDebugComPlusSymbolProvider:: IsHiddenCode | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsHiddenCode
ms.assetid: 1352c6ab-7b92-4a16-b2d2-6520b628830e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecbd7aaa05b48efcf43bb299c9c3dc2be9c679ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187208"
---
# <a name="idebugcomplussymbolproviderishiddencode"></a>IDebugComPlusSymbolProvider::IsHiddenCode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정 된 디버거 주소에서 코드를 숨길지 여부를 결정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT IsHiddenCode(  
   IDebugAddress* pAddress  
);  
```  
  
```csharp  
int IsHiddenCode(  
   IDebugAddress pAddress  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pAddress`  
 진행 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스로 표시 되는 디버그 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 코드가 숨겨진 경우는를 반환 하 `S_OK` 고 그렇지 않으면를 반환 `S_FALSE` 합니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) 인터페이스를 노출 하는 **Cdebug기호 공급자** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.  
  
```cpp#  
HRESULT CDebugSymbolProvider::IsHiddenCode(  
    IDebugAddress* pAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));  
  
    METHOD_ENTRY( CDebugSymbolProvider::IsHiddenCode );  
  
    IfFalseGo( pAddress, S_FALSE );  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    if (!pModule->IsHiddenCode( address.addr.addr.addrMethod.tokMethod,  
                                address.addr.addr.addrMethod.dwVersion,  
                                address.addr.addr.addrMethod.dwOffset ))  
    {  
  
        // S_FALSE indicates this sequence point is not hidden  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::IsHiddenCode, hr );  
  
    if (!SUCCEEDED(hr))  
    {  
        hr = S_FALSE;  
    }  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
