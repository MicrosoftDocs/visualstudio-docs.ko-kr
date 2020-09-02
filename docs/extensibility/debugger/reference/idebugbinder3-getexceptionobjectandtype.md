---
title: 'IDebugBinder3:: GetExceptionObjectAndType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e25a0f7b4e1713a072359f1efdd962f36c50b774
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735744"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
이 메서드는 개체와 연결 된 예외를 검색 합니다 (있는 경우).

## <a name="syntax"></a>구문

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>매개 변수
`ppException`\
제한이 예외를 나타내는 개체를 반환 합니다.

`ppField`\
제한이 예외를 발생 시킬 수 있는 특정 필드를 나타내는 개체를 반환 합니다 .이 개체는 null 값일 수 있습니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

> [!NOTE]
> 예외가 있는지 확인 하려면에서 반환 하는 값을 확인 합니다 `ppException` . null 값인 경우에는이 개체와 관련 된 예외가 없습니다.

## <a name="see-also"></a>추가 정보
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
