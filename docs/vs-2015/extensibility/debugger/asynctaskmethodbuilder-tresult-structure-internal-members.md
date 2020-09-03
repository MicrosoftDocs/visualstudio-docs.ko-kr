---
title: AsyncTaskMethodBuilder &lt; TResult &gt; 구조-내부 멤버 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e4999b71ae8f654aa3d362ba16c6cf5bc6574da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182259"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder &lt; TResult &gt; 구조-내부 멤버
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 항목에서는 클래스의 내부 멤버에 대해 설명 합니다 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> . 이 클래스에 대 한 일반 정보는 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 참조 항목을 참조 하세요.  
  
 **네임스페이스:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **어셈블리:** mscorlib (mscorlib.dll)  
  
 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>내부 멤버  
  
|Name|설명|  
|----------|-----------------|  
|[ObjectIdForDebugger 속성](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|디버거에 대해이 작성기를 고유 하 게 식별 하는 데 사용할 수 있는 개체를 가져옵니다.|  
|[m_task 필드](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|초기화 지연 된 빌드된 작업을 나타냅니다.|  
  
## <a name="see-also"></a>관련 항목  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [.NET Framework에 대한 병렬 확장 기능 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
