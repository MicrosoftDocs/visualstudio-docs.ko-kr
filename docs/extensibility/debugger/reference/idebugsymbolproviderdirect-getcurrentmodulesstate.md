---
title: IDebug 기호공급자직접::GetCurrentModules상태 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719077"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesstate"></a>IDebugSymbolProviderDirect::GetCurrentModulesState
기호 공급자가 구성원인 기호 그룹에 대한 정보를 검색합니다.

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
【아웃】 기호 공급자 그룹의 상태입니다.

`count`\
【아웃】 그룹의 모듈 수입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 심볼 그룹에 모듈을 추가하거나 제거할 때마다 상태가 변경됩니다. 따라서 이 메서드를 사용하여 기호 그룹이 수정되었는지 검색할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
