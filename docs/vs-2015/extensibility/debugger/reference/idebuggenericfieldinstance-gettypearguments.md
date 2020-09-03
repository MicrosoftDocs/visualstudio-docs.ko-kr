---
title: 'IDebugGenericFieldInstance:: GetTypeArguments | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetTypeArguments
- IDebugGenericFieldInstance::GetTypeArguments
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bef4d6c0d36eafd0279d97ecad2d1d2cc0656e2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180825"
---
# <a name="idebuggenericfieldinstancegettypearguments"></a>IDebugGenericFieldInstance::GetTypeArguments
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인스턴스에 대 한 형식 매개 변수 인수를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetTypeArguments(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   ULONG32*      pcArgs  
);  
```  
  
```csharp  
int GetTypeArguments(  
   uint              cArgs,  
   out IDebugField[] ppArgs,  
   ref uint          pcArgs  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cArgs`  
 진행 형식 매개 변수 수입니다.  
  
 `ppArgs`  
 제한이 형식 매개 변수의 배열을 반환 합니다.  
  
 `pcArgs`  
 [in, out] 배열에 있는 멤버의 수 `ppArgs` 입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
