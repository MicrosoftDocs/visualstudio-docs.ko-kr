---
description: 연속 되는 일련의 바이트로 가리키는 값을 가져옵니다.
title: 'IDebugPointerObject:: GetBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a150f819610de97ee292302d89e2007c6235aae
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087628"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
연속 되는 일련의 바이트로 가리키는 값을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>매개 변수
`dwStart`\
진행 가 가리키는 개체의 시작 부분에서의 오프셋 (바이트)입니다.

`dwCount`\
진행 검색할 바이트 수입니다.

`pBytes`\
[in, out] 값을 가리키는 개체의 지정 된 오프셋에서 시작 하 여 일련의 연속 바이트로 채워진 배열입니다.

`pdwBytes`\
제한이 실제로 검색 된 바이트 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는이 [Idebugpointerobject](../../../extensibility/debugger/reference/idebugpointerobject.md) 가 나타내는 포인터가 기본 형식 또는 기본 형식의 간단한 배열 (즉, 단순 바이트 시퀀스로 표현할 수 있는 배열)을 가리키는 경우에 사용 됩니다.

## <a name="see-also"></a>참조
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
