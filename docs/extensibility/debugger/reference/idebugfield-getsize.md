---
description: 이 메서드는 필드의 크기 (바이트)를 가져옵니다.
title: 'IDebugField:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c588914f93d732dc1b8e6ddc4edc41713e97fd1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151898"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
이 메서드는 필드의 크기 (바이트)를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSize( 
   DWORD* pdwSize
);
```

```csharp
int GetSize(
   out uint pdwSize
);
```

## <a name="parameters"></a>매개 변수
`pdwSize`\
제한이 크기를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 모든 필드에는 형식이 있으며 모든 형식에는 크기가 있습니다. 예를 들어 byte 형식의 필드는 크기가 1 바이트입니다.

## <a name="see-also"></a>참고 항목
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
