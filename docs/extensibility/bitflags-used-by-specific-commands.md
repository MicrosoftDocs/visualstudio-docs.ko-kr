---
title: 특정 명령에서 사용하는 비트 플래그 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740017"
---
# <a name="bitflags-used-by-specific-commands"></a>특정 명령에서 사용되는 비트 플래그
소스 제어 플러그인 API에서 하나 이상의 비트를 단일 값으로 설정하여 여러 함수의 동작을 수정할 수 있습니다. 이러한 값을 비트 플래그라고 합니다. 소스 제어 플러그인 API에서 사용하는 다양한 비트 플래그는 여기에 자세히 설명되어 있으며 이를 사용하는 함수별로 그룹화되어 있습니다.

## <a name="checked-out-flag"></a>체크 아웃플래그
 이 플래그는 [SccAdd](../extensibility/sccadd-function.md) 또는 [SccCheckin](../extensibility/scccheckin-function.md)에 대해 설정할 수 있습니다.

|플래그|값|Description|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|파일을 체크 아웃된 상태로 유지합니다.|

## <a name="add-flags"></a>플래그 추가
 이러한 플래그는 [SccAdd에서](../extensibility/sccadd-function.md)사용됩니다.

|플래그|값|Description|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|소스 제어 플러그인은 파일이 텍스트인지 바이너리인지 자동으로 감지할 것으로 예상됩니다.|
|`SCC_FILETYPE_TEXT`|0x01|파일 형식은 텍스트입니다.|
|`SCC_FILETYPE_BINARY`|0x04|파일 형식은 바이너리입니다. **참고:** `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` 플래그는 상호 배타적입니다.   정확히 하나 또는 둘 다 설정합니다.|
|`SCC_ADD_STORELATEST`|0x02|최신 버전만 저장합니다(델타 없음).|

## <a name="diff-flags"></a>Diff 플래그
 [SccDiff는](../extensibility/sccdiff-function.md) 이러한 플래그를 사용하여 diff 작업의 범위를 정의합니다. 플래그는 `SCC_DIFF_QD_xxx` 상호 배타적입니다. 그 중 하나를 지정하면 시각적 피드백이 제공되지 않습니다. "빠른 diff"(QD)에서 플러그인은 파일이 다른 경우에만 파일이 어떻게 다른지 결정하지 않습니다. 이러한 플래그가 지정되지 않으면 "시각적 diff"가 수행됩니다. 자세한 파일 차이를 계산하고 표시됩니다. 요청된 QD가 지원되지 않으면 플러그인이 다음 최상의 QD로 이동합니다. 예를 들어 IDE가 체크섬을 요청하고 플러그인이 이를 지원하지 않는 경우 플러그인은 전체 콘텐츠 검사를 수행합니다(시각적 표시보다 여전히 훨씬 빠름).

|플래그|값|Description|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|대/소문자 차이를 무시합니다.|
|`SCC_DIFF_IGNORESPACE`|0x0004|공백 차이를 무시합니다. **참고:**  `SCC_DIFF_IGNORECASE` 및 `SCC_DIFF_IGNORESPACE` 플래그는 선택적 비트 플래그입니다.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|전체 파일 내용을 비교하여 QD.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD로 체크섬.|
|`SCC_DIFF_QD_TIME`|0x0040|파일 날짜/시간 스탬프별 QD.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|이것은 모든 QD 비트 플래그를 확인하는 데 사용되는 마스크입니다. 함수로 전달해서는 안 됩니다. 세 개의 QD 비트 플래그는 상호 배타적입니다. QD는 항상 UI가 표시되지 않는다는 것을 의미합니다.|

## <a name="populatelist-flag"></a>채우기목록 플래그
 이 플래그는 `fOptions` 매개 변수의 [SccPopulateList에서](../extensibility/sccpopulatelist-function.md) 사용됩니다.

