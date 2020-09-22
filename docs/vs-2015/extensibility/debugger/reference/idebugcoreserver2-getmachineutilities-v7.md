---
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 131f5a5f276b3f93d2ede3d088556b6832cc3651
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842219"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는 서버에 대 한 컴퓨터 유틸리티를 가져옵니다.  
  
> [!NOTE]
> 이 메서드는 사용 되지 않습니다. 사용 안 함 ( [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] `E_NOTIMPL` 이 메서드가 호출 될 경우 항상를 반환 함). 기록을 위해 보존 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppUtil`  
 제한이 `IDebugMDMUtil2_V7` 컴퓨터 유틸리티 정보를 나타내는 인터페이스를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 `E_NOTIMPL`메서드가 구현 되지 않음을 나타내는를 항상 반환 합니다.  
  
## <a name="remarks"></a>설명  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]`E_NOTIMPL`이 메서드가 호출 되 면 항상를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
