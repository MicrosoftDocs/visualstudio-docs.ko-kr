---
description: 문서 위치가 지정 된 문서에 포함 되어 있는지 여부를 확인 합니다.
title: 'IDebugDocumentPosition2:: IsPositionInDocument | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab3d00df9883da93d0d8121433b962d365a408e3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066414"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
문서 위치가 지정 된 문서에 포함 되어 있는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsPositionInDocument( 
   IDebugDocument2* pDoc
);
```

```csharp
int IsPositionInDocument( 
   IDebugDocument2 pDoc
);
```

## <a name="parameters"></a>매개 변수
`pDoc`\
진행 포함 하는 문서 후보를 나타내는 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 주로 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스에서 중단점을 설정 하는 데 사용 됩니다. 문서가 로드 되 면 문서에이 위치가 포함 되어 있는지 여부를 확인 하기 위해 중단점 위치가 호출 됩니다.

## <a name="see-also"></a>참조
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
