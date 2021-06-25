---
description: 이 작업에 등록된 자식 작업의 목록입니다.
title: m_children 필드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 311ab164551e46fbe1c30b5a6045a7993a900a67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901372"
---
# <a name="m_children-field"></a>m_children 필드
이 작업에 등록된 자식 작업의 목록입니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib(mscorlib.dll) **

 .NET Framework 이 내부 멤버에 액세스할 수 없으므로 다음 구문은 CIL(공용 중간 언어)로 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>설명
 태스크가 실행되는 동안 태스크를 실행하는 스레드만 이 배열에 액세스해야 합니다.

 작업이 완료되면 다른 스레드는 아무 것도 추가하거나 제거하지 않는 한 이 필드에 액세스할 수 있습니다.

## <a name="see-also"></a>참조
- [ContingentProperties 클래스](../../extensibility/debugger/contingentproperties-class-internal-members.md)
