---
title: IDebugDocument컨텍스트2:비교 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0e46f765c8e4c0e12c3bb9447e0713919fae7b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731886"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
이 문서 컨텍스트를 지정된 문서 컨텍스트 배열과 비교합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

## <a name="parameters"></a>매개 변수
`compare`\
【인】 비교 유형을 지정하는 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) 열거형의 값입니다.

`rgpDocContextSet`\
【인】 비교되는 문서 컨텍스트를 나타내는 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 개체의 배열입니다.

`dwDocContextSetLen`\
【인】 비교할 문서 컨텍스트 배열의 길이입니다.

`pdwDocContext`\
【아웃】 인덱스를 비교를 `rgpDocContextSet` 제공하는 첫 번째 문서 컨텍스트의 배열로 반환합니다.

## <a name="return-value"></a>Return Value
 일치하는 `S_OK` 일치가 발견되면 반환합니다. 일치하는 `S_FALSE` 일치를 찾을 수 없는 경우 반환합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 배열에 전달되는 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 개체는 호출되는 `IDebugDocumentContext2` 개체를 구현하는 동일한 디버그 엔진에 의해 구현되어야 합니다. 그렇지 않으면 비교가 잘못되었습니다.

## <a name="see-also"></a>참조
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
