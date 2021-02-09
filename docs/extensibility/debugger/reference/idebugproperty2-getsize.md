---
title: 'IDebugProperty2:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af31a88859f2afba735e0696124076eb82068404
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850909"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
속성 값의 크기 (바이트)를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

## <a name="parameters"></a>매개 변수
`pdwSize`\
제한이 속성 값의 크기 (바이트)를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `S_GETSIZE_NO_SIZE`속성에 크기가 없으면를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
