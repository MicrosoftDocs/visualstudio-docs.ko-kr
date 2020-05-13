---
title: 엔크언사용할수이유 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28863549ab3eac96322530bc85c52697f20448c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737163"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`편집 및 **계속을** 사용할 수 없는 이유를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

## <a name="fields"></a>필드
`ENCUN_NONE`\
편집 및 계속을 사용할 수 없는 특별한 이유는 없습니다.

`ENCUN_INTEROP`\
InterOp 호출 중에 편집 및 계속을 사용할 수 없습니다.

`ENCUN_SQLCLR`\
CLR(공통 언어 런타임)을 사용하는 SQL 프로시저 호출 중에 편집 및 계속을 사용할 수 없습니다.

`ENCUN_MINIDUMP`\
미니 덤프를 처리하는 동안편집 및 계속을 사용할 수 없습니다.

`ENCUN_EMBEDDED`\
포함된 코드를 처리할 때 편집 및 계속을 사용할 수 없습니다.

`ENCUN_ATTACH`\
세션이 디버거에 의해 시작되지 않고 연결되었기 때문에 편집 및 계속을 사용할 수 없습니다.

`ENCUN_WIN64`\
64비트 Windows 코드를 처리하는 동안편집 및 계속을 사용할 수 없습니다.

## <a name="remarks"></a>설명
이 열거형은 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]에서만 내부용입니다. 사용자 지정 포트 공급자가 구현한 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) 및 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) 메서드는 항상 반환해야 `E_NOTIMPL`합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.idl

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
