---
title: SccSet옵션 기능 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700305"
---
# <a name="sccsetoption-function"></a>SccSetOption 함수
이 함수는 소스 제어 플러그인의 동작을 제어하는 옵션을 설정합니다.

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

【인】 소스 제어 플러그인 컨텍스트 구조입니다.

 n옵션

【인】 설정 중인 옵션입니다.

 dwVal

【인】 옵션에 대한 설정입니다.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|옵션이 성공적으로 설정되었습니다.|
|SCC_I_SHARESUBPROJOK|반환된 `nOption` `SCC_OPT_SHARESUBPROJ` 경우 원본 제어 플러그인을 사용하면 IDE에서 대상 폴더를 설정할 수 있습니다.|
|SCC_E_OPNOTSUPPORTED|옵션이 설정되지 않았으며 의존해서는 안됩니다.|

## <a name="remarks"></a>설명
 IDE는 이 함수를 호출하여 소스 제어 플러그인의 동작을 제어합니다. 첫 번째 `nOption`매개 변수는 설정 중인 값을 나타내고 `dwVal`두 번째 매개 변수는 해당 값으로 수행할 작업을 나타냅니다. 플러그인은 IDE가 `pvContext``,` [SccInitialize를](../extensibility/sccinitialize-function.md) 호출한 후 이 함수를 호출해야 하므로 이 정보와 연결된 정보를 저장합니다(SccOpenProject에 대한 각 호출 후 반드시 그런 것은 아닙니다). [SccOpenProject](../extensibility/sccopenproject-function.md)

 옵션 및 해당 값요약:

