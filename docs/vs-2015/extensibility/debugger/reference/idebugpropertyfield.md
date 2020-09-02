---
title: IDebugPropertyField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bad60a24c9120c1425a5d9041a32755feeb6e6c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692155"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 속성을 가져오고 설정할 수 있는 함수를 제공 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 기호 공급자는 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)를 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다. 이 인터페이스는 클래스에 대 한 속성 개념을 지 원하는 특수화입니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [Getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드가 반환 하는 경우 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스에서이 인터페이스를 가져오려면 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 사용 `FIELD_KIND_PROP` 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 및 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|속성을 가져오는 메서드를 가져옵니다.|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|속성을 설정 하는 메서드를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 속성은 관리 되는 코드 개념으로, 변수로 처리 되는 메서드를 나타냅니다. 관리 되지 않는 c + +에는 속성이 없습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
