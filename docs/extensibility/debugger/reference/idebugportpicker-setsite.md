---
description: 서비스 공급자를 설정 합니다.
title: 'IDebugPortPicker:: SetSite | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d1c222bd06a974e7f2b1a57096a120399b554b82
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169277"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
서비스 공급자를 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

## <a name="parameters"></a>매개 변수
`pSP`\
진행 서비스 공급자의 인터페이스에 대 한 참조입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 다른 메서드를 호출 하기 전에 호출 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
