---
title: 특정 명령에 사용 되는 bitflags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa1fd8bf025d665977e87dc8b88da724ade5a8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740017"
---
# <a name="bitflags-used-by-specific-commands"></a>특정 명령에 사용 되는 bitflags
하나 이상의 비트를 단일 값으로 설정 하 여 소스 제어 플러그 인 API에서 여러 함수의 동작을 수정할 수 있습니다. 이러한 값을 bitflags 라고 합니다. 소스 제어 플러그 인 API에서 사용 하는 다양 한 bitflag는 여기에서 자세히 설명 하며이를 사용 하는 함수 별로 그룹화 되어 있습니다.

## <a name="checked-out-flag"></a>체크 아웃 된 플래그
 이 플래그는 [Sccadd](../extensibility/sccadd-function.md) 또는 [sccadd](../extensibility/scccheckin-function.md)에 대해 설정할 수 있습니다.

|플래그|값|설명|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|파일을 체크 아웃 된 상태로 유지 합니다.|

## <a name="add-flags"></a>플래그 추가
 이러한 플래그는 [Sccadd](../extensibility/sccadd-function.md)에서 사용 됩니다.

|플래그|값|설명|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|소스 제어 플러그 인은 파일이 텍스트 인지 아니면 이진 인지를 자동으로 감지 합니다.|
|`SCC_FILETYPE_TEXT`|0x01|파일 형식이 텍스트입니다.|
|`SCC_FILETYPE_BINARY`|0x04|이진 파일 유형입니다. **참고:** `SCC_FILETYPE_TEXT` 및 `SCC_FILETYPE_BINARY` 플래그는 함께 사용할 수 없습니다.   정확히 하나 또는 모두를 설정 하지 않습니다.|
|`SCC_ADD_STORELATEST`|0x02|최신 버전 (델타 없음)만 저장 합니다.|

## <a name="diff-flags"></a>Diff 플래그
 [Sccdiff](../extensibility/sccdiff-function.md) 는 이러한 플래그를 사용 하 여 diff 작업의 범위를 정의 합니다. `SCC_DIFF_QD_xxx`플래그는 함께 사용할 수 없습니다. 이러한 항목 중 하나를 지정 하면 시각적 피드백이 제공 되지 않습니다. "빠른 diff" (QD)에서 플러그 인은 파일이 서로 다른 방법을 결정 하지 않습니다. 이러한 플래그가 지정 되어 있지 않으면 "시각적 diff"가 수행 됩니다. 자세한 파일 차이를 계산 하 고 표시 합니다. 요청 된 QD가 지원 되지 않는 경우 플러그 인은 다음으로 가장 적합 한 항목으로 이동 합니다. 예를 들어 IDE에서 체크섬을 요청 하 고 플러그 인에서이를 지원 하지 않으면 플러그 인에서 전체 콘텐츠 검사를 수행 합니다 (시각적 표시 보다 훨씬 더 빠름).

|플래그|값|설명|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|대/소문자 차이를 무시 합니다.|
|`SCC_DIFF_IGNORESPACE`|0x0004|공백 차이를 무시 합니다. **참고:**  `SCC_DIFF_IGNORECASE` 및 `SCC_DIFF_IGNORESPACE` 플래그는 선택적 bitflags입니다.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD는 전체 파일 내용을 비교 합니다.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|체크섬 별 QD.|
|`SCC_DIFF_QD_TIME`|0x0040|파일 날짜/시간 스탬프로 QD|
|`SCC_DIFF_QUICK_DIFF`|0x0070|모든 QD bitflags를 확인 하는 데 사용 되는 마스크입니다. 함수에 전달 하면 안 됩니다. 세 개의 qd bitflag는 함께 사용할 수 없습니다. QD는 항상 UI가 표시 되지 않음을 의미 합니다.|

