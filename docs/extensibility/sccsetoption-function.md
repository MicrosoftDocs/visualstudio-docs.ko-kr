---
title: SccSetOption 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1adcbb47e9fce7037fe8942326e8836ade51e3eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700305"
---
# <a name="sccsetoption-function"></a>SccSetOption 함수
이 함수는 소스 제어 플러그 인의 동작을 제어 하는 옵션을 설정 합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccSetOption(
   LPVOID pvContext,
   LONG   nOption,
   LONG   dwVal
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

진행 소스 제어 플러그 인 컨텍스트 구조입니다.

 nOption

진행 설정 되는 옵션입니다.

 dwVal

진행 옵션에 대 한 설정입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|옵션을 설정 했습니다.|
|SCC_I_SHARESUBPROJOK|`nOption`가이 `SCC_OPT_SHARESUBPROJ` 고 소스 제어 플러그 인이 IDE에서 대상 폴더를 설정할 수 있는 경우 반환 됩니다.|
|SCC_E_OPNOTSUPPORTED|옵션이 설정 되지 않아에 의존해 서는 안 됩니다.|

## <a name="remarks"></a>설명
 IDE는이 함수를 호출 하 여 소스 제어 플러그 인의 동작을 제어 합니다. 첫 번째 매개 변수인는 설정 되는 `nOption` 값을 나타내고, 두 번째 매개 변수는 `dwVal` 해당 값으로 수행할 작업을 나타냅니다. 플러그 인은와 연결 된이 정보를 저장 `pvContext``,` 하므로 [Sccinitialize](../extensibility/sccinitialize-function.md) 를 호출한 후 IDE에서이 함수를 호출 해야 합니다. [SccOpenProject](../extensibility/sccopenproject-function.md)

 옵션 및 해당 값 요약:

|`nOption`|`dwValue`|설명|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|백그라운드 이벤트 큐를 사용 하거나 사용 하지 않도록 설정 합니다.|
|`SCC_OPT_USERDATA`|임의 값|[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 콜백 함수에 전달할 사용자 값을 지정 합니다.|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|IDE에서 현재 작업 취소를 지원 하는지 여부를 나타냅니다.|
|`SCC_OPT_NAMECHANGEPFN`|[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 콜백 함수에 대 한 포인터|이름 변경 콜백 함수에 대 한 포인터를 설정 합니다.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|IDE에서 소스 제어 사용자 인터페이스를 통해 파일을 수동으로 체크 아웃할 수 있는지 아니면 소스 제어 플러그 인을 통해서만 체크 아웃 해야 하는지 여부를 나타냅니다.|
|`SCC_OPT_SHARESUBPROJ`|해당 없음|소스 제어 플러그 인에서 IDE가 로컬 프로젝트 폴더를 지정할 수 있도록 허용 하는 경우 플러그 인은을 반환 `SCC_I_SHARESUBPROJOK` 합니다.|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 `nOption`가 이면 `SCC_OPT_EVENTQUEUE` IDE에서 백그라운드 처리를 사용 하지 않도록 설정 하거나 다시 사용 하도록 설정 합니다. 예를 들어, 컴파일하는 동안 IDE는 모든 종류의 유휴 상태 처리를 중지 하도록 소스 제어 플러그 인에 지시할 수 있습니다. 컴파일 후에는 백그라운드 처리를 다시 사용 하도록 설정 하 여 플러그 인의 이벤트 큐를 최신 상태로 유지할 수 있습니다. 의 값에 해당 하는 두 가지 값, 즉, 및가 있습니다 `SCC_OPT_EVENTQUEUE` `nOption` `dwVal` `SCC_OPT_EQ_ENABLE` `SCC_OPT_EQ_DISABLE` .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 의 값 `nOption` 이 인 경우 `SCC_OPT_HASCANCELMODE` IDE를 통해 사용자는 긴 작업을 취소할 수 있습니다. `dwVal` `SCC_OPT_HCM_NO` (기본값)로 설정 하면 IDE에 취소 모드가 없음을 나타냅니다. 사용자가 취소할 수 있게 하려는 경우 소스 제어 플러그 인에서 자체 취소 단추를 제공 해야 합니다. `SCC_OPT_HCM_YES` IDE에서 작업을 취소 하는 기능을 제공 하므로 SCC 플러그 인에서 자체 취소 단추를 표시 하지 않아도 됨을 나타냅니다. IDE가로 설정 된 경우에 `dwVal` `SCC_OPT_HCM_YES` 응답할 준비가 되 `SCC_MSG_STATUS` 고 `DOCANCEL` 콜백 함수로 전송 되는 메시지 `lpTextOutProc` ( [lptextoutproc](../extensibility/lptextoutproc.md)참조)입니다. IDE에서이 변수를 설정 하지 않으면 플러그 인은 이러한 두 메시지를 보내지 않아야 합니다.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 NOption을로 설정 하 `SCC_OPT_NAMECHANGEPFN` 고 소스 제어 플러그 인과 IDE를 모두 허용 하는 경우 소스 제어 작업 중에 플러그 인이 실제로 파일의 이름을 바꾸거나 파일을 이동할 수 있습니다. 는 `dwVal` [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)형식의 함수 포인터로 설정 됩니다. 소스 제어 작업 중에 플러그 인은 세 개의 매개 변수를 전달 하 여이 함수를 호출할 수 있습니다. 파일의 이전 이름 (정규화 된 경로 포함), 해당 파일의 새 이름 (정규화 된 경로 포함) 및 IDE와 관련성이 높은 정보에 대 한 포인터입니다. IDE는를로 설정 하 고 데이터를 가리켜를 호출 하 여이 마지막 포인터로를 보냅니다 `SccSetOption` `nOption` `SCC_OPT_USERDATA` `dwVal` . 이 함수에 대 한 지원은 선택 사항입니다. 이 기능을 사용 하는 VSSCI 플러그 인은 함수 포인터 및 사용자 데이터 변수를로 초기화 해야 `NULL` 하며, 지정 되지 않은 경우에는 rename 함수를 호출 하지 않아야 합니다. 또한 지정 된 값을 포함 하거나에 대 한 새 호출에 대 한 응답으로 변경 하도록 준비 해야 합니다 `SccSetOption` . 이는 소스 제어 명령 작업 중에는 발생 하지 않지만 명령 간에 발생할 수 있습니다.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 NOption가로 설정 된 경우 `SCC_OPT_SCCCHECKOUTONLY` IDE는 현재 열려 있는 프로젝트의 파일이 원본 제어 시스템의 사용자 인터페이스를 통해 수동으로 체크 아웃 되지 않음을 나타냅니다. 대신 IDE 컨트롤의 소스 제어 플러그 인을 통해서만 파일을 체크 아웃 해야 합니다. `dwValue`가로 설정 된 경우 `SCC_OPT_SCO_NO` 파일은 플러그 인에서 정상적으로 처리 되 고 소스 제어 UI를 통해 체크 아웃할 수 있습니다. 가로 설정 된 경우에는 `dwValue` `SCC_OPT_SCO_YES` 플러그 인만 파일을 체크 아웃할 수 있으며 원본 제어 시스템의 UI는 호출 되지 않아야 합니다. Ide에서 IDE를 통해서만 체크 아웃 하는 것이 적합 한 "의사 (pseudo) 파일"을 포함 하는 경우에 해당 합니다.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 가로 설정 된 경우 IDE는 소스 제어 플러그 인에서 소스 `nOption` `SCC_OPT_SHARESUBPROJ` 제어의 파일을 추가할 때 지정 된 로컬 폴더를 사용할 수 있는지 여부를 테스트 합니다. `dwVal`이 경우 매개 변수 값은 중요 하지 않습니다. 플러그 인을 사용 하는 경우 [SccAddFromScc](../extensibility/sccaddfromscc-function.md) 가 호출 될 때 IDE가 소스 제어에서 파일을 추가할 로컬 대상 폴더를 지정할 수 있으면 `SCC_I_SHARESUBPROJOK` 함수가 호출 될 때 플러그 인이 반환 되어야 합니다 `SccSetOption` . 그런 다음 IDE는 함수의 매개 변수를 사용 하 여 `lplpFileNames` `SccAddFromScc` 대상 폴더를 전달 합니다. 플러그 인은 대상 폴더를 사용 하 여 소스 제어에서 추가 된 파일을 저장 합니다. 옵션이 설정 된 경우 플러그 인이 반환 되지 않으면 `SCC_I_SHARESUBPROJOK` `SCC_OPT_SHARESUBPROJ` IDE는 플러그 인이 현재 로컬 폴더에만 파일을 추가할 수 있다고 가정 합니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