|`nOption`|`dwValue`|설명|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|백그라운드 이벤트 큐를 활성화/비활성화합니다.|
|`SCC_OPT_USERDATA`|임의 값|[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 콜백 함수에 전달될 사용자 값을 지정합니다.|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|IDE가 현재 작업 취소를 지원하는지 여부를 나타냅니다.|
|`SCC_OPT_NAMECHANGEPFN`|[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 콜백 함수에 대한 포인터|이름 변경 콜백 함수에 대한 포인터를 설정합니다.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|IDE가 소스 제어 사용자 인터페이스를 통해 수동으로 파일을 체크 아웃할 수 있는지 또는 소스 제어 플러그인을 통해서만 체크 아웃해야 하는지 여부를 나타냅니다.|
|`SCC_OPT_SHARESUBPROJ`|해당 없음|소스 제어 플러그인에서 IDE가 로컬 프로젝트 폴더를 지정할 수 `SCC_I_SHARESUBPROJOK`있도록 허용하면 플러그인이 반환됩니다.|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 있는 `nOption` `SCC_OPT_EVENTQUEUE`경우 IDE가 백그라운드 처리를 사용하지 않도록 설정(또는 다시 활성화)합니다. 예를 들어 컴파일 중에 IDE는 소스 제어 플러그인에 모든 종류의 유휴 처리를 중지하도록 지시할 수 있습니다. 컴파일 후 백그라운드 처리를 다시 활성화하여 플러그인의 이벤트 큐를 최신 상태로 유지합니다. `SCC_OPT_EVENTQUEUE` `dwVal` `SCC_OPT_EQ_ENABLE` `SCC_OPT_EQ_DISABLE`의 값에 해당하는 두 가지 가능한 값, 즉 에 대한 값이 있습니다. `nOption`

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 값이 `nOption` `SCC_OPT_HASCANCELMODE`있는 경우 IDE를 사용하면 사용자가 긴 작업을 취소할 수 있습니다. (기본값)로 `dwVal` `SCC_OPT_HCM_NO` 설정하면 IDE에 취소 모드가 없음을 나타냅니다. 소스 제어 플러그인은 사용자가 취소할 수 있도록 하려면 자체 취소 단추를 제공해야 합니다. `SCC_OPT_HCM_YES`은 IDE가 작업을 취소할 수 있는 기능을 제공하므로 SCC 플러그인에 자체 취소 단추를 표시할 필요가 없음을 나타냅니다. `dwVal` IDE가 `SCC_OPT_HCM_YES`로 설정되면 `lpTextOutProc` 콜백 `SCC_MSG_STATUS` 함수로 `DOCANCEL` 전송된 메시지에 응답할 준비가 되어 있습니다(LPTEXTOUTPROC 참조). [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) IDE가 이 변수를 설정하지 않으면 플러그인이 이 두 메시지를 보내지 않아야 합니다.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 nOption이 `SCC_OPT_NAMECHANGEPFN`로 설정되어 있고 소스 제어 플러그인과 IDE가 모두 허용하는 경우 플러그인은 소스 제어 작업 중에 실제로 파일의 이름을 바꾸거나 이동할 수 있습니다. 는 `dwVal` [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)형식의 함수 포인터로 설정됩니다. 소스 제어 작업 중에 플러그인은 세 가지 매개 변수를 전달하여 이 함수를 호출할 수 있습니다. 파일의 이전 이름(정규화된 경로), 해당 파일의 새 이름(정규화된 경로)과 IDE와 관련이 있는 정보에 대한 포인터입니다. IDE는 `SccSetOption` 데이터를 `nOption` `SCC_OPT_USERDATA` `dwVal` 가리키며 sets를 호출하여 이 마지막 포인터를 보냅니다. 이 기능에 대한 지원은 선택 사항입니다. 이 기능을 사용하는 VSSCI 플러그는 함수 포인터와 사용자 데이터 `NULL`변수를 초기화해야 하며, 함수가 지정되지 않은 경우 이름 바꾸기 함수를 호출해서는 안 됩니다. 또한 주어진 값을 유지하거나 에 대한 새 호출에 대한 응답으로 변경할 `SccSetOption`준비를 해야 합니다. 이 작업은 소스 제어 명령 작업 중간에 발생하지 않지만 명령 간에 발생할 수 있습니다.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 nOption을 `SCC_OPT_SCCCHECKOUTONLY`로 설정된 경우 IDE는 현재 열려 있는 프로젝트의 파일을 소스 제어 시스템의 사용자 인터페이스를 통해 수동으로 체크 아웃해서는 안 됨을 나타냅니다. 대신, 파일은 IDE 제어하에 있는 소스 제어 플러그인을 통해서만 체크 아웃해야 합니다. `SCC_OPT_SCO_NO`을 설정하면 `dwValue` 파일이 플러그인에 의해 정상적으로 처리되어야 하며 소스 제어 UI를 통해 체크 아웃할 수 있음을 의미합니다. 로 설정된 경우 `dwValue` 플러그인만 파일을 체크 아웃할 수 있으며 소스 제어 시스템의 UI를 호출해서는 안 됩니다. `SCC_OPT_SCO_YES` 이는 IDE가 IDE를 통해서만 체크 아웃하는 "의사 파일"을 가질 수 있는 경우입니다.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 로 설정된 경우`nOption` IDE는 소스 제어 플러그인이 소스 제어에서 파일을 추가할 때 지정된 로컬 폴더를 사용할 수 있는지 여부를 테스트합니다. `SCC_OPT_SHARESUBPROJ` 이 경우 `dwVal` 매개 변수의 값은 중요하지 않습니다. 플러그인을 통해 IDE가 [SccAddFromScc가](../extensibility/sccaddfromscc-function.md) 호출될 때 소스 컨트롤에서 파일이 추가될 로컬 대상 폴더를 지정할 `SCC_I_SHARESUBPROJOK` 수 `SccSetOption` 있도록 허용하는 경우 함수가 호출될 때 플러그인이 반환되어야 합니다. 그런 다음 IDE는 함수의 매개 변수를 `lplpFileNames` `SccAddFromScc` 사용하여 대상 폴더에 전달합니다. 플러그인은 해당 대상 폴더를 사용하여 소스 컨트롤에서 추가된 파일을 배치합니다. 옵션을 설정할 때 플러그인이 `SCC_I_SHARESUBPROJOK` 반환되지 않으면 IDE는 플러그인이 현재 로컬 폴더에만 파일을 추가할 수 있다고 가정합니다. `SCC_OPT_SHARESUBPROJ`

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
