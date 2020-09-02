---
title: IDebugAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb6344885e9e30c056982b15b8323eef3ef467b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165184"
---
# <a name="idebugaddress"></a>IDebugAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 항목의 주소를 나타냅니다. 기호 처리기에 의해 반환 됩니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 기호 공급자는이 인터페이스를 구현 하 여 개체의 주소를 나타냅니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 많은 인터페이스에서 많은 메서드는이 인터페이스를 반환 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|개체와 해당 위치를 설명 하는 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조체를 검색 합니다.|  
  
## <a name="remarks"></a>설명  
 기호 공급자는 특정 범위 (예: 함수, 메서드 또는 클래스) 내에서 개체와 해당 위치를 나타내기 위해이 인터페이스를 반환 합니다. 이 인터페이스는에서 반환 되 고 기호 공급자 및 식 계산기의 다양 한 메서드에 전달 됩니다. 일반적으로 기호 공급자는이 인터페이스의 내용을 해석 해야 하는 유일한 엔터티입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
