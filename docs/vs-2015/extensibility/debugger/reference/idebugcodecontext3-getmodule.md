---
title: 'IDebugCodeContext3:: GetModule | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3::GetModule
ms.assetid: 8e4317b8-8255-486c-a896-a68ed94f8aa1
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 328916a6e1ceb8979c1c10c7d94dca9725689125
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190913"
---
# <a name="idebugcodecontext3getmodule"></a>IDebugCodeContext3::GetModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 모듈의 인터페이스에 대 한 참조를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2 **ppModule  
);  
```  
  
```csharp  
public int GetModule(   
   out IDebugModule2 ppModule  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppModule`  
 제한이 디버그 모듈 인터페이스에 대 한 참조입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) 인터페이스를 노출 하는 **CDebugCodeContext** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.  
  
```cpp#  
HRESULT CDebugCodeContext::GetModule(IDebugModule2** ppModule)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
  
    IfFalseGo( ppModule, E_INVALIDARG );  
    *ppModule = NULL;  
  
    IfFailGo( this->GetModule(&pModule) );  
    IfFailGo( pModule->QueryInterface(IID_IDebugModule2, (void**) ppModule) );  
  
Error:  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)
