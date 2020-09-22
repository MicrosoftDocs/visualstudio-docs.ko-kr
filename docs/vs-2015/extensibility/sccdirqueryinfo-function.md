---
title: SccDirQueryInfo 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7334ddd1ce6c7f9feac63253246e55b65121e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841354"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 현재 상태에 대 한 정규화 된 디렉터리 목록을 검사 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pContext  
 진행 소스 제어 플러그 인 컨텍스트 구조입니다.  
  
 nDirs  
 진행 쿼리 하도록 선택한 디렉터리 수입니다.  
  
 lpDirNames  
 진행 쿼리할 디렉터리의 정규화 된 경로 배열입니다.  
  
 lpStatus  
 [in, out] 상태 플래그를 반환 하기 위한 소스 제어 플러그 인의 배열 구조입니다 (자세한 내용은 [디렉터리 상태 코드](../extensibility/directory-status-code-enumerator.md) 참조).  
  
## <a name="return-value"></a>반환 값  
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|쿼리가 성공 했습니다.|  
|SCC_E_OPNOTSUPPORTED|소스 코드 제어 시스템에서이 작업을 지원 하지 않습니다.|  
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다. 다시 시도 하는 것이 좋습니다.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|일반 오류입니다.|  
  
## <a name="remarks"></a>설명  
 함수는 `SCC_DIRSTATUS` 지정 된 각 디렉터리에 대 한 하나의 항목 ( [디렉터리 상태 코드](../extensibility/directory-status-code-enumerator.md)참조)에서 반환 배열을 비트의 비트 마스크로 채웁니다. 상태 배열은 호출자가 할당 합니다.  
  
 IDE는 디렉터리의 이름을 변경 하기 전에이 함수를 사용 하 여 해당 프로젝트가 있는지 여부를 쿼리하여 디렉터리가 소스 제어에서 사용 중인지 여부를 확인 합니다. 디렉터리가 소스 제어에서 사용 되 고 있지 않은 경우 IDE는 사용자에 게 적절 한 경고를 제공할 수 있습니다.  
  
> [!NOTE]
> 소스 제어 플러그 인에서 하나 이상의 상태 값을 구현 하지 않도록 선택 하는 경우에는 구현 되지 않은 비트를 0으로 설정 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [디렉터리 상태 코드](../extensibility/directory-status-code-enumerator.md)
