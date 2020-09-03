---
title: 'IDebugEnumField:: GetUnderlyingSymbol | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 14cac9d3f761e95b821179137f2efc23ef61b91b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730276"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
이 메서드는 열거형의 이름을 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

## <a name="parameters"></a>매개 변수
`ppField`\
제한이 이 열거형의 이름을 설명 하는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 열거형의 이름에는 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)를 사용 하 여 메모리 위치에 바인딩된 열거형의 형식도 포함 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [바인딩하며](../../../extensibility/debugger/reference/idebugbinder-bind.md)
