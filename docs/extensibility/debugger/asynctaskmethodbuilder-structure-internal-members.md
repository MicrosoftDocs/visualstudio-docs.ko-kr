---
description: 이 문서에서는 AsyncTaskMethodBuilder 클래스의 내부 멤버에 대해 설명 합니다. System.runtime.compilerservices.
title: AsyncTaskMethodBuilder 구조 - 내부 멤버
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 241b4f3aae50ac70afc8320b637535035ee427e2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145692"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder 구조-내부 멤버
이 항목에서는 클래스의 내부 멤버에 대해 설명 합니다 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> . 이 클래스에 대 한 일반 정보는 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> 참조 항목을 참조 하세요.

 **네임스페이스:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **어셈블리:** mscorlib (mscorlib.dll)

 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>내부 멤버

|Name|설명|
|----------|-----------------|
|[ObjectIdForDebugger 속성](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|디버거에 대해이 작성기를 고유 하 게 식별 하는 데 사용할 수 있는 개체를 가져옵니다.|
|[m_builder 필드](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|이 제네릭이 아닌 인스턴스가 위임 하는 제네릭 작성기 개체를 나타냅니다.|

## <a name="see-also"></a>참고 항목
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [.NET Framework에 대 한 병렬 확장 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
