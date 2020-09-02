---
title: AsyncTaskMethodBuilder 구조-내부 멤버 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bfe640654c9de7daac9096aa4d75f5492a8a278
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555914"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder 구조 - 내부 멤버
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 항목에서는 클래스의 내부 멤버에 대해 설명 합니다 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> . 이 클래스에 대 한 일반 정보는 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> 참조 항목을 참조 하세요.  
  
 **네임스페이스:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **어셈블리:** mscorlib (mscorlib.dll)  
  
 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없기 때문에 다음 구문이 CIL (공용 중간 언어)에서 제공 됩니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>내부 멤버  
  
|Name|설명|  
|----------|-----------------|  
|[ObjectIdForDebugger 속성](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|디버거에 대해이 작성기를 고유 하 게 식별 하는 데 사용할 수 있는 개체를 가져옵니다.|  
|[m_builder 필드](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|이 제네릭이 아닌 인스턴스가 위임 하는 제네릭 작성기 개체를 나타냅니다.|  
  
## <a name="see-also"></a>관련 항목  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [.NET Framework에 대한 병렬 확장 기능 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
