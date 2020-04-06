---
title: 스크런스cc 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d012908e59be8b82e34ff68cdab1945c5bd2de8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700402"
---
# <a name="sccrunscc-function"></a>SccRunScc 함수
이 함수는 소스 제어 관리 도구를 호출합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 n파일

【인】 배열에 지정된 파일 `lpFileNames` 수입니다.

 lpFile 이름

【인】 선택한 파일 이름의 배열입니다.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|소스 제어 관리 도구가 성공적으로 호출되었습니다.|
|SCC_I_OPERATIONCANCELED|작업이 취소되었습니다.|
|SCC_E_INITIALIZEFAILED|소스 제어 시스템을 초기화하지 못했습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다.|
|SCC_E_CONNECTIONFAILURE|소스 제어 시스템에 연결하지 못했습니다.|
|SCC_E_FILENOTCONTROLLED|선택한 파일이 소스 제어하에 있지 않습니다.|
|SCC_E_NONSPECIFICERROR|비특정 오류입니다.|

## <a name="remarks"></a>설명
 이 기능을 사용하면 호출자가 외부 관리 도구를 통해 소스 제어 시스템의 모든 기능에 액세스할 수 있습니다. 소스 제어 시스템에 사용자 인터페이스가 없는 경우 소스 제어 플러그인은 필요한 관리 기능을 수행하는 인터페이스를 구현할 수 있습니다.

 이 함수는 현재 선택된 파일에 대한 개수 및 파일 이름 배열로 호출됩니다. 관리 도구가 지원하는 경우 파일 목록을 사용하여 관리 인터페이스에서 파일을 미리 선택할 수 있습니다. 그렇지 않으면 목록을 무시할 수 있습니다.

 이 함수는 일반적으로 사용자가 **파일** -> 소스 제어**메뉴에서** **>\<시작 소스 제어 서버를** 선택할 때 호출됩니다. 이 **시작** 메뉴 옵션은 레지스트리 항목을 설정하여 항상 비활성화하거나 숨길 수 있습니다. 방법: 자세한 내용은 [소스 제어 플러그인을 설치합니다.](../extensibility/internals/how-to-install-a-source-control-plug-in.md) 이 함수는 [SccInitialize가](../extensibility/sccinitialize-function.md) 기능 `SCC_CAP_RUNSCC` 비트를 반환하는 경우에만 호출됩니다(이 기능 및 기타 기능 비트에 대한 자세한 내용은 [기능 플래그](../extensibility/capability-flags.md) 참조).

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [방법: 소스 제어 플러그 인 설치](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [기능 플래그](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
