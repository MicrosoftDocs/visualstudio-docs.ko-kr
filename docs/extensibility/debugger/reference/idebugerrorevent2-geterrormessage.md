---
title: IDebugErrorEvent2::GetErrorMessage | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730036"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
사람이 읽을 수 있는 오류 메시지를 생성할 수 있는 정보를 반환합니다.

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
【아웃】 메시지 유형 형식을 설명하는 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) 열거형에서 값을 반환합니다.

`pbstrErrorFormat`\
【아웃】 사용자에게 보내는 최종 메시지의 형식입니다(자세한 내용은 "비고"참조).

`hrErrorReason`\
【아웃】 메시지의 오류 코드입니다.

`pdwType`\
【아웃】 오류의 심각도(예를 들어 `MessageBox`MB_XXX 상수 `MB_EXCLAMATION` 사용 `MB_WARNING`또는).

`pbstrHelpFileName`\
【아웃】 도움말 파일에 대한 경로(도움말 파일이 없는 경우 null 값으로 설정).

`pdwHelpId`\
【아웃】 표시할 도움말 항목의 ID입니다(도움말 항목이 없는 경우 0으로 설정).

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 오류 메시지는 의 `"What I was doing.  %1"`줄을 따라 서식을 지정해야 합니다. 그런 `"%1"` 다음 호출자는 오류 코드에서 파생된 오류 메시지(에서 `hrErrorReason`반환됨)로 대체됩니다. 매개 `pMessageType` 변수는 호출자에게 최종 오류 메시지를 표시하는 방법을 알려줍니다.

## <a name="see-also"></a>참조
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [메시지 유형](../../../extensibility/debugger/reference/messagetype.md)
