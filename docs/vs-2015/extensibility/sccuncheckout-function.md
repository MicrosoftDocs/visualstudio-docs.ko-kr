---
title: SccUncheckout 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3ae5ecd7568a10936479f72f92e9914132f2dcdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190860"
---
# <a name="sccuncheckout-function"></a>SccUncheckout 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 이전 체크 아웃 작업을 실행 취소 하 여 체크 아웃 전의 상태로 선택한 파일의 콘텐츠를 복원 합니다. 체크 아웃 후 파일에 대 한 모든 변경 내용이 손실 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 진행 소스 제어 플러그 인 컨텍스트 구조입니다.  
  
 hWnd  
 진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.  
  
 n  
 진행 배열에 지정 된 파일 수 `lpFileNames` 입니다.  
  
 lpFileNames 이름  
 진행 체크 아웃을 취소할 파일의 정규화 된 로컬 경로 이름 배열입니다.  
  
 fOptions  
 진행 명령 플래그 (사용 되지 않음).  
  
 pvOptions  
 진행 원본 제어 플러그 인 관련 옵션입니다.  
  
## <a name="return-value"></a>반환 값  
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|체크 아웃을 취소 했습니다.|  
|SCC_E_FILENOTCONTROLLED|선택한 파일은 소스 코드 제어에 있지 않습니다.|  
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다. 다시 시도 하는 것이 좋습니다.|  
|SCC_E_NONSPECIFICERROR|일반 오류입니다. 체크 아웃 취소가 실패 했습니다.|  
|SCC_E_NOTCHECKEDOUT|사용자가 파일을 체크 아웃 하지 않았습니다.|  
|SCC_E_NOTAUTHORIZED|사용자가이 작업을 수행할 수 없습니다.|  
|SCC_E_PROJNOTOPEN|프로젝트가 소스 제어에서 열리지 않았습니다.|  
|SCC_I_OPERATIONCANCELED|작업이 완료 되기 전에 취소 되었습니다.|  
  
## <a name="remarks"></a>설명  
 이 작업을 수행한 후 `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` 실행 취소를 체크 아웃 한 파일에 대해 및 플래그를 모두 지웁니다.  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
