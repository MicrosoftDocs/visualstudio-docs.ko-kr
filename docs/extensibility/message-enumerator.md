---
title: 메시지 열거자 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e09b72bd228839268cffc228dd0dc503cc82bd9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702502"
---
# <a name="message-enumerator"></a>메시지 열거자
다음 플래그는 IDE가 `TEXTOUTPROC` [SccOpenProject를](../extensibility/sccopenproject-function.md) 호출할 때 제공하는 콜백 함수인 함수에 사용됩니다(콜백 함수에 대한 자세한 내용은 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) 참조).

 IDE가 프로세스를 취소하라는 메시지가 지정되면 취소 메시지 중 하나가 나타날 수 있습니다. 이 경우 소스 제어 플러그인은 `SCC_MSG_STARTCANCEL` IDE에 **취소** 단추를 표시하도록 요청하는 데 사용합니다. 이 후에는 모든 일반 메시지 집합을 보낼 수 있습니다. 이러한 반환 `SCC_MSG_RTN_CANCEL`중 어느 한 개가 있으면 플러그인이 작업을 종료하고 반환합니다. 또한 플러그인은 사용자가 `SCC_MSG_DOCANCEL` 작업을 취소했는지 확인하기 위해 주기적으로 폴링을 수행합니다. 모든 작업이 완료되거나 사용자가 취소한 경우 플러그인이 전송됩니다. `SCC_MSG_STOPCANCEL` SCC_MSG_WARNING `SCC_MSG_INFO`및 SCC_MSG_ERROR 유형은 메시지 스크롤 목록에 표시되는 메시지에 사용됩니다. `SCC_MSG_STATUS`은 텍스트가 상태 표시줄 또는 임시 표시 영역에 표시되어야 한다는 것을 나타내는 특수 형식입니다. 목록에 영구적으로 남아 있지 않습니다.

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
 SCC_MSG_RTN_CANCEL 콜백에서 취소를 나타내기 위해 반환합니다.

 SCC_MSG_RTN_OK 콜백에서 계속합니다.

 SCC_MSG_INFO 메시지는 정보입니다.

 SCC_MSG_WARNING 메시지는 경고입니다.

 SCC_MSG_ERROR 메시지는 오류입니다.

 SCC_MSG_STATUS 메시지는 상태 표시줄에 대한 것입니다.

 SCC_MSG_DOCANCEL 텍스트 없음; IDE `SCC_MSG_RTN_OK` 반환 `SCC_MSG_RTN_CANCEL`또는 .

 SCC_MSG_STARTCANCEL 취소 루프를 시작합니다.

 SCC_MSG_STOPCANCEL 취소 루프를 중지합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
