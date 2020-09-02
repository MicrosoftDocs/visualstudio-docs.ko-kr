---
title: STUNIT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d97f4f065d48b2b9c56bf029fb944eb3e4e7cb11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62414613"
---
# <a name="stepunit"></a>STEPUNIT
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

단계별 실행 단위를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
typedef DWORD STEPUNIT;  
```  
  
```csharp  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
```  
  
## <a name="members"></a>멤버  
 STEP_STATEMENT  
 문 별 단계.  
  
 STEP_LINE  
 단계별 설명입니다.  
  
 STEP_INSTRUCTION  
 단계별 지침을 설명 합니다.  
  
## <a name="remarks"></a>설명  
 [단계](../../../extensibility/debugger/reference/idebugprocess3-step.md) 메서드에 인수로 전달 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
