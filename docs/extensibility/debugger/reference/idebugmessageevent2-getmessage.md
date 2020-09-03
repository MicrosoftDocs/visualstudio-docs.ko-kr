---
title: 'IDebugMessageEvent2:: GetMessage | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
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
제한이 메시지 형식을 설명 하는 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) 열거형의 값을 반환 합니다.

`pbstrMessage`\
제한이 메시지를 반환 합니다.

`pdwType`\
제한이 Win32 함수의 규칙을 사용 하 여 메시지 형식을 반환 합니다 `MessageBox` . 자세한 내용은 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) 함수를 참조 하세요.

`pbstrHelpFileName`\
[in, out] 도움말 파일 이름을 반환 합니다. 도움말 파일이 없으면 null (c + +) 이거나 비어 있는 (c #) 값일 수 있습니다.

`pdwHelpId`\
[in, out] 도움말 식별자를 반환 합니다. 이 메시지와 관련 된 도움말이 없으면 0이 될 수 있습니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
