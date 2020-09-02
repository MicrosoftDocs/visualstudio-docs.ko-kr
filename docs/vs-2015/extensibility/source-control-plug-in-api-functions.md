---
title: 소스 제어 플러그 인 API 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 02e2c7ee92ab138de7bee0d58835898f3bd0a58b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160611"
---
# <a name="source-control-plug-in-api-functions"></a>소스 제어 플러그 인 API 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

소스 제어 플러그 인 API는이 API에 따라 소스 제어 플러그 인에서 구현 해야 하는 다음 함수를 제공 합니다. 각 함수의 시그니처와 비트 플래그 및 기타 매개 변수와 연관 된 의미 체계는이 참조에 자세히 설명 되어 있습니다.  
  
## <a name="initialization-and-housekeeping-functions"></a>초기화 및 정리 함수  
  
|함수|설명|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|프로젝트를 닫습니다.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|지정 된 명령에 대 한 고급 옵션을 사용자에 게 표시 합니다.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|소스 제어 플러그 인의 버전을 반환 합니다.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|소스 제어 플러그 인을 초기화 합니다. 플러그 인의 각 인스턴스에 대해 한 번씩 호출 됩니다.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|프로젝트를 엽니다.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|다양 한 옵션을 설정 하는 데 사용 되는 일반 함수입니다. 각 옵션은로 시작 `SCC_OPT_xxx` 하 고 고유 하 게 정의 된 값 집합을 가집니다.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|소스 제어 플러그 인을 분리 해야 할 때 한 번 호출 됩니다.|  
  
## <a name="core-source-control-functions"></a>핵심 소스 제어 함수  
  
|함수|설명|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|정규화 된 경로 이름으로 지정 된 파일 배열을 소스 제어 시스템에 추가 합니다.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|사용자가 이미 소스 제어 시스템에 있는 파일을 검색 한 다음 해당 파일을 현재 프로젝트의 일부로 만들 수 있습니다.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|파일의 배열을 검사 합니다.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|파일 배열을 체크 아웃 합니다.|  
|[SccDiff](../extensibility/sccdiff-function.md)|정규화 된 경로 이름으로 지정 된 로컬 사용자 파일과 소스 제어에서 사용 하는 버전 간의 차이점을 보여 줍니다.|  
|[SccGet](../extensibility/sccget-function.md)|파일 집합의 읽기 전용 복사본을 검색 합니다.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|호출자가 요청한 파일의 상태를 확인 합니다 (via `SccQueryInfo` ).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|플러그 인에 의미 있는 프로젝트 경로를 사용자에 게 표시 하도록 소스 제어 플러그 인을 설정 합니다.|  
|[SccHistory](../extensibility/scchistory-function.md)|정규화 된 로컬 파일 이름 배열의 기록을 표시 합니다.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|현재 상태에 대 한 파일 목록을 검사 합니다. 또한은 함수를 사용 하 여 `pfnPopulate` 파일이의 조건과 일치 하지 않는 경우 호출자에 게 알립니다 `nCommand` .|  
|[SccProperties](../extensibility/sccproperties-function.md)|정규화 된 파일의 속성을 표시 합니다.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|현재 상태에 대 한 정규화 된 파일 목록을 검사 합니다.|  
|[SccRemove](../extensibility/sccremove-function.md)|소스 제어 시스템에서 정규화 된 파일의 배열을 제거 합니다.|  
|[SccRename](../extensibility/sccrename-function.md)|소스 제어 시스템에서 지정 된 파일의 이름을 새 이름으로 바꿉니다.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|원본 제어 시스템의 전체 기능 범위에 액세스 합니다.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|파일 배열의 체크 아웃을 취소 합니다.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>추가 기능을 지 원하는 함수 (소스 제어 플러그 인 API 버전 1.2)  
 이 함수 그룹은 소스 제어 플러그 인 API 버전 1.2에 포함 된 추가 기능을 정의 합니다. 이러한 기능을 통해 고급 소스 제어 기능 및 기능에 액세스할 수 있습니다.  
  
|함수|설명|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|일괄 처리 작업을 시작 합니다.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|기존 부모 프로젝트에서 지정 된 이름의 하위 프로젝트를 만듭니다.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|정규화 된 경로 이름으로 지정 된 로컬 사용자 디렉터리와 원본 제어 데이터베이스 위치 간의 차이점을 보여 줍니다.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|현재 상태에 대 한 정규화 된 디렉터리 목록을 검사 합니다.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|일괄 처리 작업을 종료 합니다.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|지정 된 프로젝트의 부모 경로를 반환 합니다 (프로젝트가 있어야 함).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|파일에 대 한 여러 체크 아웃이 허용 되는지 여부를 확인 합니다.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|플러그 인이 MSSCCPRJ.SCC를 만들지 여부를 확인 합니다. SCC 파일.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>고급 기능을 지 원하는 함수 (소스 제어 플러그 인 API 버전 1.3)  
 이 함수 그룹은 소스 제어 플러그 인 API 버전 1.3에 포함 된 추가 기능을 정의 합니다. 이러한 기능을 통해 고급 소스 제어 기능 및 기능에 액세스할 수 있습니다.  
  
|함수|설명|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|원본 제어의 파일 목록을 현재 프로젝트에 추가 합니다.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|사용자 인터페이스 없이 소스 제어에서 파일 목록을 검색 합니다.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|소스 제어에서 로컬 파일과 다른 파일 목록을 검색 합니다.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|소스 제어 플러그 인에서 지 원하는 확장 기능을 지정 하는 플래그를 검색 합니다.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|사용자 관련 옵션을 검색 합니다.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|소스 제어에서 사용할 프로젝트 또는 프로젝트의 디렉터리 및 파일 목록을 검사 합니다. 찾은 각 디렉터리와 파일 이름이 콜백 함수에 전달 됩니다.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|파일 목록에 대 한 이름 변경을 검사 합니다. 각 파일 이름은 변경 상태를 사용 하 여 콜백 함수에 전달 됩니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: scc. h  
  
 (환경 SDK 공통 포함 폴더에는 기본적으로 *[drive]* FileFiles\VSIP dEnvSDK\common\inc;에 제공 됩니다 .이 폴더에는 MSSCCI 샘플, *[drive]* FILEFILES\VSIP t\MSSCCI)를 사용 하 여 VSIP 폴더에도 제공 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)   
 [소스 제어 플러그 인 만들기](../extensibility/internals/creating-a-source-control-plug-in.md)
