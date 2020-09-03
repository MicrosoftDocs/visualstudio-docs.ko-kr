---
title: POPDIRLISTFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77e4701d3d8ec54fd37d6483f55b10a28af65b15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194056"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 함수에 제공 되는 콜백 함수로, 디렉터리 및 파일 이름 (선택 사항)의 컬렉션을 업데이트 하 여 소스 제어에서 찾을 수 있도록 합니다.  
  
 `POPDIRLISTFUNC`콜백은 실제로 소스 제어에 있는 해당 디렉터리와 파일 이름 (함수에 지정 된 목록)에 대해서만 호출 해야 합니다 `SccPopulateDirList` .  
  
## <a name="signature"></a>서명  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 pvCallerData  
 진행 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)에 지정 된 사용자 값입니다.  
  
 bFolder  
 [in] `TRUE` 의 이름이 디렉터리 이면이 고, `lpDirectoryOrFileName` 그렇지 않으면 파일 이름입니다.  
  
 lpDirectoryOrFileName  
 진행 소스 코드 제어 아래에 있는 디렉터리 또는 파일 이름의 전체 로컬 경로입니다.  
  
## <a name="return-value"></a>반환 값  
 IDE에서 적절 한 오류 코드를 반환 합니다.  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|처리를 계속합니다.|  
|SCC_I_OPERATIONCANCELED|처리를 중지합니다.|  
|SCC_E_xxx|적절 한 소스 제어 오류는 처리를 중지 해야 합니다.|  
  
## <a name="remarks"></a>설명  
 `fOptions`함수의 매개 변수에 `SccPopulateDirList` 플래그가 포함 된 경우 `SCC_PDL_INCLUDEFILES` 목록에는 디렉터리 이름 뿐만 아니라 파일 이름도 포함 될 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDE에서 구현 하는 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [오류 코드](../extensibility/error-codes.md)
