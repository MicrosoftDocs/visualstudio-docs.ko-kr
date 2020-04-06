---
title: SccPopulateList 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f518413adba1546bcff4f7cf2e62b4563cf1bcc7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700526"
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

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 n 명령

【인】 배열의 모든 파일에 적용할 소스 제어 명령입니다(가능한 명령 목록은 명령 코드 참조). [Command Code](../extensibility/command-code-enumerator.md) `lpFileNames`

 n파일

【인】 배열의 파일 `lpFileNames` 수입니다.

 lpFile 이름

【인】 IDE에 알려진 파일 이름 의 배열입니다.

 pfnPopulate

【인】 파일을 추가하고 제거하기 위해 호출할 IDE 콜백 함수(자세한 내용은 [POPLISTFUNC](../extensibility/poplistfunc.md) 참조).

 pvCallerData

【인】 콜백 함수에 변경되지 않고 전달될 값입니다.

 lpStatus

【인, 아웃】 각 파일에 대한 상태 플래그를 반환하는 소스 제어 플러그인에 대한 배열입니다.

 f옵션

【인】 명령 플래그(자세한 내용은 [특정 명령에서 사용하는 비트 플래그의](../extensibility/bitflags-used-by-specific-commands.md) "채우기 목록 플래그" 섹션을 참조하십시오).

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|성공했습니다.|
|SCC_E_NONSPECIFICERROR|비특정 오류입니다.|

## <a name="remarks"></a>설명
 이 함수는 현재 상태에 대한 파일 목록을 검사합니다. 파일이 `pfnPopulate` `nCommand`의 조건과 일치하지 않을 때 호출자에게 알리기 위해 콜백 함수를 사용합니다. 예를 들어 명령이 `SCC_COMMAND_CHECKIN` 있고 목록의 파일이 체크 아웃되지 않은 경우 콜백이 호출자에게 알리는 데 사용됩니다. 경우에 따라 소스 제어 플러그인명령의 일부가 될 수 있는 다른 파일을 찾아 추가할 수 있습니다. 예를 들어 Visual Basic 사용자는 프로젝트에서 사용되지만 Visual Basic 프로젝트 파일에는 나타나지 않는 .bmp 파일을 체크 아웃할 수 있습니다. 사용자는 IDE에서 **Get** 명령을 선택합니다. IDE는 사용자가 얻을 수 있다고 생각되는 모든 파일의 목록을 표시하지만 목록이 `SccPopulateList` 표시되기 전에 표시할 목록이 최신 상태인지 확인하기 위해 함수가 호출됩니다.

## <a name="example"></a>예제
 IDE는 사용자가 얻을 수 있다고 생각되는 파일 목록을 작성합니다. 이 목록을 표시하기 전에 `SccPopulateList` 함수를 호출하여 소스 제어 플러그인이 목록에서 파일을 추가하고 삭제할 수 있는 기회를 제공합니다. 플러그인은 지정된 콜백 함수를 호출하여 목록을 수정합니다(자세한 내용은 [POPLISTFUNC](../extensibility/poplistfunc.md) 참조).

 플러그인은 파일이 완료된 `pfnPopulate` 후 함수에서 반환될 때까지 파일을 추가하고 삭제하는 `SccPopulateList` 함수를 계속 호출합니다. 그러면 IDE가 해당 목록을 표시할 수 있습니다. 배열은 `lpStatus` IDE에 의해 전달된 원래 목록의 모든 파일을 나타냅니다. 플러그인은 콜백 기능을 사용하는 것 외에도 이러한 모든 파일의 상태를 채웁니다.

> [!NOTE]
> 소스 제어 플러그인은 항상 이 함수에서 즉시 반환하여 목록을 그대로 둘 수 있습니다. 플러그인이 이 함수를 구현하는 경우 `SCC_CAP_POPULATELIST` [SccInitialize에](../extensibility/sccinitialize-function.md)대한 첫 번째 호출에서 기능 bitflag를 설정하여 이를 나타낼 수 있습니다. 기본적으로 플러그인은 항상 전달되는 모든 항목이 파일이라고 가정해야 합니다. 그러나 IDE가 `SCC_PL_DIR` `fOptions` 매개 변수에서 플래그를 설정하면 전달되는 모든 항목은 디렉터리로 간주됩니다. 플러그인은 디렉터리에 속한 모든 파일을 추가해야 합니다. IDE는 파일과 디렉터리가 혼합되어 전달되지 않습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [특정 명령에 사용되는 Bitflag](../extensibility/bitflags-used-by-specific-commands.md)
- [명령 코드](../extensibility/command-code-enumerator.md)
