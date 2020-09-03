---
title: 'IDebugPortEx2:: GetPortProcessId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae974461e312c68e6fcc14150a08879ac7709950
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725144"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
포트 자체의 프로세스 ID를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPortProcessId ( 
   DWORD* pdwProcessId
);
```

```csharp
int GetPortProcessId ( 
   out uint pdwProcessId
);
```

## <a name="parameters"></a>매개 변수
`pdwProcessId`\
제한이 포트 자체의 실제 프로세스 ID를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 Win32 런타임에서 예를 들어이 메서드는 일반적으로 Win32 함수를 호출 `GetCurrentProcessId` 하 여 실제 프로세스 ID를 가져옵니다.

## <a name="see-also"></a>추가 정보
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
