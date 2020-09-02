---
title: 메시지 열거자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bd42c825cd45068e13178856e524268b426ec53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194333"
---
# <a name="message-enumerator"></a>메시지 열거자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음 플래그는 함수에 사용 됩니다 `TEXTOUTPROC` .이 함수는 IDE에서 [Sccopenproject](../extensibility/sccopenproject-function.md) 를 호출할 때 제공 하는 콜백 함수입니다 (콜백 함수에 대 한 자세한 내용은 [lptextoutproc](../extensibility/lptextoutproc.md) 참조).  
  
 프로세스를 취소 하 라는 메시지가 IDE에 표시 되 면 취소 메시지 중 하나가 표시 될 수 있습니다. 이 경우 소스 제어 플러그 인은를 사용 하 여 `SCC_MSG_STARTCANCEL` IDE에 **취소** 단추를 표시 하도록 요청 합니다. 그러면 모든 일반 메시지 집합이 전송 될 수 있습니다. 이러한 값이 반환 되 면 플러그 인이 `SCC_MSG_RTN_CANCEL` 작업을 종료 하 고를 반환 합니다. 또한 플러그 인은 `SCC_MSG_DOCANCEL` 사용자가 작업을 취소 했는지 여부를 주기적으로 폴링합니다. 모든 작업이 완료 되거나 사용자가 취소 한 경우 플러그 인은를 보냅니다 `SCC_MSG_STOPCANCEL` . `SCC_MSG_INFO`, SCC_MSG_WARNING 및 SCC_MSG_ERROR 유형은 메시지의 스크롤 목록에 표시 되는 메시지에 사용 됩니다. `SCC_MSG_STATUS` 는 상태 표시줄이 나 임시 표시 영역에 텍스트가 표시 되어야 함을 나타내는 특수 한 형식입니다. 목록에서 영구적으로 유지 되지 않습니다.  
  
## <a name="syntax"></a>구문  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>멤버  
 SCC_MSG_RTN_CANCEL  
 취소를 나타내려면 콜백에서 반환 합니다.  
  
 SCC_MSG_RTN_OK  
 계속 하려면 콜백에서 반환 합니다.  
  
 SCC_MSG_INFO  
 메시지는 정보 제공 용입니다.  
  
 SCC_MSG_WARNING  
 메시지는 경고입니다.  
  
 SCC_MSG_ERROR  
 메시지가 오류입니다.  
  
 SCC_MSG_STATUS  
 메시지는 상태 표시줄에 대 한 것입니다.  
  
 SCC_MSG_DOCANCEL  
 텍스트 없음 IDE는 `SCC_MSG_RTN_OK` 또는 `SCC_MSG_RTN_CANCEL` 를 반환 합니다.  
  
 SCC_MSG_STARTCANCEL  
 Cancel 루프를 시작 합니다.  
  
 SCC_MSG_STOPCANCEL  
 Cancel 루프를 중지 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
