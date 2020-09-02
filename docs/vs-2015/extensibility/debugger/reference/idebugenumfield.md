---
title: IDebugEnumField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac993e3a4676f1c84a193ddbf6e9a3b5bc8fa235
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65676511"
---
# <a name="idebugenumfield"></a>IDebugEnumField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 열거형 형식을 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 기호 공급자는 열거형을 나타내기 위해이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [Getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 가를 반환 하는 경우에는 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 사용 하 여 [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스에서이 인터페이스를 가져옵니다 `FIELD_TYPE_ENUM` .  
  
## <a name="methods-in-vtable-order"></a>VTable 순서의 메서드  
 이 인터페이스는 및 인터페이스의 메서드 외에도 `IDebugField` `IDebugContainerField` 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|이 열거형 형식의 이름을 설명 하는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 를 반환 합니다.|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|지정 된 값과 연결 된 열거 상수의 이름을 반환 합니다.|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|지정 된 열거형 상수 이름과 연결 된 값을 반환 합니다.|  
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|지정 된 열거형 상수 이름과 연결 된 값을 반환 하지만 대/소문자를 무시 합니다.|  
  
## <a name="remarks"></a>설명  
 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)를 사용 하는 위치에 실제로 바인딩된 기본 기호입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [바인딩하며](../../../extensibility/debugger/reference/idebugbinder-bind.md)
