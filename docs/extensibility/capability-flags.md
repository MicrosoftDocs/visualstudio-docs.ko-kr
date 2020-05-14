---
title: 기능 플래그 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9660cbe5a18e82974858fa4d923a38fc73e773f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739874"
---
# <a name="capability-flags"></a>기능 플래그
SCC_CAP_*xxx* 플래그는 소스 제어 플러그인의 기능을 나타내는 데 사용되는 비트 플래그입니다. SCC_EXCAP_*xxx* 플래그는 확장 된 기능을 나타내고 정수 값으로 확인 하는 증분 플래그입니다.

|기능 코드|값|Description|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|[SccRemove](../extensibility/sccremove-function.md) 및 명령을 지원합니다.|
|`SCC_CAP_RENAME`|0x00000002L|[SccRename](../extensibility/sccrename-function.md) 및 명령을 지원합니다.|
|`SCC_CAP_DIFF`|0x00000004L|[SccDiff](../extensibility/sccdiff-function.md) 및 명령을 지원합니다.|
|`SCC_CAP_HISTORY`|0x00000008L|[SccHistory](../extensibility/scchistory-function.md) 및 명령을 지원합니다.|
|`SCC_CAP_PROPERTIES`|0x00000010L|[SccProperties](../extensibility/sccproperties-function.md) 및 명령을 지원합니다.|
|`SCC_CAP_RUNSCC`|0x000000020L|[SccRunScc](../extensibility/sccrunscc-function.md) 및 명령을 지원합니다.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x000000040L|[SccGetCommand옵션](../extensibility/sccgetcommandoptions-function.md) 및 명령을 지원합니다.|
|`SCC_CAP_QUERYINFO`|0x000000080L|[SccQueryInfo](../extensibility/sccqueryinfo-function.md) 및 명령을 지원합니다.|
|`SCC_CAP_GETEVENTS`|0x000000100L|[SccGetEvents](../extensibility/sccgetevents-function.md) 및 명령을 지원합니다.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|[SccGetProjPath](../extensibility/sccgetprojpath-function.md) 및 명령을 지원합니다.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|[SccAddFromScc](../extensibility/sccaddfromscc-function.md) 및 명령을 지원합니다.|
|`SCC_CAP_COMMENTCHECKOUT`|0x000000800L|체크 아웃에 대한 설명을 지원합니다.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|체크 인에 대한 코멘트를 지원합니다.|
|`SCC_CAP_COMMENTADD`|0x00002000L|추가에 대한 주석을 지원합니다.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|제거에 대한 주석을 지원합니다.|
|`SCC_CAP_TEXTOUT`|0x00008000L|IDE가 제공하는 출력 함수에 텍스트를 씁니다.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|델타없이 파일 저장을 지원합니다.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|여러 파일 기록을 지원합니다.|
|`SCC_CAP_IGNORECASE`|0x00800000L|대/소문자를 구분하지 않음 파일 비교를 지원합니다.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|공백을 무시하는 파일 비교를 지원합니다.|
|`SCC_CAP_POPULATELIST`|0x02000000L|추가 파일 찾기를 지원합니다.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|프로젝트 만들기에 대한 주석을 지원합니다.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|제어 하에 있는 경우 모든 상태에서 diff를 지원합니다.|
|`SCC_CAP_GET_NOUI`|0x20000000L|플러그인은 Get에 대한 UI를 지원하지 않지만 IDE는 여전히 [SccGet](../extensibility/sccget-function.md)을 호출할 수 있습니다.|
|`SCC_CAP_REENTRANT`|0x40000000L|플러그인은 재진입 및 스레드 로 안전합니다. 버전 1.0에서는 재진입 및 스레드 안전으로 가정된 플러그인이 없습니다. 1.1 플러그인이 이 비트를 설정하면 호스트가 여러 프로젝트를 병렬로 열 수 있습니다.|

## <a name="capability-bits-added-in-version-12"></a>버전 1.2에 추가된 기능 비트

|기능 코드|값|Description|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)를 지원합니다.|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|[SccGetParent프로젝트패스](../extensibility/sccgetparentprojectpath-function.md)를 지원합니다.|
|`SCC_CAP_BATCH`|0x00040000L|[SccBeginBatch](../extensibility/sccbeginbatch-function.md) 및 [SccEndBatch를](../extensibility/sccendbatch-function.md)지원합니다.|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|[SccDirQueryInfo를](../extensibility/sccdirqueryinfo-function.md)지원합니다.|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|[SccDirDiff를](../extensibility/sccdirdiff-function.md)지원합니다.|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|파일 및 [SccIsMultiCheckoutEnabled에서](../extensibility/sccismulticheckoutenabled-function.md)여러 체크 아웃을 지원합니다.|
|`SCC_CAP_SCCFILE`|0x80000000L|*MSSCCPRJ.SCC* 파일(사용자/관리자 재정의 대상)과 [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)을 지원합니다.|

## <a name="capability-bits-added-in-version-13"></a>버전 1.3에 추가된 기능 비트
 이러한 플래그는 [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) 함수에 한 번에 하나씩 전달되어 기능이 지원되는지 여부를 확인합니다.

|확장 기능 코드|값|Description|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|`SCC_CHECKOUT_LOCALVER` 체크 아웃 옵션을 지원합니다.|
|`SCC_EXCAP_BACKGROUND_GET`|2|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)을 지원합니다.|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|[SccEnum변경 파일](../extensibility/sccenumchangedfiles-function.md)지원 .|
|`SCC_EXCAP_POPULATELIST_DIR`|4|추가 디렉터리 찾기를 지원합니다.|
|`SCC_EXCAP_QUERYCHANGES`|5|파일 변경 내용 을 등록합니다.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|[SccAddFilesFromSCC를](../extensibility/sccaddfilesfromscc-function.md)지원합니다.|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|[SccGetUser 옵션을](../extensibility/sccgetuseroption-function.md)지원합니다.|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|여러 스레드에서 SccQueryInfo 호출을 지원합니다.|
|`SCC_EXCAP_REMOVE_DIR`|9|SccRemoveDir 기능을 지원합니다.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|체크 아웃된 파일을 삭제할 수 있습니다.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|체크 아웃된 파일의 이름을 바꿀 수 있습니다.|

## <a name="see-also"></a>참조
- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md)
