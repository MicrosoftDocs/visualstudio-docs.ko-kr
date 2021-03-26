---
description: 서비스 공급자를 설정 합니다.
title: 'IDebugPortPicker:: SetSite | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a442c438f233187265c90e724f57e8681b95556
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072262"
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

## <a name="see-also"></a>참조
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
