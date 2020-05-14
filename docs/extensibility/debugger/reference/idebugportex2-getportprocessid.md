---
title: 아이디버그포트엑스2::겟포트프로세스 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
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
【아웃】 포트 자체의 물리적 프로세스 ID를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 예를 들어 Win32 런타임에서 이 메서드는 일반적으로 `GetCurrentProcessId` Win32 함수를 호출하여 물리적 프로세스 ID를 가져옵니다.

## <a name="see-also"></a>참조
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
