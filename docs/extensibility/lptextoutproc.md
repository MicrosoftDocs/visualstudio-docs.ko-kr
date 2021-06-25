---
title: LPTEXTOUTPROC | Microsoft Docs
description: LPTEXTOUTPROC 함수 포인터에 대해 알아봅니다. Visual Studio IDE는 오류 및 상태를 표시하는 함수를 구현합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c313375efe8afd17dd5d76f55de4cdaf016bab40
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903101"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

사용자가 IDE(통합 개발 환경) 내에서 소스 제어 작업을 실행하는 경우 소스 제어 플러그 인은 작업과 관련된 오류 또는 상태 메시지를 전달하려고 할 수 있습니다. 플러그 인은 이 목적을 위해 자체 메시지 상자를 표시할 수 있습니다. 그러나 더 원활한 통합을 위해 플러그 인은 IDE에 문자열을 전달한 다음, 상태 정보를 표시하는 기본 방식으로 문자열을 표시할 수 있습니다. 이에 대한 메커니즘은 `LPTEXTOUTPROC` 함수 포인터입니다. IDE는 오류 및 상태를 표시하기 위해 이 함수(아래에서 자세히 설명)를 구현합니다.

IDE는 `lpTextOutProc` [SccOpenProject](../extensibility/sccopenproject-function.md)를 호출할 때 이 함수에 대한 함수 포인터를 매개 변수로 소스 제어 플러그 인에 전달합니다. 예를 들어 많은 파일이 포함된 [SccGet](../extensibility/sccget-function.md) 호출 중에 SCC 작업 중에 플러그 인은 함수를 호출하여 `LPTEXTOUTPROC` 표시할 문자열을 주기적으로 전달할 수 있습니다. IDE는 상태 표시줄, 출력 창 또는 별도의 메시지 상자에 이러한 문자열을 적절하게 표시할 수 있습니다. 필요에 따라 IDE는 **취소** 단추를 사용하여 특정 메시지를 표시할 수 있습니다. 이렇게 하면 사용자가 작업을 취소할 수 있으며 이 정보를 플러그 인에 다시 전달할 수 있는 기능이 IDE에 부여됩니다.

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

표시할 텍스트 문자열입니다. 캐리지 리턴 또는 줄 피드로 이 문자열을 종료하면 안 됩니다.

mesg_type

메시지의 형식입니다. 다음 표에서는 이 매개 변수에 대해 지원되는 값을 나열합니다.

|값|설명|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|메시지는 정보, 경고 또는 오류로 간주됩니다.|
|`SCC_MSG_STATUS`|메시지는 상태를 표시하며 상태 표시줄에 표시될 수 있습니다.|
|`SCC_MSG_DOCANCEL`|메시지 문자열 없이 전송되었습니다.|
|`SCC_MSG_STARTCANCEL`|**취소** 단추 표시를 시작합니다.|
|`SCC_MSG_STOPCANCEL`|**취소** 단추 표시를 중지합니다.|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|백그라운드 작업을 취소할 것인지 IDE에 묻습니다. 작업이 취소된 경우 IDE는 를 `SCC_MSG_RTN_CANCEL` 반환하고, 그렇지 않으면 를 반환합니다. `SCC_MSG_RTN_OK` `display_string`매개 변수는 소스 제어 플러그 인에서 제공하는 [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) 구조체로 캐스팅됩니다.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|버전 제어에서 파일을 검색하기 전에 IDE에 지시합니다. `display_string`매개 변수는 소스 제어 플러그 인에서 제공하는 [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) 구조체로 캐스팅됩니다.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|버전 제어에서 파일을 검색한 후 IDE에 지시합니다. `display_string`매개 변수는 소스 제어 플러그 인에서 제공하는 [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) 구조체로 캐스팅됩니다.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|백그라운드 작업의 현재 상태를 IDE에 알려줍니다. `display_string`매개 변수는 소스 제어 플러그 인에서 제공하는 [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) 구조체로 캐스팅됩니다.|

## <a name="return-value"></a>반환 값

|값|설명|
|-----------|-----------------|
|SCC_MSG_RTN_OK|문자열이 표시되거나 작업이 성공적으로 완료되었습니다.|
|SCC_MSG_RTN_CANCEL|사용자가 작업을 취소하려고 합니다.|

## <a name="example"></a>예제
 IDE가 20개의 파일 이름을 가진 [SccGet을](../extensibility/sccget-function.md) 호출한다고 가정합니다. 소스 제어 플러그 인은 파일 get 중간에 작업을 취소하지 않도록 하려고 합니다. 각 파일을 받은 후 를 `lpTextOutProc` 호출하고, 각 파일에 대한 상태 정보를 전달하고, `SCC_MSG_DOCANCEL` 보고할 상태가 없는 경우 메시지를 보냅니다. 언제든지 플러그 인이 IDE에서 의 반환 값을 받으면 `SCC_MSG_RTN_CANCEL` 더 이상 파일이 검색되지 않도록 get 작업을 즉시 취소합니다.

## <a name="structures"></a>구조체

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 이 구조는 메시지와 함께 `SCC_MSG_BACKGROUND_IS_CANCELLED` 전송됩니다. 취소된 백그라운드 작업의 ID를 전달하는 데 사용됩니다.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 이 구조는 메시지와 함께 `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` 전송됩니다. 검색할 파일의 이름과 검색을 수행하는 백그라운드 작업의 ID를 전달하는 데 사용됩니다.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 이 구조는 메시지와 함께 `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` 전송됩니다. 지정된 파일을 검색한 결과와 검색을 수행했던 백그라운드 작업의 ID를 전달하는 데 사용됩니다. 결과로 제공될 수 있는 내용은 [SccGet의](../extensibility/sccget-function.md) 반환 값을 참조하세요.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 이 구조는 메시지와 함께 `SCC_MSG_BACKGROUND_ON_MESSAGE` 전송됩니다. 백그라운드 작업의 현재 상태를 전달하는 데 사용됩니다. 상태는 IDE에서 표시할 문자열로 표시되며 `bIsError` 메시지의 심각도를 `TRUE` 나타냅니다(오류 메시지의 경우 , `FALSE` 경고의 경우 또는 정보 메시지의 경우 ). 상태를 보내는 백그라운드 작업의 ID도 지정됩니다.

## <a name="code-example"></a>코드 예제
 다음은 호출에 대한 `LPTEXTOUTPROC` 구조를 캐스팅하는 방법을 보여주는 메시지를 보내기 위해 를 호출하는 간단한 `SCC_MSG_BACKGROUND_ON_MESSAGE` 예제입니다.

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
- [IDE에서 구현하는 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
