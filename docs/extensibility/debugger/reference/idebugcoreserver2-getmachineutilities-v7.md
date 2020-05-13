---
title: IDebugCoreServer2::GetMachineUtilities_V7 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79eba6889583f1dfa482dab107ad31eaaacdbcc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733145"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
이 메서드는 서버에 대 한 컴퓨터 유틸리티를 가져옵니다.

> [!NOTE]
> 이 메서드는 더 이상 사용되지[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 않습니다. `E_NOTIMPL` 그것은 역사적인 이유로 유지됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>매개 변수
`ppUtil`\
【아웃】 컴퓨터 `IDebugMDMUtil2_V7` 유틸리티 정보를 나타내는 인터페이스를 반환합니다.

## <a name="return-value"></a>Return Value
 메서드가 `E_NOTIMPL`구현되지 않음을 나타내는 항상 반환됩니다.

## <a name="remarks"></a>설명
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]이 `E_NOTIMPL` 메서드가 호출되는 경우 항상 반환됩니다.

## <a name="see-also"></a>참조
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
