---
title: 아이디버그문서텍스트2:겟사이즈 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edc4a209537ca4bd54d3f6d9343d1496ab7c0e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731585"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
문서의 이 위치에서 텍스트 크기를 검색합니다.

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
【아웃】 텍스트 줄 수를 반환합니다.

`pcNumChars`\
【아웃】 텍스트 의 문자 수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명

 [C++ 전용] 특정 값이 필요하지 않은 경우 매개 변수에 대해 NULL을 전달합니다.

 [C# 만] 두 매개 변수를 모두 지정해야 합니다.

## <a name="see-also"></a>참조
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
