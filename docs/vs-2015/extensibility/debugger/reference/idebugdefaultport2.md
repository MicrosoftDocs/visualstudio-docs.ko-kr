---
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca0b6b7e9753b346b8a995ffd8ddcb6cc53fe7c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697521"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 포트의 서버 및 알림 기능에 액세스 하는 여러 가지 방법을 제공 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 Visual Studio는 프로그램에 액세스 하기 위한 디버그 포트를 나타내기 위해이 인터페이스를 구현 합니다. 사용자 지정 포트 공급자는 원격 디버깅을 처리 하는 경우에도이 인터페이스를 구현할 수 있습니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) 인터페이스의 메서드에 대 한 인수는이 인터페이스를 제공 합니다. [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스에서 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 호출 하면이 인터페이스를 가져올 수도 있습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 이 인터페이스는 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)에 정의 된 메서드 외에도 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|이 포트에서 포트 알림 인터페이스를 가져옵니다.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|이 포트를 호스트 하는 서버에 대 한 인터페이스를 가져옵니다.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|이 포트가 로컬 컴퓨터에서 실행 되 고 있는지 여부를 확인 합니다.|  
  
## <a name="remarks"></a>설명  
 이름 ""은 (는) `IDebugDefaultPort2` 기본 포트를 나타내지 않으므로 점에서 명칭의 비트입니다. 이를 "IDebugPort3" 라고 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
