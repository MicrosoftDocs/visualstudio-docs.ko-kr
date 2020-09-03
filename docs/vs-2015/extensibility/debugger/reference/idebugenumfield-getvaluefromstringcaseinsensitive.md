---
title: 'IDebugEnumField:: GetValueFromStringCaseInsensitive | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: efe94a721c432cb1284df299ca267271ab5bef4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188926"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는 대/소문자를 구분 하지 않는 검색을 사용 하 여 열거형 상수의 이름과 연결 된 값을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszValue`  
 진행 값을 가져올 이름을 지정 하는 문자열입니다. C + +의 경우이는 와이드 문자열입니다.  
  
 `pValue`  
 제한이 연결 된 숫자 값을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 `S_FALSE` 이름이 열거형의 일부가 아니면가 반환 되 고, 그렇지 않으면이 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 대/소문자를 구분 하지 않습니다. 이름에 대/소문자를 구분 하는 c + +와 같은 언어에서 대/소문자를 구분 하는 검색이 필요한 경우 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)를 사용 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
