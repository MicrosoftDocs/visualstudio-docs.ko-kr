---
title: LPTEXTOUTPROC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
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
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f14942ffd59ce2c6eacf7da2d0d1ab252d58e2cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194455"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자가 IDE (통합 개발 환경) 내에서 소스 제어 작업을 실행할 때 소스 제어 플러그 인에서 작업과 관련 된 오류 또는 상태 메시지를 전달 해야 할 수 있습니다. 플러그 인은 이러한 용도로 자체 메시지 상자를 표시할 수 있습니다. 그러나 원활한 통합을 위해 플러그 인은 IDE에 문자열을 전달 하 여 상태 정보를 표시 하는 기본 방법으로 표시할 수 있습니다. 이에 대 한 메커니즘은 `LPTEXTOUTPROC` 함수 포인터입니다. IDE는 오류 및 상태 표시를 위해이 함수 (아래에서 자세히 설명)를 구현 합니다.  
  
 IDE는 `lpTextOutProc` [Sccopenproject](../extensibility/sccopenproject-function.md)를 호출할 때이 함수에 대 한 함수 포인터를 매개 변수로 전달 하 여 소스 제어 플러그 인에 전달 합니다. 예를 들어, SCC 작업 중에 여러 파일을 포함 하는 [Sccget](../extensibility/sccget-function.md) 호출 중에 플러그 인은 함수를 호출 하 여 `LPTEXTOUTPROC` 표시할 문자열을 주기적으로 전달할 수 있습니다. IDE는 이러한 문자열을 상태 표시줄, 출력 창 또는 별도의 메시지 상자에 적절 하 게 표시할 수 있습니다. 필요에 따라 IDE는 **취소** 단추를 사용 하 여 특정 메시지를 표시할 수 있습니다. 이렇게 하면 사용자가 작업을 취소할 수 있으며, IDE에서이 정보를 플러그 인에 다시 전달할 수 있는 기능을 제공 합니다.  
  
## <a name="signature"></a>서명  
 IDE의 output 함수에는 다음과 같은 시그니처가 있습니다.  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 display_string  
 표시할 텍스트 문자열입니다. 이 문자열은 캐리지 리턴 또는 줄 바꿈으로 종료 되어서는 안 됩니다.  
  
 mesg_type  
 메시지의 형식입니다. 다음 표에서는이 매개 변수에 대해 지원 되는 값을 보여 줍니다.  
  
|값|설명|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|메시지는 정보, 경고 또는 오류로 간주 됩니다.|  
|`SCC_MSG_STATUS`|이 메시지는 상태를 표시 하 고 상태 표시줄에 표시할 수 있습니다.|  
|`SCC_MSG_DOCANCEL`|메시지 문자열 없이 전송 됩니다.|  
|`SCC_MSG_STARTCANCEL`|**취소** 단추를 표시 하기 시작 합니다.|  
|`SCC_MSG_STOPCANCEL`|**취소** 단추 표시를 중지 합니다.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|백그라운드 작업을 취소 해야 하는 경우 ide를 요청 합니다. 작업이 취소 되 면 IDE가 반환 되 `SCC_MSG_RTN_CANCEL` 고, 그렇지 않으면를 반환 `SCC_MSG_RTN_OK` 합니다. `display_string`매개 변수는 소스 제어 플러그 인에서 제공 하는 [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) 구조체로 캐스팅 됩니다.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|버전 제어에서 파일을 검색 하기 전에 IDE에 파일을 알립니다. `display_string`매개 변수는 소스 제어 플러그 인에서 제공 하는 [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) 구조체로 캐스팅 됩니다.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|버전 제어에서 검색 된 후 파일을 IDE에 알립니다. `display_string`매개 변수는 소스 제어 플러그 인에서 제공 하는 [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) 구조체로 캐스팅 됩니다.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|백그라운드 작업의 현재 상태를 IDE에 알립니다. `display_string`매개 변수는 원본 제어 플러그 인에서 제공 하는 [Sccmsgdataonmessage](#LinkSccMsgDataOnMessage) 구조체로 캐스팅 됩니다.|  
  
## <a name="return-value"></a>Return Value  
  
|값|설명|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|문자열이 표시 되었거나 작업이 성공적으로 완료 되었습니다.|  
|SCC_MSG_RTN_CANCEL|사용자가 작업을 취소 하려고 합니다.|  
  
## <a name="example"></a>예  
 IDE에서 파일 이름이 20 인 [Sccget](../extensibility/sccget-function.md) 을 호출 한다고 가정 합니다. 소스 제어 플러그 인에서 파일의 중간에 있는 작업 취소를 방지 하려고 합니다. 각 파일을 가져온 후에는를 호출 하 `lpTextOutProc` 여 각 파일에 상태 정보를 전달 하 고 `SCC_MSG_DOCANCEL` 보고할 상태가 없으면 메시지를 보냅니다. 플러그 인이 IDE에서 반환 값을 받을 때 언제 든 지 `SCC_MSG_RTN_CANCEL` 가져오기 작업을 취소 하 여 더 이상 파일이 검색 되지 않도록 합니다.  
  
## <a name="structures"></a>구조체  
  
### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 이 구조는 메시지와 함께 전송 됩니다 `SCC_MSG_BACKGROUND_IS_CANCELLED` . 이는 취소 된 백그라운드 작업의 ID를 전달 하는 데 사용 됩니다.  
  
### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 이 구조는 메시지와 함께 전송 됩니다 `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` . 검색할 파일의 이름과 검색을 수행 하는 백그라운드 작업의 ID를 전달 하는 데 사용 됩니다.  
  
### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 이 구조는 메시지와 함께 전송 됩니다 `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` . 지정 된 파일을 검색 한 결과와 검색 된 백그라운드 작업의 ID를 전달 하는 데 사용 됩니다. 결과로 제공할 수 있는 항목에 대 한 [Sccget](../extensibility/sccget-function.md) 의 반환 값을 참조 하세요.  
  
### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 이 구조는 메시지와 함께 전송 됩니다 `SCC_MSG_BACKGROUND_ON_MESSAGE` . 백그라운드 작업의 현재 상태를 전달 하는 데 사용 됩니다. 상태는 IDE에서 표시 되는 문자열로 표시 되 고 `bIsError` 메시지의 심각도를 나타냅니다 ( `TRUE` 오류 메시지의 경우, `FALSE` 경고의 경우 또는 정보 메시지의 경우). 상태를 전송 하는 백그라운드 작업의 ID도 제공 됩니다.  
  
## <a name="code-example"></a>코드 예  
 다음은 `LPTEXTOUTPROC` `SCC_MSG_BACKGROUND_ON_MESSAGE` 호출에 대 한 구조를 캐스팅 하는 방법을 보여 주는 메시지를 보내기 위해를 호출 하는 간단한 예제입니다.  
  
```cpp#  
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
  
## <a name="see-also"></a>관련 항목  
 [IDE에서 구현 하는 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
