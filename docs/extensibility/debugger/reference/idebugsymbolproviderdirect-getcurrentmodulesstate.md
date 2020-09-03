---
title: 'Idebug심볼 Providerdirect:: GetCurrentModulesState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetCurrentModulesState
- IDebugSymbolProviderDirect::GetCurrentModulesState
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9e7cf711b5cf6823059945f85b9c3db30701ccf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719077"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesstate"></a>IDebugSymbolProviderDirect::GetCurrentModulesState
기호 공급자가 멤버인 기호 그룹에 대 한 정보를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCurrentModulesState(
    DWORD*          pState,
    unsigned long * count
);
```

```csharp
int GetCurrentModulesState(
    out uint pState,
    out uint count
);
```

## <a name="parameters"></a>매개 변수
`pState`\
제한이 기호 공급자 그룹의 상태입니다.

`count`\
제한이 그룹의 모듈 수입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 상태는 모듈이 기호 그룹에 추가 되거나 제거 될 때마다 변경 됩니다. 따라서이 메서드는 기호 그룹이 수정 되었는지 여부를 검색 하는 데 사용할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