## <a name="populatelist-flag"></a>PopulateList 플래그
 이 플래그는 매개 변수의 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 에서 사용 됩니다 `fOptions` .

|플래그|값|설명|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|IDE에서 파일이 아니라 디렉터리를 전달 합니다.|

## <a name="populatedirlist-flags"></a>PopulateDirList 플래그
 이러한 플래그는 매개 변수의 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 에서 사용 됩니다 `fOptions` .

|옵션 값|값|설명|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|디렉터리에 대 한 디렉터리의 한 수준 (기본값)만 검사 합니다.|
|SCC_PDL_RECURSIVE|0x0001|지정 된 각 디렉터리의 모든 디렉터리를 재귀적으로 검사 합니다.|
|SCC_PDL_INCLUDEFILES|0x0002|검사 프로세스에 파일 이름을 포함 합니다.|

## <a name="openproject-flags"></a>OpenProject 플래그
 이러한 플래그는 매개 변수의 [Sccopenproject](../extensibility/sccopenproject-function.md) 에서 사용 됩니다 `dwFlags` .

|옵션 값|값|설명|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|프로젝트가 소스 제어에 없는 경우 새로 만듭니다. 이 플래그를 설정 하지 않으면 사용자에 게 프로젝트를 만들라는 메시지를 표시 `SCC_OP_SILENTOPEN` 합니다 (플래그가 지정 되지 않은 경우).|
|SCC_OP_SILENTOPEN|0x00000002L|사용자에 게 프로젝트를 만들지 묻는 메시지를 표시 하지 않습니다. 만 반환 `SCC_E_UNKNOWNPROJECT` 합니다.|

## <a name="get-flags"></a>플래그 가져오기
 이러한 플래그는 [Sccget](../extensibility/sccget-function.md) 및 [sccget](../extensibility/scccheckout-function.md)에서 사용 됩니다.

|플래그|값|설명|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|IDE는 파일이 아니라 디렉터리를 전달 합니다 .이 디렉터리의 모든 파일을 가져옵니다.|
|`SCC_GET_RECURSIVE`|0x00000002L|IDE는 디렉터리를 전달 합니다. 이러한 디렉터리와 모든 하위 디렉터리를 가져옵니다.|

## <a name="noption-values"></a>nOption 값
 이러한 플래그는 [Sccsetoption](../extensibility/sccsetoption-function.md) 에서 매개 변수에 사용 됩니다 `nOption` .

|플래그|값|설명|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|이벤트 큐의 상태를 설정 합니다.|
|`SCC_OPT_USERDATA`|0x00000002L|에 대 한 사용자 데이터를 지정 `SCC_OPT_NAMECHANGEPFN` 합니다.|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE는 취소를 처리할 수 있습니다.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|이름 변경에 대 한 콜백을 설정 합니다.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|소스 제어 플러그 인 UI 체크 아웃을 사용 하지 않도록 설정 하 고 작업 디렉터리를 설정 하지 않습니다.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|작업 디렉터리를 지정 하기 위해 소스 제어 시스템에서 추가 합니다. 직계 하위 항목인 경우 연결 된 프로젝트로 공유 해 보세요.|

## <a name="dwval-bitflags"></a>dwval bitflag
 이러한 플래그는 [Sccsetoption](../extensibility/sccsetoption-function.md) 에서 매개 변수에 사용 됩니다 `dwVal` .

|플래그|값|설명|값으로 사용 `nOption`|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|이벤트 큐 작업을 일시 중단 합니다.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|이벤트 큐 로깅을 사용 합니다.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|기본 에는 취소 모드가 없습니다. 필요한 경우 플러그 인에서 제공 해야 합니다.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|IDE는 취소를 처리 합니다.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|기본 플러그 인 UI를 체크 아웃 하는 확인 작업 디렉터리가 설정 되었습니다.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|플러그 인 UI를 체크 아웃 하지 않고 작업 디렉터리가 없습니다.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>참조
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
