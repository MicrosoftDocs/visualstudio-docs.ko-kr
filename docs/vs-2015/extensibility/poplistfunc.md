---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c3ae2ce451f076c33ea5613b71c6d262c1d7a0e
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2020
ms.locfileid: "90841879"
---
# <a name="poplistfunc"></a>POPLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 콜백은 IDE에 의해 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 제공 되며 소스 제어 플러그 인에서 파일 또는 디렉터리 목록을 업데이트 하는 데 사용 됩니다 (함수에도 제공 됨 `SccPopulateList` ).  
  
 사용자가 IDE에서 **get** 명령을 선택 하면 ide는 사용자가 가져올 수 있는 모든 파일의 목록 상자를 표시 합니다. 그러나 IDE는 사용자가 가져올 수 있는 모든 파일의 정확한 목록을 알 수 없습니다. 플러그 인에만이 목록이 있습니다. 다른 사용자가 소스 코드 제어 프로젝트에 파일을 추가한 경우 이러한 파일은 목록에 표시 되지만 IDE는 이러한 파일에 대해 알지 못합니다. IDE는 사용자가 가져올 수 있다고 생각 하는 파일 목록을 작성 합니다. 이 목록을 사용자에 게 표시 하기 전에 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 를 호출 하 여 `,` 소스 제어 플러그 인이 목록에서 파일을 추가 하 고 삭제할 수 있습니다.  
  
## <a name="signature"></a>서명  
 소스 제어 플러그 인은 다음 프로토타입을 사용 하 여 IDE 구현 함수를 호출 하 여 목록을 수정 합니다.  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 pvCallerData  
 `pvCallerData`호출자가 [SccPopulateList](../extensibility/sccpopulatelist-function.md)에 전달 하는 매개 변수입니다. 소스 제어 플러그 인은이 매개 변수의 내용에 대해 아무 것도 가정 하지 않습니다.  
  
 fAddRemove  
 인 `TRUE` 경우 `lpFileName` 파일 목록에 추가 해야 하는 파일입니다. 인 `FALSE` 경우 `lpFileName` 파일 목록에서 삭제 해야 하는 파일입니다.  
  
 nStatus  
 상태 `lpFileName` (비트의 조합입니다. `SCC_STATUS` 자세한 내용은 [파일 상태 코드](../extensibility/file-status-code-enumerator.md) 참조).  
  
 lpFileName  
 목록에서 추가 하거나 삭제할 파일 이름의 전체 디렉터리 경로입니다.  
  
## <a name="return-value"></a>Return Value  
  
|값|Description|  
|-----------|-----------------|  
|`TRUE`|플러그 인은이 함수를 계속 호출할 수 있습니다.|  
|`FALSE`|IDE 쪽에 문제가 있습니다 (예: 메모리 부족). 플러그 인에서 작업을 중지 해야 합니다.|  
  
## <a name="remarks"></a>설명  
 소스 제어 플러그 인에서 파일 목록에 추가 하거나 파일 목록에서 삭제 하려는 각 파일에 대해이 함수를 호출 하 여를 전달 `lpFileName` 합니다. `fAddRemove`플래그는 목록에 추가할 새 파일이 나 삭제할 이전 파일을 나타냅니다. `nStatus`매개 변수는 파일의 상태를 제공 합니다. SCC 플러그 인이 파일 추가 및 삭제를 마치면 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 호출에서 반환 됩니다.  
  
> [!NOTE]
> `SCC_CAP_POPULATELIST`Visual Studio에는 기능 비트가 필요 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDE에서 구현 하는 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [파일 상태 코드](../extensibility/file-status-code-enumerator.md)
