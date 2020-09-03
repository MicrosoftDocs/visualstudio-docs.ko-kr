---
title: BSTR_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e9859267cc26ec012852a1150e458c81383dfd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737711"
---
# <a name="bstr_array"></a>BSTR_ARRAY
문자열의 배열을 설명 하는 구조체입니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagBSTR_ARRAY {
    DWORD dwCount;
    BSTR* Members;
} BSTR_ARRAY;
```

```csharp
struct BSTR_ARRAY {
    DWORD    dwCount;
    string[] Members;
}
```

## <a name="members"></a>멤버
`dwCount`\
배열에 있는 문자열의 수 `Members` 입니다.

`Members`\
문자열 배열입니다.

## <a name="remarks"></a>설명
이 구조체는 [Enumpersistedports](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) 메서드에서 반환 됩니다.

 [C + + 전용] 를 사용 하 여 각 개별 문자열을 해제 해야 하며 배열을 사용 하 여 `SysFreeString` `Members` 배열을 해제 해야 합니다 `CoTaskMemFree` .

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
