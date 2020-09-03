---
title: 'IDebugProgramEngines2:: EnumPossibleEngines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a417fd4f0d90ffebd291179dee28a0e81f92cce9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182182"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 프로그램을 디버그할 수 있는 모든 가능한 디버그 엔진 (DE)의 Guid를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `celtBuffer`  
 진행 반환할 대상 Guid 수입니다. 또한 배열의 최대 크기를 지정 합니다 `rgguidEngines` .  
  
 `rgguidEngines`  
 [in, out] 채워질 끝 Guid의 배열입니다.  
  
 `pceltEngines`  
 제한이 반환 되는 실제 DE Guid 수를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)`버퍼가 충분히 크지 않은 경우 [c + +] 또는 [c #] 0x8007007A를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 엔진 수를 확인 하려면 `celtBuffer` 매개 변수를 0으로 설정 하 고 `rgguidEngines` 매개 변수를 null 값으로 설정 하 여이 메서드를 한 번 호출 합니다. 이 `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` 는 (c #의 경우 0X8007007A)를 반환 하 고 `pceltEngines` 매개 변수는 필요한 버퍼 크기를 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
