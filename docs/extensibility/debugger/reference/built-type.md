---
description: BUILT_TYPE 구조는 메타 데이터에서 가져온 필드 형식에 대 한 정보를 지정 합니다.
title: BUILT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00a031d02bba7ffcc1dca6f2cf73cfceeed04838
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096579"
---
# <a name="built_type"></a>BUILT_TYPE
이 구조는 메타 데이터에서 가져온 필드 형식에 대 한 정보를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>멤버
`ulAppDomainID`\
기호를 가져온 응용 프로그램의 ID입니다. 이는 응용 프로그램의 인스턴스를 고유 하 게 식별 하는 데 사용 됩니다.

`guidModule`\
이 필드를 포함 하는 모듈의 GUID입니다.

`pUnderlyingField`\
이 작성 된 필드와 연결 된 기본 필드를 식별 하는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다.

## <a name="remarks"></a>설명
이 구조체는 [](../../../extensibility/debugger/reference/type-info.md) `dwKind` 구조체의 필드가 `TYPE_INFO` `TYPE_KIND_BUILT` ( [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 열거형의 값)로 설정 된 경우 TYPE_INFO 구조체에서 합집합의 일부로 표시 됩니다.

## <a name="requirements"></a>요구 사항
헤더: sh

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
