---
title: 'IDebugProgramNode2:: GetHostMachineName_V7 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 843e5fdf91fe817681b95422474d3887de5756b0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898615"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> Mapi. 사용 하지 마십시오.

## <a name="syntax"></a>구문

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>매개 변수

`pbstrHostMachineName`\
제한이 프로그램이 실행 되 고 있는 컴퓨터의 이름을 반환 합니다.

## <a name="return-value"></a>Return Value

구현은 항상를 반환 해야 `E_NOTIMPL` 합니다.

## <a name="remarks"></a>설명

> [!WARNING]
> Visual Studio 2005을 사용 하 여이 메서드는 더 이상 사용 되지 않으며 항상를 반환 해야 `E_NOTIMPL` 합니다.

## <a name="see-also"></a>참고 항목

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
