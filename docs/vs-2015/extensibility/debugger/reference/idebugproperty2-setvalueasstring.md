---
title: 'IDebugProperty2:: SetValueAsString | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d50057570b5b067447321f975d4d33da8aa3de43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193432"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정 된 문자열에서 속성 값을 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszValue`  
 진행 설정할 값을 포함 하는 문자열입니다.  
  
 `nRadix`  
 진행 숫자 정보를 해석 하는 데 사용할 기 수입니다. 이는 기 수를 자동으로 결정 하는 0이 될 수 있습니다.  
  
 `dwTimeout`  
 진행 이 메서드에서 반환 될 때까지 대기할 최대 시간 (밀리초)을 지정 합니다. `INFINITE`무기한 대기 하려면를 사용 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 다음 표에서는 다른 가능한 값을 보여 줍니다.  
  
|값|설명|  
|-----------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|문자열을 속성 값으로 변환할 수 없거나 속성 값을 설정할 수 없는 경우|  
|`E_SETVALUE_VALUE_IS_READONLY`|속성이 읽기 전용입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
