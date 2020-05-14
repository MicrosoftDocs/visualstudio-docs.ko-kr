---
title: 아이디버그포인터오브젝트::세트바이트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dede3ee5291afbfbeab4d6e60dcbd56e205e4526
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725506"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
일련의 연속 바이트에서 가리키는 값을 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>매개 변수
`dwStart`\
【인】 가리키는 개체의 시작 부분부터 바이트로 오프셋입니다.

`dwCount`\
【인】 설정할 바이트 수입니다.

`pBytes`\
【인】 새 값을 나타내는 바이트 배열입니다. 이 값은 지정된 오프셋에서 시작하여 개체에 저장됩니다.

`pdwBytes`\
【아웃】 실제로 설정된 바이트 수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 [IDebugPointerObject로](../../../extensibility/debugger/reference/idebugpointerobject.md) 표시되는 포인터가 기본 형식 또는 기본 형식의 간단한 배열(즉, 간단한 바이트 시퀀스로 나타낼 수 있는 배열)을 가리키는 경우 이 메서드가 사용됩니다. 이 `IDebugPointerObject` 개체는 null 참조일 수 없습니다(메모리의 주소를 가리가야 합니다).

## <a name="see-also"></a>참조
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
