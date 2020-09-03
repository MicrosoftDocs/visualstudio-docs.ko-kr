---
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2cd6afb417de4d8a362916f91593d0d0e67d307c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156505"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 소스 문서를 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 일반적으로이 인터페이스를 구현 합니다. 디버그 엔진 (DE)은 소스 코드를 제공 해야 하 고 소스는 디스크에 존재 하지 않는 경우에도이 인터페이스를 구현할 수 있습니다.  이 경우 DE는 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 및 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) 인터페이스에 대 한 몇 가지 추가 메서드 뿐만 아니라 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 및 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) 인터페이스도 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 `IDebugDocumentContext2`,, 및 인터페이스의 메서드는 `IDebugDisassemblyStream2` `IDebugDocumentPosition2` `IDebugActivateDocumentEvent2` 이 인터페이스를 반환 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugDocument2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|여러 형식 중 하나로 문서 이름을 가져옵니다.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|문서의 클래스 식별자를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 DE-DE가 소스 코드를 제공 하는 경우에만 구현 됩니다. 예를 들어, HTML 페이지에서 스크립트를 디버깅 하는 경우 원본이 다운로드 되거나 동적으로 생성 되 고 디스크 파일로 존재 하지 않기 때문에 소스 코드를 제공 합니다. C + +와 같은 일반적인 언어를 디버깅할 때이 인터페이스를 구현할 필요가 없습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
