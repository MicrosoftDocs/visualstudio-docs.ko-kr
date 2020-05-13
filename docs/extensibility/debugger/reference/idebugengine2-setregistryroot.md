---
title: IDebugEngine2::세트레지스트리루트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beba304e846126b262c23c0fc8232f79de5fd794
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730878"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
디버그 엔진(DE)에 대한 레지스트리 루트를 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetRegistryRoot( 
   LPCOLESTR pszRegistryRoot
);
```

```csharp
int SetRegistryRoot( 
   string pszRegistryRoot
);
```

## <a name="parameters"></a>매개 변수
`pszRegistryRoot`\
【인】 사용할 레지스트리 루트입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드를 사용 하 여 DE 레지스트리 설정을 가져오는 데 사용 해야 하는 대체 레지스트리 루트를 지정할 수 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 있습니다. 예를 들어 "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp".

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
