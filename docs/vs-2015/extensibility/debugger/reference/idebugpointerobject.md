---
title: IDebugPointerObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4cd84c3580d94491e09ce9e8cde8175f9e437be0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693393"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 이 인터페이스는 포인터 개체를 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 식 계산기는 포인터 개체를 나타내기 위해이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스는가 포인터를 나타내는 경우 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 사용 하 여이 인터페이스를 가져올 수 있습니다 `IDebugObject` .  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md)에서 상속 된 메서드 외에도 인터페이스는 `IDebugPointerObject` 다음 메서드를 노출 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|인터페이스가 가리키는 개체를 가져옵니다.|  
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|인터페이스가 일련의 연속 바이트로 가리키는 값을 가져옵니다.|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|연속 된 일련의 바이트에서 인터페이스가 가리키는 값을 설정 합니다.|  
  
## <a name="remarks"></a>설명  
 식 계산기는이 인터페이스를 사용 하 여 구문 분석 트리의 포인터를 나타냅니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: ee. h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [식 계산 인터페이스](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
