---
title: 아이디버그프로그램2::GetENCUpdate | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e90ff9f8a7a80913aec72b9fe2bb6fe470013d51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722841"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
이 메서드는 이 프로그램에 대한 ENC(편집 및 계속) 업데이트를 가져옵니다. 사용자 지정 디버그 `E_NOTIMPL`엔진은 항상 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>매개 변수
`ppUpdate`\
【아웃】 이 프로그램을 업데이트하는 데 사용할 수 있는 내부 인터페이스를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

> [!NOTE]
> 사용자 지정 디버그 엔진은 항상 반환해야 `E_NOTIMPL`합니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
