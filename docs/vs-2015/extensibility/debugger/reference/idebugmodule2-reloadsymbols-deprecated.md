---
title: 'IDebugModule2:: ReloadSymbols_Deprecated | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ce816e20e59d407f9b3cd84e3dffa703d84a324
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189546"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

사용되지 않습니다. 사용 하지 마십시오. 이 모듈에 대 한 기호를 다시 로드 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```csharp  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszUrlToSymbols`  
 진행 기호 저장소에 대 한 경로입니다.  
  
 `pbstrDebugMessage`  
 제한이 모듈 창에서 모듈 이름 오른쪽에 표시 되는 상태 메시지 (예: 상태 또는 오류 메시지)를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 디버그 엔진은 항상를 반환 해야 합니다 `E_FAIL` .  
  
## <a name="remarks"></a>설명  
 이 메서드는 더 이상 지원 되지 않습니다. 대신 [loadsymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) 메서드를 구현 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
