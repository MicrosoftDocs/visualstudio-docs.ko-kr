---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d9d1030616fa8d7f3a1bfc6b533c4ed8433ea89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703894"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 현재 디버그 세션에서 실행 되는 프로그램을 열거 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE (디버그 엔진)는이 인터페이스를 구현 하 여 DE-DE에서 디버그 하는 프로그램 목록을 제공 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 Visual Studio는 [Enumprograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 을 호출 하 여이 인터페이스를 가져옵니다. [Enumprograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) 은 Visual Studio에서 사용 되지 않습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugPrograms2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[다음](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|열거형 시퀀스에서 지정 된 수의 프로그램을 검색 합니다.|  
|[skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|열거형 시퀀스에서 지정 된 수의 프로그램을 건너뜁니다.|  
|[재설정](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|  
|[복제](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|열거자의 프로그램 수를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 Visual Studio에서는이 인터페이스를 사용 하 여 다음을 수행 합니다.  
  
- [Enumprograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 을 호출한 다음 각 프로그램에서 [enumprograms](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) 을 호출 하 여 **모듈** 창을 채웁니다.  
  
- 를 호출 **Attach to Process** 하 `IDebugProcess2::EnumPrograms` 고 각 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스에서 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 호출 하 여 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) 인터페이스를 가져오는 프로세스에 연결 목록을 채웁니다.  
  
- 프로세스에서 각 프로그램을 디버그할 수 있는 DEs 목록 ( [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)사용)을 생성 합니다.  
  
- 각 프로그램에 편집 하며 계속 하기 (ENC) 업데이트를 적용 합니다 (IDebugProcess2:: EnumPrograms을 호출 하 고 [Getencupdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)를 호출 하 여).  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
