---
title: SccHistory 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8df85c03201e46768c43fb64cc41b7fa081eb91a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841514"
---
# <a name="scchistory-function"></a>SccHistory 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 지정 된 파일의 기록을 표시 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pvContext`  
 진행 소스 제어 플러그 인 컨텍스트 구조입니다.  
  
 `hWnd`  
 진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.  
  
 `nFiles`  
 진행 배열에 지정 된 파일 수 `lpFileName` 입니다.  
  
 `lpFileName`  
 진행 파일의 정규화 된 이름 배열입니다.  
  
 `fOptions`  
 진행 명령 플래그 (현재 사용 되지 않음)입니다.  
  
 `pvOptions`  
 진행 원본 제어 플러그 인 관련 옵션입니다.  
  
## <a name="return-value"></a>반환 값  
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|버전 기록을 가져왔습니다.|  
|SCC_I_RELOADFILE|소스 제어 시스템은 기록을 가져오는 동안 디스크에서 파일을 수정 했습니다. 예를 들어 이전 버전의 파일을 가져오면 IDE에서이 파일을 다시 로드 해야 합니다.|  
|SCC_E_FILENOTCONTROLLED|파일이 소스 제어에 있지 않습니다.|  
|SCC_E_OPNOTSUPPORTED|소스 제어 시스템에서이 작업을 지원 하지 않습니다.|  
|SCC_E_NOTAUTHORIZED|사용자가이 작업을 수행할 수 없습니다.|  
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다. 다시 시도 하는 것이 좋습니다.|  
|SCC_E_PROJNOTOPEN|프로젝트가 열려 있지 않습니다.|  
|SCC_E_NONSPECIFICERROR|일반 오류입니다. 파일 히스토리를 가져올 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 원본 제어 플러그 인은를 부모 창으로 사용 하 여 각 파일의 기록을 표시 하는 자체 대화 상자를 표시할 수 있습니다 `hWnd` . 또는 지원 되는 경우 [Sccopenproject](../extensibility/sccopenproject-function.md) 에 제공 된 선택적 텍스트 출력 콜백 함수를 사용할 수 있습니다.  
  
 특정 상황에서 검사 중인 파일은이 호출을 실행 하는 동안 변경 될 수 있습니다. 예를 들어 [!INCLUDE[vsvss](../includes/vsvss-md.md)] 기록 명령은 사용자에 게 이전 버전의 파일을 가져올 수 있는 기회를 제공 합니다. 이 경우 소스 제어 플러그 인은를 반환 `SCC_I_RELOAD` 하 여 파일을 다시 로드 해야 한다고 IDE에 경고 합니다.  
  
> [!NOTE]
> 소스 제어 플러그 인이 파일 배열에 대해이 함수를 지원 하지 않으면 첫 번째 파일의 파일 기록만 표시할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
