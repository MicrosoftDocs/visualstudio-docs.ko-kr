---
title: LPTEXTOUTPROC | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38c3e8263b9a30058c2de019e5e92160b716aa71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702798"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

사용자가 IDE(통합 개발 환경) 내부에서 소스 제어 작업을 실행하는 경우 소스 제어 플러그인은 작업과 관련된 오류 또는 상태 메시지를 전달할 수 있습니다. 플러그인은 이 목적을 위해 자체 메시지 상자를 표시할 수 있습니다. 그러나 보다 원활한 통합을 위해 플러그인은 문자열을 IDE에 전달한 다음 상태 정보를 표시하는 기본 방식으로 문자열을 표시할 수 있습니다. 이 메커니즘은 함수 `LPTEXTOUTPROC` 포인터입니다. IDE는 오류 및 상태를 표시하기 위해 이 함수(아래에 자세히 설명됨)를 구현합니다.

IDE는 `lpTextOutProc` [SccOpenProject](../extensibility/sccopenproject-function.md)를 호출할 때 소스 제어 플러그인 함수 포인터를 매개 변수로 이 함수에 전달합니다. 예를 들어 많은 파일이 포함된 [SccGet을](../extensibility/sccget-function.md) 호출하는 동안 SCC 작업 중에 플러그인은 `LPTEXTOUTPROC` 함수를 호출하여 주기적으로 표시할 문자열을 전달할 수 있습니다. IDE는 이러한 문자열을 상태 표시줄, 출력 창 또는 별도의 메시지 상자에 적절히 표시할 수 있습니다. 선택적으로 IDE는 **취소** 버튼으로 특정 메시지를 표시할 수 있습니다. 이렇게 하면 사용자가 작업을 취소할 수 있으며 IDE는 이 정보를 다시 플러그인으로 전달할 수 있습니다.

## <a name="signature"></a>서명
 IDE의 출력 함수에는 다음과 같은 서명이 있습니다.

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>매개 변수

display_string

표시할 텍스트 문자열입니다. 이 문자열은 캐리지 리턴 또는 라인 피드로 종료해서는 안 됩니다.

mesg_type

메시지의 형식입니다. 다음 표에는 이 매개 변수에 대해 지원되는 값이 나열되어 있습니다.

|값|Description|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|메시지는 정보, 경고 또는 오류로 간주됩니다.|
|`SCC_MSG_STATUS`|이 메시지는 상태를 표시하고 상태 표시줄에 표시할 수 있습니다.|
|`SCC_MSG_DOCANCEL`|메시지 문자열없이 전송됩니다.|
|`SCC_MSG_STARTCANCEL`|**취소** 단추 표시를 시작합니다.|
|`SCC_MSG_STOPCANCEL`|**취소** 단추 표시를 중지합니다.|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|백그라운드 작업을 취소할 것인지 IDE에 요청합니다: 작업이 취소된 경우 IDE가 반환됩니다. `SCC_MSG_RTN_CANCEL` 그렇지 않으면 `SCC_MSG_RTN_OK`을 반환합니다. 매개 `display_string` 변수는 소스 제어 플러그인에서 제공하는 [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) 구조로 캐스팅됩니다.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|버전 컨트롤에서 파일을 검색하기 전에 IDE에 파일에 대해 알려줍니다. 매개 `display_string` 변수는 소스 제어 플러그인에서 제공하는 [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) 구조로 캐스팅됩니다.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|버전 컨트롤에서 파일을 검색한 후 IDE에 파일에 대해 알려줍니다. 매개 `display_string` 변수는 소스 제어 플러그인에서 제공하는 [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) 구조로 캐스팅됩니다.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|배경 작업의 현재 상태를 IDE에 지정합니다. 매개 `display_string` 변수는 소스 제어 플러그인에서 제공하는 [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) 구조로 캐스팅됩니다.|

## <a name="return-value"></a>반환 값

|값|Description|
|-----------|-----------------|
|SCC_MSG_RTN_OK|문자열이 표시되었지만 작업이 성공적으로 완료되었습니다.|
|SCC_MSG_RTN_CANCEL|사용자가 작업을 취소하려고 합니다.|

## <a name="example"></a>예제
 IDE가 20개의 파일 이름으로 [SccGet을](../extensibility/sccget-function.md) 호출한다고 가정합니다. 소스 제어 플러그인은 파일 get 중간에 작업을 취소하지 않도록 하려고 합니다. 각 파일을 가져오는 후 `lpTextOutProc`호출하여 각 파일의 상태 정보를 `SCC_MSG_DOCANCEL` 전달하고 보고할 상태가 없는 경우 메시지를 보냅니다. 언제든지 플러그인이 `SCC_MSG_RTN_CANCEL` IDE에서 반환 값을 받으면 get 작업을 즉시 취소하여 더 이상 파일이 검색되지 않습니다.

## <a name="structures"></a>구조체

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIs취소

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 이 구조는 `SCC_MSG_BACKGROUND_IS_CANCELLED` 메시지와 함께 전송됩니다. 취소된 백그라운드 작업의 ID를 통신하는 데 사용됩니다.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccmsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 이 구조는 `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` 메시지와 함께 전송됩니다. 검색할 파일의 이름과 검색을 수행하는 백그라운드 작업의 ID를 전달하는 데 사용됩니다.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccmsgData온애프터겟파일

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 이 구조는 `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` 메시지와 함께 전송됩니다. 지정된 파일을 검색한 결과와 검색을 수행한 백그라운드 작업의 ID를 전달하는 데 사용됩니다. 결과로 부여할 수 있는 내용은 [SccGet의](../extensibility/sccget-function.md) 반환 값을 참조하십시오.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccmsgData온메시지

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 이 구조는 `SCC_MSG_BACKGROUND_ON_MESSAGE` 메시지와 함께 전송됩니다. 백그라운드 작업의 현재 상태를 통신하는 데 사용됩니다. 상태는 IDE에 의해 표시될 문자열로 표현되며 `bIsError` 메시지의 심각도를`TRUE` 나타냅니다(오류 메시지; `FALSE` 경고 또는 정보 메시지에 대한). 상태를 보내는 백그라운드 작업의 ID도 제공됩니다.

## <a name="code-example"></a>코드 예제
 다음은 `LPTEXTOUTPROC` `SCC_MSG_BACKGROUND_ON_MESSAGE` 메시지를 보내도록 요청하는 간단한 예제로, 호출의 구조를 캐스팅하는 방법을 보여 주습니다.

```cpp
LONG SendStatusMessage(
    LPTEXTOUTPROC pTextOutProc,
    DWORD         dwBackgroundID,
    LPCTSTR       pStatusMsg,
    BOOL          bIsError)
{
    SccMsgDataOnMessage msgData = { 0 };
    LONG                result  = 0;

    msgData.dwBackgroundOperationID = dwBackgroundID;
    msgData.szMessage               = pStatusMsg;
    msgData.bIsError                = bIsError;

    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);
    return result;
}
```

## <a name="see-also"></a>참조
- [IDE에서 구현한 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)
- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md)
