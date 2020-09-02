---
title: JMC_CODE_SPEC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca7d6bfb799f0a9460702c4b581ef3f5261672b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147493"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 구조는 모듈에 대 한 JustMyCode 정보를 설정 하는 데 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef struct _JMC_CODE_SPEC {  
   BOOL fIsUserCode;  
   BSTR bstrModuleName;  
} JMC_CODE_SPEC;  
```  
  
```csharp  
public struct JMC_CODE_SPEC {  
   public int    fIsUserCode;  
   public string bstrModuleName;  
};  
```  
  
## <a name="members"></a>멤버  
 fIsUserCode  
 모듈이 사용자 코드로 간주 되는 경우 0이 아닌 값 `TRUE` 이 고, 그렇지 않으면 `FALSE` 모듈이 외부 코드로 처리 되 고 디버깅 되지 않는 경우 영 ()입니다.  
  
 bstrModuleName  
 문제의 모듈 이름입니다.  
  
## <a name="remarks"></a>설명  
 이 구조체는 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) 메서드에 이러한 구조체의 목록으로 전달 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
