---
title: 'IDebugModOpt:: GetModOpts | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 319e059116e46d532a7c199ab863538d2154999a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162528"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

선택적 한정자 목록을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetModOpts(  
   ULONG  celt,  
   BSTR*  rgelt,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetModOpts(  
   uint         celt,  
   out string[] rgelt,  
   ref uint     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `celt`  
 진행 반환 되는 요소 수입니다.  
  
 `rgelt`  
 제한이 옵션이 포함 된 배열을 반환 합니다.  
  
 `pceltFetched`  
 [in, out] 배열에서 반환 된 요소의 수 `rgelt` 입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
