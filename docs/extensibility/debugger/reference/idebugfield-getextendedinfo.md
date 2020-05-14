---
title: 아이데버그필드::GetExtendedInfo | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc414dd57e86149e38d7c85d11252eb93efced51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728871"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
이 메서드는 필드에 대 한 확장 된 정보를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>매개 변수
`guidExtendedInfo`\
【인】 반환할 정보를 선택합니다. 유효한 값은 다음과 같습니다.

|값|Description|
|-----------|-----------------|
|`guidConstantValue`|바이트 시퀀스의 값입니다.|
|`guidConstantType`|형식 서명으로 입력합니다.|

`prgBuffer`\
【아웃】 확장 된 정보를 반환 합니다.

`pdwLen`\
【인, 아웃】 확장 된 정보의 크기를 바이트로 반환 합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 현재 이 메서드는 상수의 형식 또는 값만 반환합니다. 호출자는 COM의 `prgBuffer` `CoTaskMemFree` 함수(C++) 또는 <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#)를 호출하여 반환된 버퍼를 해제해야 합니다.

## <a name="see-also"></a>참조
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
