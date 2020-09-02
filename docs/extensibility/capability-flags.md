---
title: 기능 플래그 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739874"
---
# <a name="capability-flags"></a>기능 플래그
SCC_CAP_*xxx* 플래그는 소스 제어 플러그 인의 기능을 나타내는 데 사용 되는 비트 플래그입니다. SCC_EXCAP_*xxx* 플래그는 확장 기능을 나타내고 정수 값을 확인 하는 증분 플래그입니다.

|기능 코드|값|설명|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|[Sccremove](../extensibility/sccremove-function.md) 및 명령을 지원 합니다.|
|`SCC_CAP_RENAME`|0x00000002L|[Sccrename](../extensibility/sccrename-function.md) 및 명령을 지원 합니다.|
|`SCC_CAP_DIFF`|0x00000004L|[Sccdiff](../extensibility/sccdiff-function.md) 및 명령을 지원 합니다.|
|`SCC_CAP_HISTORY`|0x00000008L|는 [Scchistory](../extensibility/scchistory-function.md) 및 명령을 지원 합니다.|
|`SCC_CAP_PROPERTIES`|0x00000010L|[Sccproperties](../extensibility/sccproperties-function.md) 및 명령을 지원 합니다.|
|`SCC_CAP_RUNSCC`|0x00000020L|[SccRunScc](../extensibility/sccrunscc-function.md) 및 명령을 지원 합니다.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 및 명령을 지원 합니다.|
|`SCC_CAP_QUERYINFO`|0x00000080L|[Sccqueryinfo](../extensibility/sccqueryinfo-function.md) 및 명령을 지원 합니다.|
|`SCC_CAP_GETEVENTS`|0x00000100L|[Sccgetevents](../extensibility/sccgetevents-function.md) 및 명령을 지원 합니다.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|[SccGetProjPath](../extensibility/sccgetprojpath-function.md) 및 명령을 지원 합니다.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|[SccAddFromScc](../extensibility/sccaddfromscc-function.md) 및 명령을 지원 합니다.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|체크 아웃 시 설명을 지원 합니다.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|체크 인에 대 한 설명을 지원 합니다.|
|`SCC_CAP_COMMENTADD`|0x00002000L|추가에 대 한 설명을 지원 합니다.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|제거에 대 한 설명을 지원 합니다.|
|`SCC_CAP_TEXTOUT`|0x00008000L|IDE 제공 출력 함수에 텍스트를 씁니다.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|에서는 델타 없이 파일을 저장할 수 있습니다.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|에서는 여러 파일 기록을 지원 합니다.|
|`SCC_CAP_IGNORECASE`|0x00800000L|대/소문자를 구분 하지 않는 파일 비교를 지원 합니다.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|공백을 무시 하는 파일 비교를 지원 합니다.|
|`SCC_CAP_POPULATELIST`|0x02000000L|추가 파일 찾기를 지원 합니다.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|프로젝트 만들기에 대 한 주석을 지원 합니다.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|컨트롤에서 모든 상태에 대 한 diff를 지원 합니다.|
|`SCC_CAP_GET_NOUI`|0x20000000L|플러그 인은 Get을 위한 UI를 지원 하지 않지만 IDE는 [Sccget](../extensibility/sccget-function.md)을 계속 호출할 수 있습니다.|
|`SCC_CAP_REENTRANT`|0x40000000L|플러그 인은 재진입 및 스레드로부터 안전 합니다. 버전 1.0에서 플러그 인은 재진입 및 스레드로부터 안전 하 게 간주 되지 않습니다. 1.1 플러그 인이이 비트를 설정 하면 호스트에서 여러 프로젝트를 병렬로 열 수 있습니다.|

## <a name="capability-bits-added-in-version-12"></a>버전 1.2에 추가 된 기능 비트

|기능 코드|값|설명|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)을 지원 합니다.|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)을 지원 합니다.|
|`SCC_CAP_BATCH`|0x00040000L|[Sccbeginbatch](../extensibility/sccbeginbatch-function.md) 및 [sccbeginbatch](../extensibility/sccendbatch-function.md)를 지원 합니다.|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|[Sccdirqueryinfo](../extensibility/sccdirqueryinfo-function.md)를 지원 합니다.|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|는 [Sccdirdiff](../extensibility/sccdirdiff-function.md)를 지원 합니다.|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|는 파일 및 [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)여러 체크 아웃을 지원 합니다.|
|`SCC_CAP_SCCFILE`|0x80000000L|*Mssccprj.scc* 파일 (사용자/관리자 재정의에 따라) 및 [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)를 지원 합니다.|

## <a name="capability-bits-added-in-version-13"></a>버전 1.3에 추가 된 기능 비트
 이러한 플래그는 기능이 지원 되는지 여부를 확인 하기 위해 [Sccgetextendedcapabilities](../extensibility/sccgetextendedcapabilities-function.md) 함수에 한 번에 하나씩 전달 됩니다.

|확장 된 기능 코드|값|설명|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|는 `SCC_CHECKOUT_LOCALVER` 체크 아웃에 대 한 옵션을 지원 합니다.|
|`SCC_EXCAP_BACKGROUND_GET`|2|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)을 지원 합니다.|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|[Sccenumchangedfiles](../extensibility/sccenumchangedfiles-function.md)를 지원 합니다.|
|`SCC_EXCAP_POPULATELIST_DIR`|4|추가 디렉터리 찾기를 지원 합니다.|
|`SCC_EXCAP_QUERYCHANGES`|5|파일 변경 내용 열거를 지원 합니다.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|[Sccaddfilesfromscc](../extensibility/sccaddfilesfromscc-function.md)를 지원 합니다.|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)을 지원 합니다.|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|에서는 여러 스레드에서 SccQueryInfo를 호출할 수 있습니다.|
|`SCC_EXCAP_REMOVE_DIR`|9|는 SccRemoveDir 함수를 지원 합니다.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|체크 아웃 한 파일을 삭제할 수 있습니다.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|체크 아웃 된 파일의 이름을 바꿀 수 있습니다.|

## <a name="see-also"></a>참조
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
