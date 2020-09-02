---
title: GUID_ARRAY | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0465188cd44ad14ef3f7df9f5eda619a5ecb6d0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160105"
---
# <a name="guid_array"></a>GUID_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

사용 가능한 디버그 엔진에 대 한 고유 식별자 배열을 설명 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagGUID_ARRAY  
{  
   DWORD dwCount;  
   GUID *Members;  
} GUID_ARRAY;  
```  
  
```csharp  
public struct GUID_ARRAY  
{  
   public uint dwCount;  
   public Guid Members;  
}  
```  
  
## <a name="terms"></a>용어  
 dwCount  
 배열의 고유 식별자 수입니다.  
  
 멤버  
 고유 식별자가 포함 된 배열입니다.  
  
## <a name="remarks"></a>설명  
 이 구조체는 [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) 메서드에서 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
