---
title: SccDirDiff 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 81279e0fdb0df6600686adc57bb1c5489e8e7aab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841367"
---
# <a name="sccdirdiff-function"></a>SccDirDiff 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 클라이언트 디스크의 현재 로컬 디렉터리와 소스 제어에서 해당 하는 프로젝트 간의 차이를 표시 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pContext  
 진행 소스 제어 플러그 인 컨텍스트 구조입니다.  
  
 hWnd  
 진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.  
  
 lpDirName  
 진행 시각적 차이점을 표시할 로컬 디렉터리에 대 한 정규화 된 경로입니다.  
  
 dwFlags  
 진행 명령 플래그 (설명 부분 참조).  
  
 pvOptions  
 진행 원본 제어 플러그 인 관련 옵션입니다.  
  
## <a name="return-value"></a>반환 값  
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|디스크의 디렉터리는 소스 코드 제어의 프로젝트와 동일 합니다.|  
|SCC_I_FILESDIFFER|디스크의 디렉터리는 소스 코드 제어의 프로젝트와 다릅니다.|  
|SCC_I_RELOADFILE|파일이 나 프로젝트를 다시 로드 해야 합니다.|  
|SCC_E_FILENOTCONTROLLED|디렉터리가 소스 코드 제어에 있지 않습니다.|  
|SCC_E_NOTAUTHORIZED|사용자가이 작업을 수행할 수 없습니다.|  
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다. 다시 시도 하는 것이 좋습니다.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|일반 오류입니다.|  
|SCC_E_FILENOTEXIST|로컬 디렉터리를 찾을 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 이 함수는 지정 된 디렉터리에 대 한 변경 내용 목록을 사용자에 게 표시 하도록 소스 제어 플러그 인에 지시 하는 데 사용 됩니다. 플러그 인은 사용자의 디스크에 있는 사용자의 디렉터리와 버전 제어에서 해당 하는 프로젝트 간의 차이점을 표시 하기 위해 해당 창을 선택 형식으로 엽니다.  
  
 플러그 인에서 디렉터리 비교를 지 원하는 경우 "빠른 diff" 옵션이 지원 되지 않는 경우에도 파일 이름에 대 한 디렉터리 비교를 지원 해야 합니다.  
  
|`dwFlags`|해석|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|대/소문자를 구분 하지 않는 비교 (빠른 diff 또는 시각적 개체에 사용 될 수 있음)|  
|SCC_DIFF_IGNORESPACE|공백을 무시 합니다 (빠른 diff 또는 시각적 개체에 사용 될 수 있음).|  
|SCC_DIFF_QD_CONTENTS|소스 제어 플러그 인에서 지원 되는 경우 디렉터리를 바이트 단위로 자동으로 비교 합니다.|  
|SCC_DIFF_QD_CHECKSUM|플러그 인에서 지원 되는 경우는 체크섬을 통해 디렉터리를 자동으로 비교 하거나, 지원 되지 않는 경우 SCC_DIFF_QD_CONTENTS로 대체 합니다.|  
|SCC_DIFF_QD_TIME|플러그 인에서 지원 되는 경우는 해당 타임 스탬프를 통해 디렉터리를 자동으로 비교 하거나, 지원 되지 않는 경우 SCC_DIFF_QD_CHECKSUM 또는 SCC_DIFF_QD_CONTENTS를 대체 합니다.|  
  
> [!NOTE]
> 이 함수는 [Sccdiff](../extensibility/sccdiff-function.md)와 동일한 명령 플래그를 사용 합니다. 그러나 소스 제어 플러그 인은 디렉터리에 대해 "빠른 diff" 작업을 지원 하지 않도록 선택할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
