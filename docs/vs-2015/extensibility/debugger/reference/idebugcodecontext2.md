---
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e06fd709b2d076b6fa8de7f104e907eb1b35a42
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190948"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 코드 명령의 시작 위치를 나타냅니다. 오늘날 대부분의 런타임 아키텍처에서 코드 컨텍스트는 프로그램의 실행 스트림에서 주소로 간주할 수 있습니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진은이 인터페이스를 구현 하 여 코드 명령의 위치를 문서 위치와 연결 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 많은 인터페이스의 메서드는이 인터페이스 (일반적으로 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md))를 반환 합니다. [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 인터페이스 뿐만 아니라 중단점 확인 정보 에서도 광범위 하 게 사용 됩니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|활성 코드 컨텍스트에 해당 하는 문서 컨텍스트를 가져옵니다.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|이 코드 컨텍스트의 언어 정보를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 `IDebugCodeContext2`인터페이스와 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 인터페이스의 주요 차이점은는 `IDebugCodeContext2` 항상 명령에 맞추어 정렬 된다는 것입니다. 즉 `IDebugCodeContext2` ,는 항상 명령의 시작 부분을 가리키지만,는 `IDebugMemoryContext2` 런타임 아키텍처의 모든 메모리를 가리킬 수 있습니다. `IDebugCodeContext2` 는 기본 저장소 크기 (일반적으로 바이트)가 아닌 명령으로 증가 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [그런](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
