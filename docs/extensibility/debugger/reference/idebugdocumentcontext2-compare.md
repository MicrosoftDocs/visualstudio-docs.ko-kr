---
title: 'IDebugDocumentContext2:: Compare | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731886"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
이 문서 컨텍스트를 지정 된 문서 컨텍스트의 배열과 비교 합니다.

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
진행 비교 유형을 지정 하는 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) 열거형의 값입니다.

`rgpDocContextSet`\
진행 비교할 문서 컨텍스트를 나타내는 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 개체의 배열입니다.

`dwDocContextSetLen`\
진행 비교할 문서 컨텍스트의 배열 길이입니다.

`pdwDocContext`\
제한이 `rgpDocContextSet` 비교를 만족 하는 첫 번째 문서 컨텍스트의 배열로 인덱스를 반환 합니다.

## <a name="return-value"></a>반환 값
 `S_OK`일치 하는 항목이 있으면를 반환 합니다. 일치 하는 `S_FALSE` 항목이 없으면를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 배열에 전달 된 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 개체는에서 호출 되는 개체를 구현 하는 동일한 디버그 엔진에 의해 구현 되어야 합니다. `IDebugDocumentContext2` 그렇지 않으면 비교가 유효 하지 않습니다.

## <a name="see-also"></a>추가 정보
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
