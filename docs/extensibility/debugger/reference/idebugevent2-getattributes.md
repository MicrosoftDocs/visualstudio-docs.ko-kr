---
title: 'IDebugEvent2:: GetAttributes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ffc3fc1b7988401611190fdf09e8041bf0dc5b1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729950"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
이 디버그 이벤트의 특성을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

## <a name="parameters"></a>매개 변수
`pdwAttrib`\
제한이 [Eventattributes](../../../extensibility/debugger/reference/eventattributes.md) 열거형의 플래그 조합입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 모든 이벤트에 공통적입니다. 이 메서드는 이벤트의 형식을 설명 합니다. 예를 들어는 이벤트 동기 또는 비동기 이며 이벤트를 중지 하는 이벤트입니다.

## <a name="see-also"></a>추가 정보
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
