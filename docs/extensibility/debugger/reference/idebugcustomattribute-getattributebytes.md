---
title: IDebug사용자 속성::GetAttribute바이트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 621ebf3949a273e06053ced67209aa052c25bce0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732803"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
특성 정보를 바이트 의 Blob로 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>매개 변수
`ppBlob`\
【인, 아웃】 특성 바이트로 채워진 배열입니다.

`pdwLen`\
【인, 아웃】 `ppBlob` 배열에서 반환할 최대 바이트 수를 지정하고 실제로 배열에 기록된 바이트 수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 `ppBlob` 사용 가능한 특성 바이트 수를 반환하려면 매개 변수를 null 값으로 설정합니다. 그런 다음 배열을 할당하고 매개 `ppBlob` 변수에 대해 해당 배열을 전달합니다.

 특성 바이트는 사용자 지정 특성의 원시 데이터를 나타냅니다.

## <a name="see-also"></a>참조
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
