---
title: 'IDebugSymbolSearchEvent2:: Get기호 Searchinfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c8ef097ed02ae90b03289e3a2f3a1ad3f0ad8618
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841483"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

기호 로드 프로세스에 대 한 결과를 검색 하기 위해 이벤트 처리기에 의해 호출 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```csharp  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pModule`  
 제한이 기호가 로드 된 모듈을 나타내는 IDebugModule3 개체입니다.  
  
 `pbstrDebugMessage`  
 [in, out] 모듈의 오류 메시지를 포함 하는 문자열을 반환 합니다. 오류가 없는 경우이 문자열에는 모듈의 이름만 포함 되지만 비워 두면 안 됩니다.  
  
> [!NOTE]
> [C + +] `pbstrDebugMessage` 는이 될 수 없으며 `NULL` 를 사용 하 여 해제 해야 합니다 `SysFreeString` .  
  
 `pdwModuleInfoFlags`  
 제한이 기호가 로드 되었는지 여부를 나타내는 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) 열거형의 플래그 조합입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 모듈에 대 한 디버깅 기호를 로드 하려고 시도한 후 처리기가 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) 이벤트를 수신 하면 처리기는 thismethod를 호출 하 여 해당 load의 결과를 확인할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
