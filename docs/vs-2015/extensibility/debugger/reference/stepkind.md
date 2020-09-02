---
title: STKIND | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a24513e5d047501417e4c61285662f7167241e3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62414661"
---
# <a name="stepkind"></a>STEPKIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

단계별 실행 단계 종류를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```csharp  
public enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
```  
  
## <a name="members"></a>멤버  
 STEP_INTO  
 한 단계씩 함수를 수행 합니다.  
  
 STEP_OVER  
 함수에 대 한 단계를 수행 합니다.  
  
 STEP_OUT  
 함수에서 작업을 수행 합니다.  
  
 STEP_BACKWARDS  
 함수를 한 단계씩 뒤로 이동 합니다.  
  
## <a name="remarks"></a>설명  
 [단계](../../../extensibility/debugger/reference/idebugprocess3-step.md) 메서드에 인수로 전달 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
