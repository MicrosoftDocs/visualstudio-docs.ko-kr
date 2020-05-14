---
title: 우발적 속성 클래스 - 내부 구성원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6441cafcc34a06464061b41691ea5faa32fc359
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739106"
---
# <a name="contingentproperties-class---internal-members"></a>우발적속성 클래스 - 내부 멤버
개체에 대한 <xref:System.Threading.Tasks.Task> 추가 속성을 포함합니다.

 **네임스페이스:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib (mscorlib.dll)

 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없으므로 CIL(일반 중간 언어)으로 다음 구문이 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>멤버

### <a name="fields"></a>필드

|이름|설명|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|이 작업에 등록된 자식 작업 목록입니다.|

## <a name="remarks"></a>설명
 .NET Framework는 필요한 경우에만 이 클래스의 필드를 초기화합니다.

## <a name="see-also"></a>참조
- [.NET 프레임워크에 대한 병렬 확장 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
