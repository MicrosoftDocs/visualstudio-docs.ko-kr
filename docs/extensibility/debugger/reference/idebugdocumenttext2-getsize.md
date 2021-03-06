---
description: 문서의이 위치에 있는 텍스트의 크기를 검색 합니다.
title: 'IDebugDocumentText2:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9499af30f9e9139d0ff64fcf17695b7a4ad69c9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066336"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
문서의이 위치에 있는 텍스트의 크기를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

## <a name="parameters"></a>매개 변수
`pcNumLines`\
제한이 텍스트의 줄 수를 반환 합니다.

`pcNumChars`\
제한이 텍스트의 문자 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명

 [C + + 전용] 특정 값을 원하지 않는 경우 매개 변수에 대해 NULL을 전달 합니다.

 [C #만 해당] 두 매개 변수를 모두 지정 해야 합니다.

## <a name="see-also"></a>참조
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
