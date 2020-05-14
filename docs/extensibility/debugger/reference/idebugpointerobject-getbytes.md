---
title: IDebugPointerObject::GetBytes | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17bc39f65d7c4c42b4f958b559df7c5b7d3bbdf7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725522"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
연속 바이트로 가리키는 값을 가져옵니다.

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
【인】 가리키는 개체의 시작 부분부터 바이트로 오프셋입니다.

`dwCount`\
【인】 검색할 바이트 수입니다.

`pBytes`\
【인, 아웃】 가리키는 개체에서 지정된 오프셋에서 시작하여 연속 바이트의 일련의 값으로 값이 채워진 배열입니다.

`pdwBytes`\
【아웃】 실제로 검색된 바이트 수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 [IDebugPointerObject로](../../../extensibility/debugger/reference/idebugpointerobject.md) 표시되는 포인터가 기본 형식 또는 기본 형식의 간단한 배열(즉, 간단한 바이트 시퀀스로 나타낼 수 있는 배열)을 가리키는 경우 이 메서드가 사용됩니다.

## <a name="see-also"></a>참조
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [설정수](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
