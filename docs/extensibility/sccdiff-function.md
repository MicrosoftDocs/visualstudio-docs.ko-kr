---
description: 이 함수는 현재 파일(로컬 디스크)과 소스 제어 시스템의 마지막 체크 인 버전 간의 차이점을 표시하거나 선택적으로 확인합니다.
title: SccDiff 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 484d8b5e988ede9b50099e3c0376f2c3afce8317
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904658"
---
# <a name="sccdiff-function"></a>SccDiff 함수
이 함수는 현재 파일(로컬 디스크)과 소스 제어 시스템의 마지막 체크 인 버전 간의 차이점을 표시하거나 선택적으로 확인합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>매개 변수
 pvContext

[in] 소스 제어 플러그 인 컨텍스트 구조입니다.

 Hwnd

[in] 소스 제어 플러그 인이 제공하는 모든 대화 상자의 부모로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 lpFileName

[in] 차이점이 요청된 파일 이름입니다.

 fOptions

[in] 명령 플래그입니다. 자세한 내용은 설명을 참조하세요.

 pvOptions

[in] 소스 제어 플러그 인 관련 옵션입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|작업 복사본과 서버 버전은 동일합니다.|
|SCC_I_FILESDIFFERS|작업 복사본은 소스 제어의 버전과 다릅니다.|
|SCC_I_RELOADFILE|파일 또는 프로젝트를 다시 로드해야 합니다.|
|SCC_E_FILENOTCONTROLLED|파일이 소스 제어에 있지 않습니다.|
|SCC_E_NOTAUTHORIZED|사용자가 이 작업을 수행할 수 없습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도 하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류; 파일 차이를 가져오지 못했습니다.|
|SCC_E_FILENOTEXIST|로컬 파일을 찾을 수 없습니다.|

## <a name="remarks"></a>설명
 이 함수는 두 가지 용도로 사용됩니다. 기본적으로 파일에 대한 변경 내용 목록이 표시됩니다. 소스 제어 플러그 인은 선택한 형식에 관계없이 자체 창을 열어 디스크의 사용자 파일과 소스 제어에 있는 파일의 최신 버전 간의 차이점을 표시합니다.

 또는 IDE는 파일이 변경되었는지 여부를 결정하기만 하면 될 수 있습니다. 예를 들어 IDE는 사용자에게 알리지 않고 파일을 체크 아웃해도 안전한지 확인해야 할 수 있습니다. 이 경우 IDE는 `SCC_DIFF_CONTENTS` 플래그를 전달합니다. 소스 제어 플러그 인은 소스 제어 파일에 대해 디스크의 파일(바이트 바이트)을 확인하고 사용자에게 아무것도 표시하지 않고 두 파일이 다른지 여부를 나타내는 값을 반환해야 합니다.

 성능 최적화를 위해 소스 제어 플러그 인은 에서 호출하는 바이트별 비교 대신 체크섬 또는 타임스탬프를 기반으로 하는 대안을 사용할 수 있습니다. `SCC_DIFF_CONTENTS` 이러한 형식의 비교는 분명히 더 빠르지만 안정성이 떨어집니다. 모든 소스 제어 시스템에서 이러한 대체 비교 방법을 지원할 수 있는 것은 아니며 플러그 인은 콘텐츠 비교로 대체해야 할 수 있습니다. 모든 소스 제어 플러그 인은 최소한 콘텐츠 비교를 지원해야 합니다.

> [!NOTE]
> 빠른 차이 플래그는 함께 사용할 수 없습니다. 플래그를 전달하지 않는 것은 유효하지만 동시에 두 개 이상의 플래그를 전달하는 것은 유효하지 않습니다. `SCC_DIFF_QUICK_DIFF`모든 플래그를 결합하는 마스크인 는 테스트에 사용할 수 있지만 매개 변수로 전달되면 안 됩니다.

|`fOption`|의미|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|대/소문자를 구분하지 않는 비교(빠른 차이 또는 시각적 차이에 사용할 수 있음).|
|SCC_DIFF_IGNORESPACE|공백을 무시합니다(빠른 차이 또는 시각적 차이에 사용할 수 있음).|
|SCC_DIFF_QD_CONTENTS|파일 바이트 바이트를 자동으로 비교합니다.|
|SCC_DIFF_QD_CHECKSUM|지원되는 경우 체크섬을 통해 파일을 자동으로 비교합니다. 지원되지 않는 경우 콘텐츠 비교로 돌아갑니다.|
|SCC_DIFF_QD_TIME|지원되는 경우 해당 타임스탬프를 통해 파일을 자동으로 비교합니다. 지원되지 않는 경우 콘텐츠 비교로 돌아갑니다.|

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
