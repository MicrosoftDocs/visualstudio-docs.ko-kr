---
description: 이 디버그 이벤트의 특성을 가져옵니다.
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7402c2b5a367a3a0a681a9a17ef89872a7b3e96
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152977"
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

## <a name="see-also"></a>참고 항목
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
