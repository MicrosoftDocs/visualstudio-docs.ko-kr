---
description: 특정 코드 컨텍스트의 코드 위치 식별자를 반환 합니다.
title: 'IDebugDisassemblyStream2:: GetCodeLocationId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f68ee6ff0495fe36d8de8ccf0e3c2c81f3d05ac5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067090"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
특정 코드 컨텍스트의 코드 위치 식별자를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>매개 변수
`pCodeContext`\
진행 식별자로 변환할 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체입니다.

`puCodeLocationId` 제한이 코드 위치 식별자를 반환 합니다. 설명 부분을 참조하세요.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `E_CODE_CONTEXT_OUT_OF_SCOPE`코드 컨텍스트가 유효 하지만 범위 밖에 있는 경우를 반환 합니다.

## <a name="remarks"></a>설명
 코드 위치 식별자는 디스어셈블리를 지 원하는 디버그 엔진 (DE)에 특정 합니다. 이 위치 식별자는 코드의 위치를 추적 하기 위해 DE에서 내부적으로 사용 되며, 일반적으로 특정 종류의 주소 또는 오프셋입니다. 유일한 요구 사항은 한 위치의 코드 컨텍스트가 다른 위치의 코드 컨텍스트 보다 작은 경우 첫 번째 코드 컨텍스트의 해당 코드 위치 식별자도 두 번째 코드 컨텍스트의 코드 위치 식별자 보다 작아야 한다는 것입니다.

 코드 위치 식별자의 코드 컨텍스트를 검색 하려면 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
