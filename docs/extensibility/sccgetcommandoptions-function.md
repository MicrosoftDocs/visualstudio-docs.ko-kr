---
title: SccGetCommand옵션 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eeefa26422476ca40e782df3ff35eee9d429a149
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700828"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions 함수
이 함수는 지정된 명령에 대한 고급 옵션을 사용자에게 묻는 메시지를 표시합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccGetCommandOptions(
   LPVOID pvContext,
   HWND hWnd,
   enum SCCCOMMAND iCommand,
   LPCMDOPTS* ppvOptions
);
```

### <a name="parameters"></a>매개 변수
 pvContext

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 Icommand

【인】 고급 옵션이 요청되는 명령입니다(가능한 값은 [명령 코드](../extensibility/command-code-enumerator.md) 참조).

 ppv옵션

【인】 옵션 구조(일 수도 `NULL`있음).

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|성공했습니다.|
|SCC_I_ADV_SUPPORT|소스 제어 플러그인은 명령에 대한 고급 옵션을 지원합니다.|
|SCC_I_OPERATIONCANCELED|사용자가 소스 제어 플러그인의 **옵션** 대화 상자를 취소했습니다.|
|SCC_E_OPTNOTSUPPORTED|소스 제어 플러그인은 이 작업을 지원하지 않습니다.|
|SCC_E_ISCHECKEDOUT|현재 체크 아웃된 파일에서 이 작업을 수행할 수 없습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR|비특정 오류입니다.|

## <a name="remarks"></a>설명
 IDE는 소스 제어 플러그인이 `ppvOptions` = `NULL` 지정된 명령에 대한 고급 옵션 기능을 지원하는지 확인하기 위해 이 함수를 처음으로 호출합니다. 플러그인이 해당 명령에 대한 기능을 지원하는 경우 사용자가 고급 옵션(일반적으로 대화 상자의 **고급** 단추로 구현)을 요청하고 해당 포인터에 대해 `ppvOptions` NULL이 아닌 `NULL` 포인터를 제공하면 IDE는 이 함수를 다시 호출합니다. 플러그인은 사용자가 지정한 고급 옵션을 개인 구조에 저장하고 에서 해당 `ppvOptions`구조에 대한 포인터를 반환합니다. 그런 다음 이 구조는 `SccGetCommandOptions` 함수에 대한 후속 호출을 포함하여 이 에 대해 알아야 하는 다른 모든 소스 제어 플러그인 API 함수에 전달됩니다.

 예를 들어 이 상황을 명확히 하는 데 도움이 될 수 있습니다.

 사용자가 **Get** 명령을 선택하고 IDE에 대화 **상자 가** 표시됩니다. `SccGetCommandOptions` IDE는 로 `iCommand` 설정하고 `SCC_COMMAND_GET` `ppvOptions` 로 설정된 `NULL`함수를 호출합니다. 이것은 소스 제어 플러그인에 의해 질문으로 해석됩니다, "이 명령에 대한 고급 옵션이 있습니까?" 플러그인이 반환되면 `SCC_I_ADV_SUPPORT`IDE는 대화 상자 **에** **고급** 단추를 표시합니다.

 사용자가 **고급** 단추를 처음 클릭할 때 IDE는 `SccGetCommandOptions` 함수를 다시 호출하며`NULL``ppvOptions` 이번에는 포인터를 가리키는 비(non-)가 있는 함수를 `NULL` 호출합니다. 플러그인은 자체 옵션 **받기** 대화 상자를 표시하고, 사용자에게 정보를 묻고, 해당 정보를 자체 구조로 넣고, `ppvOptions`해당 구조에 대한 포인터를 반환합니다.

 사용자가 동일한 대화 상자에서 **Advanced를** 다시 클릭하면 구조가 `SccGetCommandOptions` 다시 플러그인으로 전달되도록 IDE는 변경하지 `ppvOptions`않고 함수를 다시 호출합니다. 이렇게 하면 플러그인이 대화 상자를 사용자가 이전에 설정한 값으로 다시 초기화할 수 있습니다. 플러그 인은 반환하기 전에 구조를 수정합니다.

 마지막으로 사용자가 IDE의 **대화 상자에서** **확인을** 클릭하면 IDE는 [SccGet을](../extensibility/sccget-function.md)호출하여 고급 `ppvOptions` 옵션이 포함된 구조가 반환됩니다.

> [!NOTE]
> 이 `SCC_COMMAND_OPTIONS` 명령은 사용자가 통합 작동 방식을 제어하는 기본 설정을 설정할 수 있는 **옵션** 대화 상자를 IDE에 표시할 때 사용됩니다. 소스 제어 플러그인이 자체 기본 설정 대화 상자를 제공하려는 경우 IDE의 기본 설정 대화 상자의 **고급** 단추에서 표시할 수 있습니다. 플러그인은 이 정보를 얻고 유지하는 전적인 책임이 있습니다. IDE는 이를 사용하거나 수정하지 않습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
- [명령 코드](../extensibility/command-code-enumerator.md)
