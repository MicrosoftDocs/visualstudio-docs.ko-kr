---
title: JMC_CODE_SPEC | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0a6746ed0df400efc7feb3fb541c57c88f78cc2c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714735"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
이 구조는 모듈에 대한 JustMyCode 정보를 설정하는 데 사용됩니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _JMC_CODE_SPEC {
    BOOL fIsUserCode;
    BSTR bstrModuleName;
} JMC_CODE_SPEC;
```

```csharp
public struct JMC_CODE_SPEC {
    public int    fIsUserCode;
    public string bstrModuleName;
};
```

## <a name="members"></a>멤버
`fIsUserCode`\
0이 아닌`TRUE`( ) 모듈이 사용자 코드로 간주되는 경우; 그렇지 않으면`FALSE`0 () 모듈을 외부 코드로 처리하고 디버깅하지 않는 경우.

`bstrModuleName`\
해당 모듈의 이름입니다.

## <a name="remarks"></a>설명
이 구조는 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) 메서드에 이러한 구조의 목록으로 전달 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
