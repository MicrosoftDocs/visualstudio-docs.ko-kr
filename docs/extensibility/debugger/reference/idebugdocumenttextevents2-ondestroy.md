---
title: 'IDebugDocumentTextEvents2:: onDestroy | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnDestroy
helpviewer_keywords:
- IDebugDocumentTextEvents2::onDestroy
ms.assetid: 60e4689c-c899-4c14-9d18-96393b741e1f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 791ed47d09d44713f4586d79ac2a1655ea0bb94b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99848184"
---
# <a name="idebugdocumenttextevents2ondestroy"></a>IDebugDocumentTextEvents2::onDestroy
전체 문서가 소멸 되었음을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
HRESULT onDestroy( 
   void 
);
```

```csharp
int onDestroy();
```

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
