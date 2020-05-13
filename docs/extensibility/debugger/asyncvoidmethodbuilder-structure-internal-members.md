---
title: 비동기 보이드 메소드 빌더 구조 - 내부 구성원 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739293"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>비동기 메서드빌더 구조 - 내부 멤버
이 항목에서는 클래스의 내부 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 멤버에 대해 설명합니다. 이 클래스에 대한 일반적인 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 정보는 참조 항목을 참조하십시오.

 **네임스페이스:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **어셈블리:** mscorlib (mscorlib.dll)

 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없으므로 CIL(일반 중간 언어)으로 다음 구문이 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>내부 구성원

|이름|설명|
|----------|-----------------|
|[ObjectIdForDebugger 속성](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|디버거에 이 빌더를 고유하게 식별하는 데 사용할 수 있는 개체를 가져옵니다.|
|[m_objectIdForDebugger 필드](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|디버거가 이 빌더를 고유하게 식별하는 데 사용하는 게으른 초기화 개체를 나타냅니다.|

## <a name="see-also"></a>참조
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [.NET 프레임워크에 대한 병렬 확장 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
