---
description: 디버그 엔진 (DE)의 레지스트리 루트를 설정 합니다.
title: 'IDebugEngine2:: SetRegistryRoot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01d43d2891b4ffb6257dfe0a367971022ebb1f99
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153900"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
디버그 엔진 (DE)의 레지스트리 루트를 설정 합니다.

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
진행 사용할 레지스트리 루트입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는를 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 사용 하 여 레지스트리 설정을 가져오는 데 사용 하는 대체 레지스트리 루트를 지정할 수 있습니다 (예: "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp").

## <a name="see-also"></a>참고 항목
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
