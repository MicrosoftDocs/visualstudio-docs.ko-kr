---
title: IDebugArrayField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20d5df8df3e556f0908668b98a836cbedbbce47e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686995"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 배열 기호 또는 형식을 설명 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugArrayField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 기호 공급자는 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스를 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다. 이 인터페이스는 배열 개체를 나타내는 특수화입니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [Getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 에서 플래그를 반환 하는 경우 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스에서이 인터페이스를 가져오려면 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 사용 `FIELD_TYPE_ARRAY` 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 및 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스의 메서드 외에도이 인터페이스는 다음을 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|배열의 요소 수를 가져옵니다.|  
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|배열에 있는 요소의 형식을 가져옵니다.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|배열의 순위를 가져옵니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
