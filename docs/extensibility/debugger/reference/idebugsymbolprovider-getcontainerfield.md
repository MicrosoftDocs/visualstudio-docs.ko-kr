---
title: 'Idebug Provider:: GetContainerField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetContainerField
helpviewer_keywords:
- IDebugSymbolProvider::GetContainerField method
ms.assetid: d6b56b4f-a96b-4fa7-87c1-bac4e58fa766
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 729457fd071ab4a271f46b159e031fdc5cfc19bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719389"
---
# <a name="idebugsymbolprovidergetcontainerfield"></a>IDebugSymbolProvider::GetContainerField
이 메서드는 디버그 주소를 포함 하는 필드를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetContainerField( 
   IDebugAddress*         pAddress,
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainerField(
   IDebugAddress            pAddress,
   out IDebugContainerField ppContainerField
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
진행 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스로 표시 되는 주소입니다.

`ppContainerField`\
제한이 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스가 나타내는 컨테이너 필드를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
