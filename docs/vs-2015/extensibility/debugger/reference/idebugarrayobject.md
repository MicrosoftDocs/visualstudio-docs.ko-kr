---
title: IDebugArrayObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f8ec4c883078663d0e252d6a04ae7441f12f31d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686982"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 이 인터페이스는 배열 개체를 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 식 계산기는 배열을 나타내는이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스는 개체가 배열을 나타내는 경우 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 사용 하 여이 인터페이스를 가져올 수 있습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 인터페이스의 메서드 외에도 `IDebugObject` 다음 메서드가 인터페이스에서 구현 됩니다 `IDebugArrayObject` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|배열의 요소 수를 가져옵니다.|  
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|배열의 요소를 가져옵니다.|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|배열의 모든 요소를 가져옵니다.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|배열의 순위를 가져옵니다.|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|배열의 크기를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 식 계산기는이 인터페이스를 사용 하 여 구문 분석 트리에서 배열을 나타냅니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: ee. h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
