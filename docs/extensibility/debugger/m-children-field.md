---
title: m_children 필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07933fd4c9f359e72714600abdf8b4ee29268f84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738432"
---
# <a name="m_children-field"></a>m_children 필드
이 작업에 등록된 자식 작업 목록입니다.

 **네임스페이스:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **조립:** mscorlib *(mscorlib.dll)*

 .NET Framework에서 이 내부 멤버에 액세스할 수 없으므로 CIL(일반 중간 언어)에서 다음 구문이 제공됩니다.

## <a name="syntax"></a>구문

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>설명
 작업이 실행되는 동안 작업을 실행하는 스레드만 이 배열에 액세스해야 합니다.

 작업이 완료되면 다른 스레드는 이 필드에 아무 것도 추가하지 않거나 해당 필드에 아무 것도 제거하지 않는 한 이 필드에 액세스할 수 있습니다.

## <a name="see-also"></a>참조
- [우발적 속성 클래스](../../extensibility/debugger/contingentproperties-class-internal-members.md)