|플래그|값|Description|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|IDE는 파일이 아닌 디렉터리를 전달합니다.|

## <a name="populatedirlist-flags"></a>채우기DirList 플래그
 이러한 플래그는 `fOptions` 매개 변수의 [SccPopulateDirList에서](../extensibility/sccpopulatedirlist-function.md) 사용됩니다.

|옵션 값|값|Description|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|디렉터리에 대한 디렉터리 수준을 한 수준만 검사합니다(기본값입니다).|
|SCC_PDL_RECURSIVE|0x0001|지정된 각 디렉터리 아래에 있는 모든 디렉터리를 재귀적으로 검사합니다.|
|SCC_PDL_INCLUDEFILES|0x0002|검사 프로세스에 파일 이름을 포함합니다.|

## <a name="openproject-flags"></a>오픈 프로젝트 플래그
 이러한 플래그는 `dwFlags` 매개 변수의 [SccOpenProject에서](../extensibility/sccopenproject-function.md) 사용됩니다.

|옵션 값|값|Description|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|프로젝트가 소스 컨트롤에 없는 경우 프로젝트를 만듭니다. 이 플래그가 설정되지 않은 경우 플래그가 `SCC_OP_SILENTOPEN` 지정되지 않은 경우 프로젝트를 만들라는 메시지를 사용자에게 표시합니다.|
|SCC_OP_SILENTOPEN|0x00000002L|사용자에게 프로젝트를 만들라는 메시지를 표시하지 마십시오. 그냥 `SCC_E_UNKNOWNPROJECT`반환합니다.|

## <a name="get-flags"></a>깃발 받기
 이러한 플래그는 [SccGet](../extensibility/sccget-function.md) 및 [SccCheckout에서](../extensibility/scccheckout-function.md)사용됩니다.

|플래그|값|Description|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|IDE는 파일이 아닌 디렉토리를 전달합니다: 이러한 디렉토리의 모든 파일 가져옵니다.|
|`SCC_GET_RECURSIVE`|0x00000002L|IDE는 디렉토리를 전달합니다: 이러한 디렉터리와 모든 하위 디렉토리를 가져옵니다.|

## <a name="noption-values"></a>n옵션 값
 이러한 플래그는 `nOption` 매개 변수의 [SccSetOption에서](../extensibility/sccsetoption-function.md) 사용됩니다.

|플래그|값|Description|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|이벤트 큐의 상태를 설정합니다.|
|`SCC_OPT_USERDATA`|0x00000002L|에 대한 `SCC_OPT_NAMECHANGEPFN`사용자 데이터 지정|
|`SCC_OPT_HASCANCELMODE`|0x000000003L|IDE는 취소를 처리할 수 있습니다.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|이름 변경에 대한 콜백을 설정합니다.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x0000000005L|소스 제어 플러그인 UI 체크 아웃을 사용하지 않도록 설정하고 작업 디렉토리를 설정하지 않습니다.|
|`SCC_OPT_SHARESUBPROJ`|0x000000006L|원본 제어 시스템에서 추가하여 작업 디렉토리를 지정합니다. 직접 하위 항목인 경우 연결된 프로젝트에 공유해 보십시오.|

## <a name="dwval-bitflags"></a>dwVal 비트 플래그
 이러한 플래그는 `dwVal` 매개 변수의 [SccSetOption에서](../extensibility/sccsetoption-function.md) 사용됩니다.

|플래그|값|Description|값으로 `nOption` 사용|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|이벤트 큐 활동을 일시 중단합니다.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|이벤트 큐 로깅을 활성화합니다.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(기본값) 취소 모드가 없습니다. 원하는 경우 플러그 인을 공급해야 합니다.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|IDE 핸들은 취소됩니다.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(기본값) 플러그인 UI에서 체크 아웃 확인; 작업 디렉토리가 설정됩니다.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|플러그인 UI 체크 아웃, 작업 디렉토리 가 없습니다.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>참조
- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md)
