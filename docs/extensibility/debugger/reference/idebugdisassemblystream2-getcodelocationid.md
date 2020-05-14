---
title: IDebugDisassemblyStream2::GetCodelocationId | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32be70e11776177a0e68f09689c2262497703ab1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732246"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
특정 코드 컨텍스트에 대한 코드 위치 식별자를 반환합니다.

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
【인】 식별자로 변환할 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체입니다.

`puCodeLocationId`【아웃】 코드 위치 식별자를 반환합니다. 설명 부분을 참조하세요.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 코드 `E_CODE_CONTEXT_OUT_OF_SCOPE` 컨텍스트가 유효하지만 범위를 벗어난 경우 반환합니다.

## <a name="remarks"></a>설명
 코드 위치 식별자는 분해를 지원하는 DE(디버그 엔진)에만 해당됩니다. 이 위치 식별자는 DE에서 내부적으로 코드의 위치를 추적하는 데 사용되며 일반적으로 일종의 주소 또는 오프셋입니다. 유일한 요구 사항은 한 위치의 코드 컨텍스트가 다른 위치의 코드 컨텍스트보다 작으면 첫 번째 코드 컨텍스트의 해당 코드 위치 식별자도 두 번째 코드 컨텍스트의 코드 위치 식별자보다 작아야 한다는 것입니다.

 코드 위치 식별자의 코드 컨텍스트를 검색하려면 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) 메서드를 호출합니다.

## <a name="see-also"></a>참조
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
