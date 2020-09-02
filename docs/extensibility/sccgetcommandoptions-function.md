---
title: SccGetCommandOptions 함수 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700828"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions 함수
이 함수는 지정 된 명령에 대 한 고급 옵션을 사용자에 게 표시 합니다.

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

진행 소스 제어 플러그 인 컨텍스트 구조입니다.

 hWnd

진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.

 iCommand

진행 고급 옵션이 요청 된 명령입니다 (가능한 값에 대 한 [명령 코드](../extensibility/command-code-enumerator.md) 참조).

 ppvOptions

진행 옵션 구조 (일 수도 있습니다 `NULL` .

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|성공했습니다.|
|SCC_I_ADV_SUPPORT|원본 제어 플러그 인은 명령에 대 한 고급 옵션을 지원 합니다.|
|SCC_I_OPERATIONCANCELED|사용자가 소스 제어 플러그 인 **옵션** 대화 상자를 취소 했습니다.|
|SCC_E_OPTNOTSUPPORTED|소스 제어 플러그 인에서이 작업을 지원 하지 않습니다.|
|SCC_E_ISCHECKEDOUT|현재 체크 아웃 된 파일에 대해이 작업을 수행할 수 없습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다. 다시 시도 하는 것이 좋습니다.|
|SCC_E_NONSPECIFICERROR|일반 오류입니다.|

## <a name="remarks"></a>설명
 IDE는를 사용 하 여 처음으로이 함수를 호출 `ppvOptions` = `NULL` 하 여 소스 제어 플러그 인이 지정 된 명령에 대 한 고급 옵션 기능을 지원 하는지 여부를 확인 합니다. 플러그 인이 해당 명령에 대 한 기능을 지 원하는 경우 사용자가 고급 옵션 (일반적으로 대화 상자에서 **고급** 단추로 구현 됨)을 요청 하 고 해당 포인터에 대 한 NULL이 아닌 포인터를 포인터로 제공 하면 IDE에서이 함수를 다시 호출 합니다 `ppvOptions` `NULL` . 플러그 인은 사용자가 지정한 모든 고급 옵션을 전용 구조에 저장 하 고의 해당 구조에 대 한 포인터를 반환 합니다 `ppvOptions` . 그런 다음이 구조는 함수에 대 한 후속 호출을 포함 하 여 알아야 하는 다른 모든 소스 제어 플러그 인 API 함수로 전달 됩니다 `SccGetCommandOptions` .

 이러한 상황을 명확 하 게 보여 주는 예를 들면 다음과 같습니다.

 사용자가 **get** 명령을 선택 하면 IDE는 **get** 대화 상자를 표시 합니다. IDE는 `SccGetCommandOptions` `iCommand` 를로 설정 하 `SCC_COMMAND_GET` 고를로 `ppvOptions` 설정 하 여 함수 `NULL` 를 호출 합니다. 이는 "이 명령에 대 한 고급 옵션이 있습니까?" 라는 질문으로 소스 제어 플러그 인에 의해 해석 됩니다. 플러그 인이 반환 되는 경우 `SCC_I_ADV_SUPPORT` IDE는 **가져오기** 대화 상자에 **고급** 단추를 표시 합니다.

 사용자가 **고급** 단추를 처음 클릭 하면 IDE에서 함수를 다시 호출 합니다 `SccGetCommandOptions` . 이번에 `NULL``ppvOptions` 는 포인터를 가리키는가 아닌를 사용 합니다 `NULL` . 플러그 인은 자체 **가져오기 옵션** 대화 상자를 표시 하 고, 사용자에 게 정보를 묻는 메시지를 표시 하 고, 해당 정보를 자체 구조에 저장 하 고,의 해당 구조에 대 한 포인터를 반환 합니다 `ppvOptions` .

 사용자가 같은 대화 상자에서 **고급** 을 다시 클릭 하는 경우 IDE는 `SccGetCommandOptions` 변경 없이 함수를 다시 호출 `ppvOptions` 하므로 구조가 플러그 인으로 다시 전달 됩니다. 이를 통해 플러그 인은 사용자가 이전에 설정한 값으로 대화 상자를 다시 초기화할 수 있습니다. 플러그 인은를 반환 하기 전에 구조를 먼저 수정 합니다.

 마지막으로, 사용자가 IDE의 **가져오기** 대화 상자에서 **확인** 을 클릭 하면 Ide는 [sccget](../extensibility/sccget-function.md)을 호출 하 여 `ppvOptions` 고급 옵션을 포함 하는에서 반환 된 구조체를 전달 합니다.

> [!NOTE]
> 이 명령은 `SCC_COMMAND_OPTIONS` IDE가 통합의 작동 방식을 제어 하는 기본 설정을 지정할 수 있는 **옵션** 대화 상자를 표시할 때 사용 됩니다. 소스 제어 플러그 인에서 자체 기본 설정 대화 상자를 제공 하려는 경우 IDE의 기본 설정 대화 상자에 있는 **고급** 단추에서 해당 대화 상자를 표시할 수 있습니다. 플러그 인은이 정보를 가져오고 유지 하는 일을 담당 합니다. IDE는이를 사용 하거나 수정 하지 않습니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [명령 코드](../extensibility/command-code-enumerator.md)
