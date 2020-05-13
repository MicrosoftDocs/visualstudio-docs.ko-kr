---
title: IDebugMessageEvent2::GetMessage | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 819b796a656f0ef8775fbb1c9e800e3019b81729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727407"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
표시할 메시지를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMessage( 
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrMessage,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetMessage( 
   out enum_MESSAGETYPE pMessageType,
   out string           pbstrMessage,
   out uint             pdwType,
   out string           pbstrHelpFileName,
   out uint             dwHelpId
);
```

## <a name="parameters"></a>매개 변수
`pMessageType`\
【아웃】 [메시지 유형형식을](../../../extensibility/debugger/reference/messagetype.md) 설명하는 MESSAGETYPE 열거형에서 값을 반환합니다.

`pbstrMessage`\
【아웃】 메시지를 반환합니다.

`pdwType`\
【아웃】 Win32 `MessageBox` 함수의 규칙을 사용하여 메시지 형식을 반환합니다. 자세한 내용은 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) 기능을 참조하십시오.

`pbstrHelpFileName`\
【인, 아웃】 도움말 파일 이름을 반환합니다. 도움말 파일이 없는 경우 null(C++) 또는 빈(C#) 값일 수 있습니다.

`pdwHelpId`\
【인, 아웃】 도움말 식별자를 반환합니다. 이 메시지와 관련된 도움이 없는 경우 0일 수 있습니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [메시지 유형](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
