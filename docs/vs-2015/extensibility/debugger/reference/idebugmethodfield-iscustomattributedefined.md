---
title: 'IDebugMethodField:: IsCustomAttributeDefined | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7fcc496131cd27837dc53fe2ecba05cf6b2c44d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162555"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

특정 사용자 지정 특성이 정의 되어 있는지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszCustomAttributeName`  
 진행 찾을 사용자 지정 특성의 이름을 포함 하는 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드에 사용자 지정 특성이 정의 되어 있으면 S_OK을 반환 하 고, 그렇지 않으면 S_FALSE을 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
