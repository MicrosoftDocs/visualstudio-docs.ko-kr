---
description: 문서 컨텍스트를 지정 된 수의 문이나 줄로 이동 합니다.
title: 'IDebugDocumentContext2:: Seek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9fcc430102ec974f2492a8e65894faa45978693
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066557"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
문서 컨텍스트를 지정 된 수의 문이나 줄로 이동 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Seek( 
   int                      nCount,
   IDebugDocumentContext2** ppDocContext
);
```

```cpp
int Seek( 
   int                        nCount,
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>매개 변수
`nCount`\
진행 문서 컨텍스트에 따라 앞으로 이동할 문이나 줄의 수입니다.

`ppDocContext`\
제한이 새 위치를 사용 하 여 새 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
