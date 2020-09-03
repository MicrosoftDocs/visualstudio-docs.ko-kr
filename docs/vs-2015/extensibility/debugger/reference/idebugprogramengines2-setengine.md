---
title: 'IDebugProgramEngines2:: SetEngine | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7541971da9420b0527b7c9885f1421b8c2ce0075
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182179"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로그램 또는 프로그램 노드에서이 프로그램을 디버깅 하는 데 사용할 DE (디버그 엔진)를 알려 줍니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT SetEngine(   
   REFGUID guidEngine  
);  
```  
  
```csharp  
int SetEngine(   
   ref Guid guidEngine  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `guidEngine`  
 진행 DE의 GUID입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
