---
title: IDebugMethodField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d7f6fc12a3366200ca1e14c0e2d55f4f6d797f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694346"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 메서드에 대해 설명 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 기호 공급자는 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스를 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다. 이 인터페이스는 메서드를 제공 하는 특수화입니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [Getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 가를 반환 하는 경우 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스에서이 인터페이스를 가져오려면 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 사용 `FIELD_TYPE_METHOD` 합니다. 또한 [Getpropertygetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [Getpropertygetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)및 [enumconstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)메서드는 모두 인터페이스를 반환 합니다 `IDebugMethodField` .  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 및 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|메서드의 매개 변수에 대 한 열거자를 만듭니다.|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|메서드를 포함 하는 개체의 "this" 포인터를 가져옵니다.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|메서드의 모든 지역 변수에 대 한 열거자를 만듭니다.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|메서드의 선택 된 지역 변수에 대 한 열거자를 만듭니다.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|특정 사용자 지정 특성이 정의 되어 있는지 여부를 확인 합니다.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|메서드의 정적 지역 변수에 대 한 열거자를 만듭니다.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|메서드의 전역 컨테이너를 가져옵니다.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|메서드를 호출 하는 데 필요한 각 인수의 형식에 대 한 열거자를 만듭니다.|  
  
## <a name="remarks"></a>설명  
 메서드는 매개 변수와 지역 변수를 포함할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
