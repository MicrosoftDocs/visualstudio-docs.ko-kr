---
title: 'IDebugDynamicFieldCOMPlus:: GetTypeFromTypeDef | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetTypeFromTypeDef
- IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
ms.assetid: 7f6cd3d3-f4da-4893-be91-8dd104be8010
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 239ecc56f6d86b24dcda4e2b2191c66e1553780f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68142949"
---
# <a name="idebugdynamicfieldcomplusgettypefromtypedef"></a>IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

해당 토큰이 지정 된 형식을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetTypeFromTypeDef(  
   ULONG32       ulAppDomainID,  
   GUID          guidModule,  
   _mdToken      tokClass,  
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetTypeFromTypeDef(  
   uint            ulAppDomainID,  
   Guid            guidModule,  
   int             tokClass,  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ulAppDomainID`  
 진행 응용 프로그램 도메인의 식별자입니다.  
  
 `guidModule`  
 진행 모듈의 고유 식별자입니다.  
  
 `tokClass`  
 진행 형식을 나타내는 토큰입니다.  
  
 `ppType`  
 제한이 형식을 포함 하는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)
