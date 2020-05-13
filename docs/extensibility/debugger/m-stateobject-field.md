---
title: m_stateObject 필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fed70f2eda19ad96454a83217c20c046809f3034
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738378"
---
# <a name="m_stateobject-field"></a>m_stateObject 필드
작업에서 사용할 데이터를 나타내는 개체입니다.

 **네임스페이스:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **조립:** mscorlib *(mscorlib.dll)*

 .NET Framework에서 이 내부 멤버에 액세스할 수 없으므로 CIL(일반 중간 언어)에서 다음 구문이 제공됩니다.

## <a name="syntax"></a>구문

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>설명
 생성자의 `state` 매개 변수입니다. <xref:System.Threading.Tasks.Task.%23ctor%2A> 또한 속성에 대 한 <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> 백업 필드입니다.

## <a name="see-also"></a>참조
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)
