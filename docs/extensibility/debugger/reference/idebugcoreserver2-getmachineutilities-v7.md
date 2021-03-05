---
description: 이 메서드는 서버에 대 한 컴퓨터 유틸리티를 가져옵니다.
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc58f41d9cca98f6c15c164ed4acb941345627e5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154771"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
이 메서드는 서버에 대 한 컴퓨터 유틸리티를 가져옵니다.

> [!NOTE]
> 이 메서드는 사용 되지 않습니다. 사용 안 함 ( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] `E_NOTIMPL` 이 메서드가 호출 될 경우 항상를 반환 함). 기록을 위해 보존 됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>매개 변수
`ppUtil`\
제한이 `IDebugMDMUtil2_V7` 컴퓨터 유틸리티 정보를 나타내는 인터페이스를 반환 합니다.

## <a name="return-value"></a>반환 값
 `E_NOTIMPL`메서드가 구현 되지 않음을 나타내는를 항상 반환 합니다.

## <a name="remarks"></a>설명
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]`E_NOTIMPL`이 메서드가 호출 되 면 항상를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
