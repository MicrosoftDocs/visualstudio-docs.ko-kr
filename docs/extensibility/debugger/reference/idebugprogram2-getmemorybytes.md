---
title: 'IDebugProgram2:: GetMemoryBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetMemoryBytes
helpviewer_keywords:
- IDebugProgram2::GetMemoryBytes
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cc0be42ace78dbd46fd64ce42f446a9449998b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722816"
---
# <a name="idebugprogram2getmemorybytes"></a>IDebugProgram2::GetMemoryBytes
프로그램이 차지 하는 메모리 바이트를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMemoryBytes( 
   IDebugMemoryBytes2** ppMemoryBytes
);
```

```csharp
int GetMemoryBytes( 
   out IDebugMemoryBytes2 ppMemoryBytes
);
```

## <a name="parameters"></a>매개 변수
`ppMemoryBytes`\
제한이 프로그램의 메모리 바이트를 나타내는 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) 개체로 표시 되는 메모리 바이트는 프로그램을 실행할 때 할당 된 메모리가 아닌 메모리의 프로그램 이미지에 대 한 것입니다.

## <a name="see-also"></a>추가 정보
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
