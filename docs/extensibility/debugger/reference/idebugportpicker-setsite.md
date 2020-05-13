---
title: 아이데버그포트피커::세트사이트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 07dac3f407b6869dad90f06d778911fdd9cfed41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724863"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
서비스 공급자를 설정합니다.

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
【인】 서비스 공급자의 인터페이스에 대한 참조입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 다른 메서드를 호출하기 전에 호출됩니다.

## <a name="see-also"></a>참조
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
