---
title: IDebugProgramNode2::GetHostMachineName_V7 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8c328c83ebe52f842b1990debe07aed3fd764c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722090"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> 되지 않는. 사용하지 마십시오.

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
【아웃】 프로그램이 실행 중인 컴퓨터의 이름을 반환합니다.

## <a name="return-value"></a>Return Value

구현은 항상 `E_NOTIMPL`반환되어야 합니다.

## <a name="remarks"></a>설명

> [!WARNING]
> Visual Studio 2005에서 이 메서드는 더 이상 `E_NOTIMPL`사용되지 않으며 항상 반환해야 합니다.

## <a name="see-also"></a>참조

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
