---
title: 'IDebugDocument2:: GetDocumentClassID | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71683c91082f477da530ec1be1fdc7627d6a7635
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732034"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
문서의 클래스 식별자를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDocumentClassID( 
   CLSID* pclsid
);
```

```csharp
int GetDocumentClassID( 
   out Guid pclsid
);
```

## <a name="parameters"></a>매개 변수
`pclsid` 제한이 문서의 클래스 ID 인 GUID를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 클래스 GUID는 각각 문서를 나타내는 개별 클래스를 인스턴스화하는 데 사용할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
