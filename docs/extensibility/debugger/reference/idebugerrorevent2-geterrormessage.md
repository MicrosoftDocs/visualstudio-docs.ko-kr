---
title: 'IDebugErrorEvent2:: GetErrorMessage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ff1da2f2a2d24b958a613e6fe5cb58c0081ed3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730036"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
사람이 읽을 수 있는 오류 메시지를 생성할 수 있는 정보를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>매개 변수
`pMessageType`\
제한이 메시지 형식을 설명 하는 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) 열거형의 값을 반환 합니다.

`pbstrErrorFormat`\
제한이 사용자에 대 한 최종 메시지의 형식입니다. 자세한 내용은 "주의"를 참조 하십시오.

`hrErrorReason`\
제한이 메시지에 대 한 오류 코드입니다.

`pdwType`\
제한이 오류의 심각도입니다 (예 `MessageBox` : 또는) .의 경우에는 MB_XXX 상수를 사용 `MB_EXCLAMATION` `MB_WARNING` 합니다.

`pbstrHelpFileName`\
제한이 도움말 파일의 경로입니다. 도움말 파일이 없으면 null 값으로 설정 됩니다.

`pdwHelpId`\
제한이 표시할 도움말 항목의 ID입니다 (도움말 항목이 없으면 0으로 설정 됨).

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 오류 메시지는의 줄을 따라 포맷 해야 합니다 `"What I was doing.  %1"` . `"%1"`그런 다음는 오류 코드 (에서 반환 됨)에서 파생 된 오류 메시지와 함께 호출자에 의해 대체 됩니다 `hrErrorReason` . `pMessageType`매개 변수는 최종 오류 메시지를 표시 하는 방법을 호출자에 게 알립니다.

## <a name="see-also"></a>추가 정보
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
