---
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b6756d574c36d6381b606be597ca0e54e7945763
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874358"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
실행의 특정 지점에 도달한 후 프로그램이 실행을 중지할 수 있는지 여부를 확인 하는 데 사용 됩니다.

## <a name="syntax"></a>구문

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>필드
`CANSTOP_ENTRYPOINT`\
지정 된 프로그램의 진입점을 지정 합니다.

`CANSTOP_STEPIN`\
함수를 한 단계씩 실행 하도록 지정 합니다.

## <a name="remarks"></a>설명
프로그램의 진입점에 도달 하거나 함수 또는 메서드를 한 단계씩 코드 실행 한 후에 중지할 수 있는 경우 [Getreason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) 메서드에 인수로 전달 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
