---
title: METADATA_TYPE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afe5ea128775c7be0e48035ab4c7e7d370c9d233
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714298"
---
# <a name="metadata_type"></a>METADATA_TYPE
이 구조는 메타데이터에서 가져온 필드 유형에 대한 정보를 지정합니다.

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
 기호가 온 응용 프로그램의 ID입니다. 이는 응용 프로그램의 인스턴스를 고유하게 식별하는 데 사용됩니다.

 `guidModule`\
 이 필드를 포함하는 모듈의 GUID입니다.

 `tokClass`\
 이 유형의 메타데이터 토큰 ID입니다.

 [C++] `_mdToken` 32 `typedef` 비트에 `int`대 한입니다.

## <a name="remarks"></a>설명
 이 구조는 `dwKind` `TYPE_INFO` 구조의 필드가 설정될 때 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 구조체에서 `TYPE_KIND_METADATA` 연합의 일부로 [나타납니다(dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 열거된 값).

 값은 `tokClass` 형식을 고유하게 식별하는 메타데이터 토큰입니다. 메타데이터 토큰 ID의 상위 비트를 해석하는 방법에 대한 `CorTokenType` 자세한 내용은 .NET Framework SDK의 corhdr.h 파일의 열거를 참조하십시오.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
