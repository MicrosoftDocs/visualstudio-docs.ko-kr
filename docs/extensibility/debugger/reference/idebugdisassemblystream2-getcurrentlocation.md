---
title: 'IDebugDisassemblyStream2:: GetCurrentLocation | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
ms.assetid: 512302f1-12b1-4107-8a6e-c5bc878ce1c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 440afc26688522da5cc8b6c20b2712872b4ce6b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732229"
---
# <a name="idebugdisassemblystream2getcurrentlocation"></a>IDebugDisassemblyStream2::GetCurrentLocation
현재 코드 위치를 나타내는 코드 위치 식별자를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCurrentLocation( 
   UINT64* puCodeLocationId
);
```

```csharp
int GetCurrentLocation( 
   out ulong puCodeLocationId
);
```

## <a name="parameters"></a>매개 변수
`puCodeLocationId`\
제한이 코드 위치 식별자를 반환 합니다. 코드 위치 식별자에 대 한 설명은 [Getcodelocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) 메서드에 대 한 설명 섹션을 참조 하세요.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) 메서드를 호출 하 여 코드 위치 식별자를 코드 컨텍스트로 변환할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
