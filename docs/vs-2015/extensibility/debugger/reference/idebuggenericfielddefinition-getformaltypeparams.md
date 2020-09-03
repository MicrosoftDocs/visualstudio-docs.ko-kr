---
title: 'IDebugGenericFieldDefinition:: GetFormalTypeParams | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e4595cd8a93c266d0eb70e91b8ab8ca8aeb8cb5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180834"
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

매개 변수 수를 지정 하 여 형식 매개 변수를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```csharp  
int GetFormalTypeParams(  
   uint                          cParams,  
   out IDebugGenericParamField[] ppParams,  
   ref uint                      pcParams  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cParams`  
 진행 매개 변수 수입니다.  
  
 `ppParams`  
 제한이 형식 매개 변수의 배열입니다.  
  
 `pcParams`  
 [in, out] 배열의 매개 변수 수 `ppParams` 입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 형식 매개 변수를 왼쪽에서 오른쪽 순서로 반환 합니다. 예를 들어 사전은 \<K,V> IDebugFormalGenericParameters {K, V}를 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
