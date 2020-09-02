---
title: SccQueryInfo 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f951e7ef29fbba7225997276b31bd9f32731efc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199979"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 소스 제어에서 선택한 파일 집합에 대 한 상태 정보를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 진행 소스 제어 플러그 인 컨텍스트 구조입니다.  
  
 n  
 진행 배열에 지정 된 파일 수 `lpFileNames` 와 `lpStatus` 배열의 길이입니다.  
  
 lpFileNames 이름  
 진행 쿼리할 파일의 이름 배열입니다.  
  
 lpStatus  
 [in, out] 소스 제어 플러그 인에서 각 파일에 대 한 상태 플래그를 반환 하는 배열입니다. 자세한 내용은 [파일 상태 코드](../extensibility/file-status-code-enumerator.md)를 참조 하세요.  
  
## <a name="return-value"></a>반환 값  
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|쿼리가 성공 했습니다.|  
|SCC_E_ACCESSFAILURE|원본 제어 시스템에 액세스 하는 데 문제가 발생 했습니다. 네트워크 또는 경합 문제로 인해 발생 했을 수 있습니다. 다시 시도 하는 것이 좋습니다.|  
|SCC_E_PROJNOTOPEN|프로젝트가 소스 제어에서 열려 있지 않습니다.|  
|SCC_E_NONSPECIFICERROR|일반 오류입니다.|  
  
## <a name="remarks"></a>설명  
 `lpFileName`이 빈 문자열이 면 현재 업데이트할 상태 정보가 없습니다. 그렇지 않으면 상태 정보가 변경 되었을 수 있는 파일의 전체 경로 이름입니다.  
  
 반환 배열은 비트의 비트 마스크 일 수 있습니다 `SCC_STATUS_xxxx` . 자세한 내용은 [파일 상태 코드](../extensibility/file-status-code-enumerator.md)를 참조 하세요. 소스 제어 시스템은 일부 비트 형식을 지원 하지 않을 수 있습니다. 예를 들어를 `SCC_STATUS_OUTOFDATE` 제공 하지 않으면 비트가 설정 되지 않습니다.  
  
 이 함수를 사용 하 여 파일을 체크 아웃 하는 경우 다음 `MSSCCI` 상태 요구 사항을 확인 하세요.  
  
- `SCC_STATUS_OUTBYUSER` 현재 사용자가 파일을 체크 아웃 하면가 설정 됩니다.  
  
- `SCC_STATUS_CHECKEDOUT` 가 설정 되지 않은 경우 설정할 수 없습니다 `SCC_STATUS_OUTBYUSER` .  
  
- `SCC_STATUS_CHECKEDOUT` 는 파일이 지정 된 작업 디렉터리로 체크 아웃 된 경우에만 설정 됩니다.  
  
- 현재 사용자가 파일을 작업 디렉터리가 아닌 다른 디렉터리에 체크 아웃 하면이 `SCC_STATUS_OUTBYUSER` 설정 되지만는 설정 `SCC_STATUS_CHECKEDOUT` 되지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [파일 상태 코드](../extensibility/file-status-code-enumerator.md)
