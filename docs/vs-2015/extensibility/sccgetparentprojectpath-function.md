---
title: SccGetParentProjectPath 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a631936dee7608306edfcd86f686b788e57133f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200094"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 지정 된 프로젝트의 부모 프로젝트 경로를 결정 합니다. 이 함수는 사용자가 Visual Studio 프로젝트를 소스 제어에 추가할 때 호출 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pContext  
 진행 소스 제어 플러그 인 컨텍스트 포인터입니다.  
  
 hWnd  
 진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.  
  
 lpUser  
 [in, out] 사용자 이름 (NULL 종결자를 포함 하 여 최대 SCC_USER_SIZE)입니다.  
  
 lpProjPath  
 진행 프로젝트 경로를 식별 하는 문자열입니다 (NULL 종결자를 포함 하 여 최대 SCC_PRJPATH_SIZE).  
  
 lpAuxProjPath  
 [in, out] 프로젝트를 식별 하는 보조 문자열입니다 (NULL 종결자를 포함 하 여 최대 SCC_PRJPATH_SIZE).  
  
 lpParentProjPath  
 [in, out] 부모 프로젝트 경로를 식별 하는 출력 문자열입니다 (NULL 종결자를 포함 하 여 최대 SCC_PRJPATH_SIZE).  
  
## <a name="return-value"></a>반환 값  
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|부모 프로젝트 경로를 가져왔습니다.|  
|SCC_E_INITIALIZEFAILED|프로젝트를 초기화할 수 없습니다.|  
|SCC_E_INVALIDUSER|사용자가 소스 제어 플러그 인에 로그인 할 수 없습니다.|  
|SCC_E_UNKNOWNPROJECT|소스 제어 플러그 인에서 프로젝트를 알 수 없습니다.|  
|SCC_E_INVALIDFILEPATH|파일 경로가 잘못 되었거나 사용할 수 없습니다.|  
|SCC_E_NOTAUTHORIZED|사용자가이 작업을 수행할 수 없습니다.|  
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다. 다시 시도 하는 것이 좋습니다.|  
|SCC_E_PROJSYNTAXERR|프로젝트 구문이 잘못 되었습니다.|  
|SCC_E_CONNECTIONFAILURE|연결 문제를 저장 합니다.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|일반 오류입니다.|  
  
## <a name="remarks"></a>설명  
 이 함수는 성공 또는 실패 코드를 반환 하 고, 성공 하면 지정 된 `lpParentProjPath` 프로젝트에 대 한 전체 프로젝트 경로를 사용 하 여 변수를 채웁니다.  
  
 이 함수는 기존 프로젝트의 부모 프로젝트 경로를 반환 합니다. 루트 프로젝트의 경우 함수는 전달 된 프로젝트 경로 (즉, 동일한 루트 프로젝트 경로)를 반환 합니다. 프로젝트 경로는 소스 제어 플러그 인에만 의미가 있는 문자열입니다.  
  
 IDE는 `lpUser` 및 매개 변수에 대 한 변경 내용을 허용할 수 있도록 준비 됩니다 `lpAuxProjPath` . 사용자가 나중에이 프로젝트를 열 때 IDE는 이러한 문자열을 유지 하 고 [Sccopenproject](../extensibility/sccopenproject-function.md) 에 전달 합니다. 따라서 이러한 문자열은 소스 제어 플러그 인이 프로젝트와 연결 하는 데 필요한 정보를 추적 하는 방법을 제공 합니다.  
  
 이 함수는 사용자에 게 프로젝트를 선택 하 라는 메시지를 표시 하지 않는다는 점을 제외 하 고 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)와 비슷합니다. 또한 새 프로젝트를 만들지 않고 기존 프로젝트 에서만 작동 합니다.  
  
 `SccGetParentProjectPath`가 호출 되 면 `lpProjPath` 및가 `lpAuxProjPath` 비어 있지 않고 유효한 프로젝트에 해당 합니다. 이러한 문자열은 일반적으로 IDE에서 함수에 대 한 이전 호출에서 수신 `SccGetProjPath` 합니다.  
  
 `lpUser`인수는 사용자 이름입니다. IDE는 이전에 함수에서 받은 것과 동일한 사용자 이름을 전달 하 `SccGetProjPath` 고, 소스 제어 플러그 인은이 이름을 기본값으로 사용 해야 합니다. 사용자에 게 플러그 인에 대 한 열린 연결이 이미 있는 경우 플러그 인은 함수를 자동으로 작동 하는지 확인 하기 위해 모든 프롬프트를 제거 하려고 합니다. 그러나 로그인에 실패 하는 경우 플러그 인은 사용자에 게 로그인을 요청 하 고 유효한 로그인을 받으면 해당 이름을 다시 전달 합니다 `lpUser` . 플러그 인이이 문자열을 변경할 수 있으므로 IDE는 항상 크기 (+ 1)의 버퍼를 할당 `SCC_USER_LEN` 합니다. 문자열이 변경 된 경우 새 문자열은 올바른 로그인 이름 이어야 합니다 (적어도 이전 문자열).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject 및 SccGetParentProjectPath에 대 한 기술 정보  
 소스 제어 시스템에서 사용자에 게 위치를 선택 하 라는 메시지가 표시 되는 횟수를 최소화 하기 위해 Visual Studio에서 솔루션 및 프로젝트를 소스 제어에 추가 하는 것이 간소화 되었습니다. 소스 제어 플러그 인에서 새 함수 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) 및 함수를 모두 지 원하는 경우 이러한 변경 내용은 Visual Studio에 의해 활성화 됩니다 `SccGetParentProjectPath` . 그러나 다음 레지스트리 항목을 사용 하 여 이러한 변경 내용을 사용 하지 않도록 설정 하 고 이전 Visual Studio (소스 제어 플러그 인 API 버전 1.1) 동작으로 되돌릴 수 있습니다.  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001  
  
 이 레지스트리 항목이 없거나 dword: 00000000으로 설정 된 경우 Visual Studio는 새 함수인 및를 사용 하려고 시도 `SccCreateSubProject` `SccGetParentProjectPath` 합니다.  
  
 레지스트리 항목을 dword: 00000001로 설정 하면 Visual Studio에서는 이러한 새 함수를 사용 하려고 시도 하지 않으며, 소스 제어에 추가 하는 작업은 이전 버전의 Visual Studio와 동일 하 게 작동 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
