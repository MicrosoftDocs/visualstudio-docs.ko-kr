---
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 18edddd698953bf71febb8f9f2f1bac704205120
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703930"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 실행 중인 포트를 사용 하 여 디버그할 수 있는 프로그램을 등록 하거나 등록 취소 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 사용자 지정 포트 공급자는이 인터페이스를 구현 하 여 포트에서 프로그램 추가 및 제거를 지원 합니다. 일반적으로 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스를 구현 하는 동일한 개체에서 구현 됩니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 인터페이스에 대 한 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 호출에서 `IDebugPort2` 이 인터페이스를 반환 합니다. 또한 [Getportnotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) 에 대 한 호출은이 인터페이스를 반환 합니다. 디버그 엔진은이 인터페이스를 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)에 대 한 매개 변수로 볼 수 있습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugPortNotify2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|실행 중인 포트를 사용 하 여 디버그할 수 있는 프로그램을 등록 합니다.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|실행 중인 포트에서 디버그할 수 있는 프로그램의 등록을 취소 합니다.|  
  
## <a name="remarks"></a>설명  
 디버그 포트에서 프로그램이 로드 되거나 언로드될 때를 알 수 없는 경우 사용자 지정 포트 공급자가이 인터페이스를 구현 해야 합니다. 특정 포트를 통해 디버깅 하기 위해 로드 된 모든 프로그램은이 인터페이스를 사용 하 여 추적 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
