---
description: 이 메서드는 필드에 대 한 확장 정보를 가져옵니다.
title: 'IDebugField:: GetExtendedInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e17c824d2be7ff12e3e967b953e25359b650b1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077072"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
이 메서드는 필드에 대 한 확장 정보를 가져옵니다.

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
진행 반환 될 정보를 선택 합니다. 유효한 값은 다음과 같습니다.

|값|Description|
|-----------|-----------------|
|`guidConstantValue`|바이트 시퀀스에 해당 하는 값입니다.|
|`guidConstantType`|형식 시그니처 형식입니다.|

`prgBuffer`\
제한이 확장 정보를 반환 합니다.

`pdwLen`\
[in, out] 확장 정보의 크기 (바이트)를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 현재이 메서드는 상수의 형식 또는 값만 반환 합니다. 호출자는 `prgBuffer` COM의 `CoTaskMemFree` 함수 (c + +) 또는 <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c #)를 호출 하 여에서 반환 된 버퍼를 해제 해야 합니다.

## <a name="see-also"></a>참조
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
