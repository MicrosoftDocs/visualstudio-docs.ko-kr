---
title: SccRunScc 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d2b36bd226d4eb19a694347edcba51812ee6f771
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190878"
---
# <a name="sccrunscc-function"></a>SccRunScc 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 소스 제어 관리 도구를 호출 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
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
 진행 선택한 파일 이름의 배열입니다.  
  
## <a name="return-value"></a>반환 값  
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|소스 제어 관리 도구를 성공적으로 호출 했습니다.|  
|SCC_I_OPERATIONCANCELED|작업이 취소 되었습니다.|  
|SCC_E_INITIALIZEFAILED|소스 제어 시스템을 초기화 하지 못했습니다.|  
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다.|  
|SCC_E_CONNECTIONFAILURE|원본 제어 시스템에 연결 하지 못했습니다.|  
|SCC_E_FILENOTCONTROLLED|선택한 파일은 소스 제어에서 관리 되지 않습니다.|  
|SCC_E_NONSPECIFICERROR|일반 오류입니다.|  
  
## <a name="remarks"></a>설명  
 이 함수를 사용 하면 호출자가 외부 관리 도구를 통해 소스 제어 시스템의 모든 기능에 액세스할 수 있습니다. 소스 제어 시스템에 사용자 인터페이스가 없는 경우 소스 제어 플러그 인에서 필요한 관리 기능을 수행 하는 인터페이스를 구현할 수 있습니다.  
  
 이 함수는 현재 선택 된 파일에 대 한 개수 및 파일 이름 배열을 사용 하 여 호출 됩니다. 관리 도구에서 지 원하는 경우 파일 목록을 사용 하 여 관리 인터페이스의 파일을 미리 선택할 수 있습니다. 그렇지 않으면 목록을 무시할 수 있습니다.  
  
 이 함수는 일반적으로 사용자가 **파일** ** \<Source Control Server> **  ->  **소스 컨트롤** 메뉴에서 시작을 선택 하면 호출 됩니다. 레지스트리 항목을 설정 하 여이 **시작** 메뉴 옵션을 항상 사용 하지 않도록 설정 하거나 숨길 수 있습니다. 자세한 내용은 [방법: 소스 제어 플러그 인 설치](../extensibility/internals/how-to-install-a-source-control-plug-in.md) 를 참조 하세요. 이 함수는 [Sccinitialize](../extensibility/sccinitialize-function.md) 가 기능 비트를 반환 하는 경우에만 호출 됩니다 `SCC_CAP_RUNSCC` (이 기능 및 기타 기능 비트에 대 한 자세한 내용은 [기능 플래그](../extensibility/capability-flags.md) 참조).  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [방법: 소스 제어 플러그 인 설치](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [기능 플래그](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
