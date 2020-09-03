---
title: 'IDebugPointerObject:: SetBytes | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725506"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
연속 된 일련의 바이트에서 가리키는 값을 설정 합니다.

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
진행 가 가리키는 개체의 시작 부분에서의 오프셋 (바이트)입니다.

`dwCount`\
진행 설정할 바이트 수입니다.

`pBytes`\
진행 새 값을 나타내는 바이트 배열입니다. 이 값은 지정 된 오프셋에서 시작 하 여 개체에 저장 됩니다.

`pdwBytes`\
제한이 실제로 설정 된 바이트 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는이 [Idebugpointerobject](../../../extensibility/debugger/reference/idebugpointerobject.md) 가 나타내는 포인터가 기본 형식 또는 기본 형식의 간단한 배열 (즉, 단순 바이트 시퀀스로 표현할 수 있는 배열)을 가리키는 경우에 사용 됩니다. 이 `IDebugPointerObject` 개체는 null 참조일 수 없습니다 (메모리의 주소를 가리켜야 함).

## <a name="see-also"></a>추가 정보
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
