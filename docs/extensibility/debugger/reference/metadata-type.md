---
description: METADATA_TYPE 구조는 메타 데이터에서 가져온 필드 형식에 대 한 정보를 지정 합니다.
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a76e051e146985338564d497323b6232b35a4a1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079854"
---
# <a name="metadata_type"></a>METADATA_TYPE
이 구조는 메타 데이터에서 가져온 필드 형식에 대 한 정보를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>매개 변수
 `ulAppDomainID`\
 기호를 가져온 응용 프로그램의 ID입니다. 이는 응용 프로그램의 인스턴스를 고유 하 게 식별 하는 데 사용 됩니다.

 `guidModule`\
 이 필드를 포함 하는 모듈의 GUID입니다.

 `tokClass`\
 이 형식의 메타 데이터 토큰 ID입니다.

 [C + +] `_mdToken` 는 `typedef` 32 비트에 대 한입니다 `int` .

## <a name="remarks"></a>설명
 이 구조체는 [](../../../extensibility/debugger/reference/type-info.md) `dwKind` 구조체의 필드가 `TYPE_INFO` `TYPE_KIND_METADATA` ( [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 열거형의 값)로 설정 된 경우 TYPE_INFO 구조체에서 합집합의 일부로 표시 됩니다.

 `tokClass`값은 형식을 고유 하 게 식별 하는 메타 데이터 토큰입니다. 메타 데이터 토큰 ID의 상위 비트를 해석 하는 방법에 대 한 자세한 내용은 `CorTokenType` .NET FRAMEWORK SDK의 corhdr .h 파일에서 열거형을 참조 하세요.

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
