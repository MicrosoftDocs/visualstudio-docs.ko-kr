---
title: m_children 필드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 749b7a8da2cbdf8377e7f2e1fcb39787e2f42303
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149056"
---
# <a name="m_children-field"></a>m_children 필드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 작업에 등록 된 자식 작업의 목록입니다.  
  
 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **어셈블리:** mscorlib (mscorlib.dll)  
  
 .NET Framework에서이 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>설명  
 태스크가 실행 되는 동안에는 작업을 실행 하는 스레드만이 배열에 액세스 해야 합니다.  
  
 작업이 완료 되 면 다른 스레드가이 필드에 아무것도 추가 하거나 제거 하지 않는 한이 필드에 액세스할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [ContingentProperties 클래스](../../extensibility/debugger/contingentproperties-class-internal-members.md)
