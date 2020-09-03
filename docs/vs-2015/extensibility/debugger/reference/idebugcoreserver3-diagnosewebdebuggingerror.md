---
title: IDebugCoreServer3::D iagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 24f142a631df25cfbff8ed795736c0cbf4e59eaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205274"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

자동 연결이 실패 한 이유를 확인 하려고 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszUrl`  
 진행 현재 사용 되지 않습니다. 항상 null 값으로 설정 해야 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 다음은 일반적인 반환 코드입니다.  
  
|코드|Description|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|원격 서버에서 디버깅을 시작 하지 못한 이유를 확인할 수 없습니다.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|사용 권한이 부족 하거나 디버그 동사를 사용할 수 없기 때문일 수 있습니다. 원격 서버에서 디버그할 수 없습니다.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|웹 서버가 잠겨 있어 디버깅을 사용 하도록 설정 하는 데 필요한 디버그 동사를 차단 합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
