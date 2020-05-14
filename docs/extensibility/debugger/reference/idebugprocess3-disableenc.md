---
title: 아이디버그프로세스3::D사용 가능ENC | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b39bb448501bacd5ab458b7e61bb1a5044bc8a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723740"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
이 메서드는 명시적으로 편집 및 이 프로세스에 계속 (그리고 포함 하는 모든 프로그램)를 사용 하지 않도록 설정 합니다. 사용자 지정 포트 공급자는 항상 반환해야 `E_NOTIMPL`합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>매개 변수
`reason`\
【인】 [EncUnavailable에서 값이유](../../../extensibility/debugger/reference/encunavailablereason.md) 열거.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

> [!NOTE]
> 사용자 지정 포트 공급자는 항상 반환해야 `E_NOTIMPL`합니다.

## <a name="remarks"></a>설명
 프로세스에 대해 편집 및 계속을 사용하지 않도록 설정하면 프로세스를 다시 시작해야만 다시 사용할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
