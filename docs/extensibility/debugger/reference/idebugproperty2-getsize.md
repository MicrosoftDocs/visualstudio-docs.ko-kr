---
title: 아이디버그프로퍼티2:겟사이즈 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f57a742bae0217493d8869b257e4a17839e4e14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721335"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
속성 값의 크기를 바이트로 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

## <a name="parameters"></a>매개 변수
`pdwSize`\
【아웃】 속성 값의 크기를 바이트로 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 속성에 크기가 없는 경우 반환합니다. `S_GETSIZE_NO_SIZE`

## <a name="see-also"></a>참조
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
