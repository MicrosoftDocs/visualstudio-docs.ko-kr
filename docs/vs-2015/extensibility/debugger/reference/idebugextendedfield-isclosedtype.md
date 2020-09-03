---
title: 'IDebugExtendedField:: IsClosedType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a1cf28e8391a1dd37949c042bd7d58d9c8b7da06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148984"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

필드가 폐쇄형 형식을 나타내는지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT IsClosedType(  
   void  
);  
```  
  
```csharp  
int IsClosedType();  
```  
  
## <a name="return-value"></a>Return Value  
 필드가 닫힌 형식이 면는를 반환 하 `S_OK` 고, 그렇지 않으면를 반환 `S_FALSE` 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
