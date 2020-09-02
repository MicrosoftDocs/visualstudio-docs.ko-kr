---
title: METADATA_ADDRESS_ARRAYELEM | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f558dc11f4f338cd370442bf9feaed419ce29411
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547600"
---
# <a name="metadata_address_arrayelem"></a>METADATA_ADDRESS_ARRAYELEM
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 구조체는 배열 내의 배열 요소를 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {  
   _mdToken tokMethod;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_ARRAYELEM;  
```  
  
```csharp  
public struct METADATA_ADDRESS_ARRAYELEM {  
   public int  tokMethod;  
   public uint dwIndex;  
}  
```  
  
## <a name="terms"></a>용어  
 tokMethod  
 이 요소가 속하는 배열의 ID입니다.  
  
 [C + +] `_mdToken` 는 `typedef` 32 비트에 대 한입니다 `int` .  
  
 dwIndex  
 배열 내에 있는이 요소의 인덱스입니다.  
  
## <a name="remarks"></a>설명  
 이 구조체는 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` 구조체의 필드가 `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_ARRAYELEM` ( [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 열거형의 값)로 설정 된 경우 DEBUG_ADDRESS_UNION 구조체의 공용 구조체의 일부입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
