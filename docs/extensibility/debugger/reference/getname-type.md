---
title: GETNAME_TYPE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d0d146ec4ed7340bde36b298df9d455257b35fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736666"
---
# <a name="getname_type"></a>GETNAME_TYPE
검색할 파일의 이름 유형을 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>필드
`GN_NAME`\
문서 또는 컨텍스트의 친숙한 이름을 지정합니다.

`GN_FILENAME`\
문서 또는 컨텍스트의 전체 경로를 지정합니다.

`GN_BASENAME`\
문서 또는 컨텍스트의 전체 경로 대신 기본 파일 이름을 지정합니다.

`GN_MONIKERNAME`\
모니커 의 형태로 문서 또는 컨텍스트의 고유한 이름을 지정합니다.

`GN_URL`\
문서 또는 컨텍스트의 URL 이름을 지정합니다.

`GN_TITLE`\
문서의 제목이 있는 경우 문서의 제목을 지정합니다.

`GN_STARTPAGEURL`\
프로세스의 시작 페이지 URL을 가져옵니다.

## <a name="remarks"></a>설명
이러한 값은 [GetName,](../../../extensibility/debugger/reference/idebugdocument2-getname.md) [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)및 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) 메서드에 매개 변수로 전달되어 반환할 이름의 종류를 지정합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
