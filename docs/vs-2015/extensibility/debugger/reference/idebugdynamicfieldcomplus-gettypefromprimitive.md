---
title: 'IDebugDynamicFieldCOMPlus:: GetTypeFromPrimitive | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
- GetTypeFromPrimitive
ms.assetid: d7f51e2a-1b72-489c-b7b6-4af7b7e4d663
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd843f488439370ad652b52949b524e0ecca8af8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198475"
---
# <a name="idebugdynamicfieldcomplusgettypefromprimitive"></a>IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

기본 형식이 지정 된 형식을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetTypeFromPrimitive(  
   DWORD         dwCorElementType,  
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetTypeFromPrimitive(  
   uint            dwCorElementType,  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwCorElementType`  
 진행 기본 형식을 나타내는 [Corelementtype 열거형](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) 의 값입니다.  
  
 `ppType`  
 제한이 유형을 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)
