---
title: 'IDebugEnumField:: GetValueFromString | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f553b7f019dd89af771e057a46a11b1affed1308
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188948"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는 열거형 상수의 이름과 연결 된 값을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromString(  
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
 이 메서드는 대/소문자를 구분 합니다. 이름에 대/소문자를 구분 하지 않는 Visual Basic와 같은 언어에서 대/소문자를 구분 하지 않고 검색 해야 하는 경우 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)를 사용 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
