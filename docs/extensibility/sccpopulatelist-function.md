---
description: 이 함수는 특정 소스 제어 명령에 대한 파일 목록을 업데이트하고 지정된 모든 파일에 소스 제어 상태를 제공합니다.
title: SccPopulateList 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b386c576b48e14b6118f62d451c42ac20f048b45
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902347"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList 함수
이 함수는 특정 소스 제어 명령에 대한 파일 목록을 업데이트하고 지정된 모든 파일에 소스 제어 상태를 제공합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccPopulateList (
   LPVOID          pvContext,
   enum SCCCOMMAND nCommand,
   LONG            nFiles,
   LPCSTR*         lpFileNames,
   POPLISTFUNC     pfnPopulate,
   LPVOID          pvCallerData,
   LPLONG          lpStatus,
   LONG            fOptions
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

[in] 소스 제어 플러그 인 컨텍스트 구조입니다.

 nCommand

[in] 배열의 모든 파일에 적용할 소스 제어 `lpFileNames` 명령입니다(가능한 명령 목록은 [명령 코드](../extensibility/command-code-enumerator.md) 참조).

 nFiles

[in] 배열의 파일 `lpFileNames` 수입니다.

 lpFileNames

[in] IDE에 알려진 파일 이름의 배열입니다.

 pfnPopulate

[in] 파일을 추가 및 제거하기 위해 호출할 IDE 콜백 함수입니다(자세한 내용은 [POPLISTFUNC](../extensibility/poplistfunc.md) 참조).

 pvCallerData

[in] 콜백 함수에 변경되지 않고 전달할 값입니다.

 lpStatus

[in, out] 각 파일에 대한 상태 플래그를 반환하는 소스 제어 플러그 인의 배열입니다.

 fOptions

[in] 명령 플래그(자세한 내용은 [특정 명령에서 사용되는 Bitflags의](../extensibility/bitflags-used-by-specific-commands.md) "PopulateList 플래그" 섹션 참조).

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|성공.|
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류입니다.|

## <a name="remarks"></a>설명
 이 함수는 파일 목록에서 현재 상태를 검사합니다. `pfnPopulate`이 함수는 콜백 함수를 사용하여 파일이 의 조건과 일치하지 않을 때 호출자에게 알립니다. `nCommand` 예를 들어 명령이 `SCC_COMMAND_CHECKIN` 이고 목록의 파일이 체크 아웃되지 않은 경우 콜백을 사용하여 호출자에게 알릴 수 있습니다. 경우에 따라 소스 제어 플러그 인은 명령의 일부일 수 있는 다른 파일을 찾아서 추가할 수 있습니다. 예를 들어 Visual Basic 사용자가 프로젝트에서 사용하지만 Visual Basic 프로젝트 파일에 표시되지 않는 .bmp 파일을 체크 아웃할 수 있습니다. 사용자가 IDE에서 **Get** 명령을 선택합니다. IDE는 사용자가 얻을 수 있다고 생각하는 모든 파일의 목록을 표시하지만, 목록이 `SccPopulateList` 표시되기 전에 함수가 호출되어 표시할 목록이 최신인지 확인합니다.

## <a name="example"></a>예제
 IDE는 사용자가 얻을 수 있다고 생각하는 파일 목록을 작성합니다. 이 목록을 표시하기 전에 함수를 호출하여 `SccPopulateList` 소스 제어 플러그 인에 목록에서 파일을 추가하고 삭제할 수 있는 기회를 제공합니다. 플러그 인은 지정된 콜백 함수를 호출하여 목록을 수정합니다(자세한 내용은 [POPLISTFUNC](../extensibility/poplistfunc.md) 참조).

 플러그 인은 작업이 `pfnPopulate` 완료된 다음 함수에서 반환될 때까지 파일을 추가 및 삭제하는 함수를 계속 `SccPopulateList` 호출합니다. 그러면 IDE에서 해당 목록을 표시할 수 있습니다. `lpStatus`배열은 IDE에서 전달한 원래 목록의 모든 파일을 나타냅니다. 플러그 인은 콜백 함수를 사용하는 것 외에도 이러한 모든 파일의 상태를 채웁니다.

> [!NOTE]
> 소스 제어 플러그 인에는 항상 목록을 그대로 두고 이 함수에서 즉시 반환하는 옵션이 있습니다. 플러그 인이 이 함수를 구현하는 경우 `SCC_CAP_POPULATELIST` [SccInitialize](../extensibility/sccinitialize-function.md)에 대한 첫 번째 호출에서 기능 비트 플래그를 설정하여 이를 나타낼 수 있습니다. 기본적으로 플러그 인은 항상 전달되는 모든 항목이 파일이라고 가정해야 합니다. 그러나 IDE가 매개 변수에 플래그를 설정하는 경우 `SCC_PL_DIR` `fOptions` 전달되는 모든 항목은 디렉터리로 간주됩니다. 플러그 인은 디렉터리에 속한 모든 파일을 추가해야 합니다. IDE는 파일과 디렉터리를 혼합하여 전달하지 않습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [특정 명령에 사용되는 Bitflag](../extensibility/bitflags-used-by-specific-commands.md)
- [명령 코드](../extensibility/command-code-enumerator.md)
