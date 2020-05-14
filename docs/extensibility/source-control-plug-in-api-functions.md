---
title: 소스 제어 플러그인 API 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce685729dda8750d772e244398b736cff4951b72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699916"
---
# <a name="source-control-plug-in-api-functions"></a>소스 제어 플러그 인 API 함수
소스 제어 플러그인 API는 이 API에 따라 소스 제어 플러그인에 의해 구현되어야 하는 다음 기능을 제공합니다. 각 함수의 시그니처와 비트 플래그 및 기타 매개 변수와 연관된 의미 체계는 이 참조에서 자세히 설명합니다.

## <a name="initialization-and-housekeeping-functions"></a>초기화 및 하우스키핑 기능

|함수|설명|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|프로젝트를 닫습니다.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|지정된 명령에 대한 고급 옵션을 사용자에게 요청합니다.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|소스 제어 플러그인 의 버전을 반환합니다.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|소스 제어 플러그인을 초기화합니다. 플러그인의 각 인스턴스에 대해 한 번 호출됩니다.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|프로젝트를 엽니다.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|다양한 옵션을 설정하는 데 사용되는 일반 함수입니다. 각 옵션에서 `SCC_OPT_xxx` 시작하여 자체적으로 정의된 값 집합을 가짐|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|소스 제어 플러그인의 플러그를 뽑아야 할 때 한 번 호출됩니다.|

## <a name="core-source-control-functions"></a>핵심 소스 제어 기능

|함수|설명|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|소스 제어 시스템에 정규화된 경로 이름으로 지정된 파일 배열을 추가합니다.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|사용자가 소스 제어 시스템에 이미 있는 파일을 찾아본 다음 해당 파일을 현재 프로젝트의 일부로 만들 수 있습니다.|
|[SccCheckin](../extensibility/scccheckin-function.md)|파일 배열을 체크 인합니다.|
|[SccCheckout](../extensibility/scccheckout-function.md)|파일 배열을 체크 아웃합니다.|
|[SccDiff](../extensibility/sccdiff-function.md)|정규화된 경로 이름으로 지정된 로컬 사용자 파일과 소스 제어의 버전 간의 차이점을 표시합니다.|
|[SccGet](../extensibility/sccget-function.md)|파일 집합의 읽기 전용 복사본을 검색합니다.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|호출자 (통해)에 `SccQueryInfo`대해 요청 한 파일의 상태를 확인합니다.|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|소스 제어 플러그인을 발생하여 플러그인에 의미 있는 프로젝트 경로를 사용자에게 요청합니다.|
|[SccHistory](../extensibility/scchistory-function.md)|정규화된 로컬 파일 이름 배열에 대한 기록을 표시합니다.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|파일의 현재 상태를 검사합니다. 또한 이 함수를 사용하여 파일이 `pfnPopulate` `nCommand`의 조건과 일치하지 않을 때 호출자에게 알립니다.|
|[SccProperties](../extensibility/sccproperties-function.md)|정규화된 파일의 속성을 표시합니다.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|정규화된 파일 의 현재 상태를 검사합니다.|
|[SccRemove](../extensibility/sccremove-function.md)|소스 제어 시스템에서 정규화된 파일의 배열을 제거합니다.|
|[SccRename](../extensibility/sccrename-function.md)|소스 제어 시스템의 새 이름으로 지정된 파일의 이름을 바꿉니다.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|소스 제어 시스템의 모든 기능에 액세스합니다.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|파일 배열의 체크 아웃을 취소합니다.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>추가 기능을 지원하는 기능(소스 제어 플러그인 API의 버전 1.2)
 이 함수 그룹은 소스 제어 플러그인 API의 버전 1.2에 포함된 추가 기능을 정의합니다. 고급 소스 제어 기능 및 기능에 대한 액세스를 제공합니다.

|함수|설명|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|일괄 처리 작업을 시작합니다.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|기존 상위 프로젝트 아래에 지정된 이름으로 하위 프로젝트를 만듭니다.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|정규화된 경로 이름으로 지정된 로컬 사용자의 디렉터리와 소스 제어 데이터베이스 위치 간의 차이점을 보여 주며|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|정규화된 디렉터리 목록을 검사하여 현재 상태를 검사합니다.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|일괄 처리 작업을 종료합니다.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|지정된 프로젝트의 상위 경로를 반환합니다(프로젝트가 있어야 합니다).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|파일에서 여러 체크 아웃이 허용되는지 여부를 확인합니다.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|플러그인이 MSSCCPRJ를 만들지 여부를 확인합니다. SCC 파일.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>고급 기능을 지원하는 기능(소스 제어 플러그인 API의 버전 1.3)
 이 함수 그룹은 소스 제어 플러그인 API의 버전 1.3에 포함된 추가 기능을 정의합니다. 고급 소스 제어 기능 및 기능에 대한 액세스를 제공합니다.

|함수|설명|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|소스 컨트롤의 파일 목록을 현재 프로젝트에 추가합니다.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|사용자 인터페이스 없이 소스 컨트롤에서 파일 목록을 검색합니다.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|로컬 파일과 다른 소스 컨트롤의 파일 목록을 검색합니다.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|소스 제어 플러그인에서 지원하는 확장 기능을 지정하는 플래그를 검색합니다.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|사용자별 옵션을 검색합니다.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|소스 제어하에 있는 프로젝트 또는 프로젝트의 디렉터리 및 파일 목록을 검사합니다. 발견된 각 디렉터리 및 파일 이름은 콜백 함수에 전달됩니다.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|파일 목록에 대한 이름 변경 내용을 검사합니다. 각 파일 이름은 변경 상태가 있는 콜백 함수에 전달됩니다.|

## <a name="requirements"></a>요구 사항
 헤더: scc.h

 (환경 SDK 공통에 제공 폴더를 포함, 기본적으로 *[드라이브]* \프로그램 파일\VSIP 8.0\EnvSDK\common\inc; 또한 MSSCCI 샘플과 VSIP 폴더에 제공, *[드라이브]* \프로그램 파일\VSIP 8.0\MSSCCI).

## <a name="see-also"></a>참조
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
- [소스 제어 플러그 인 만들기](../extensibility/internals/creating-a-source-control-plug-in.md)
