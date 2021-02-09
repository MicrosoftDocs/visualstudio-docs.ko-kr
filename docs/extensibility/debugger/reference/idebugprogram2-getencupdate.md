---
title: 'IDebugProgram2:: GetENCUpdate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7e3dbb0fdc7ea7ca7560f62bc7da45e57b24383
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878905"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
이 메서드는이 프로그램에 대 한 편집 하며 계속 하기 (ENC) 업데이트를 가져옵니다. 사용자 지정 디버그 엔진은 항상를 반환 `E_NOTIMPL` 합니다.

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
제한이 이 프로그램을 업데이트 하는 데 사용할 수 있는 내부 인터페이스를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

> [!NOTE]
> 사용자 지정 디버그 엔진은 항상를 반환 해야 합니다 `E_NOTIMPL` .

## <a name="see-also"></a>참고 항목
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
