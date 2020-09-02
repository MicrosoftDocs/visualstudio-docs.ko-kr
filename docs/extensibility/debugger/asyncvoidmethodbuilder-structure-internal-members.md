---
title: AsyncVoidMethodBuilder 구조-내부 멤버 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 866a53fae7bb2cc5325112b84d992da6f95af246
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739293"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder 구조-내부 멤버
이 항목에서는 클래스의 내부 멤버에 대해 설명 합니다 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> . 이 클래스에 대 한 일반 정보는 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 참조 항목을 참조 하세요.

 **네임스페이스:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **어셈블리:** mscorlib (mscorlib.dll)

 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>내부 멤버

|Name|설명|
|----------|-----------------|
|[ObjectIdForDebugger 속성](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|디버거에 대해이 작성기를 고유 하 게 식별 하는 데 사용할 수 있는 개체를 가져옵니다.|
|[m_objectIdForDebugger 필드](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|디버거에서이 작성기를 고유 하 게 식별 하는 데 사용 되는 지연 된 초기화 개체를 나타냅니다.|

## <a name="see-also"></a>추가 정보
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [.NET Framework에 대 한 병렬 확장 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
